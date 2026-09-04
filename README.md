# ZEIT ONLINE Terraform ``baseproject``connector

---

**_NOTE:_** This Action is used internally by the ZEIT ONLINE organization and is probably not useful outside of this specific context.

---

## Summary

This composite action fetches environment-specific infrastructure infos from a [Terraform baseproject](https://github.com/ZeitOnline/terraform-modules-baseproject) instance. Its main purpose is to facilitate standardized, secure (i.e. keyless) Authentication against ZON Cloud infrastructure, such as GCE, GKE, GCR and Vault.


## Example Usage


### Authenticate against GKE and GAR

Set up authentication against the Cluster that is configured for the project-environment.
Also authenticate against GAR. All following steps will be fully authenticated to K8s/GAR.

```yaml
jobs:
    build:
        # ...
        steps:
            # ...
            - name: Baseproject
              uses: ZeitOnline/gh-action-baseproject@v0
              with:
                project_name: ${{ env.PROJECT }}
                environment: ${{ env.ENVIRONMENT }}
                gke_auth: true
                gar_docker_auth: true
            # ...
```

### Fetch secrets from Vault

The `gh-action-baseproject` Action outputs all information neccessary for authenticating against Vault with the
`jwt` auth method:

```yaml
jobs:
    build:
        # ...
        steps:
            - name: Baseproject
              uses: ZeitOnline/gh-action-baseproject@v0
              with:
                project_name: ${{ env.PROJECT }}
                environment: ${{ env.ENVIRONMENT }}

            - name: Retrieve secrets from Vault
              id: vault-secrets
              uses: hashicorp/vault-action@v2.4.0
              with:
                method: jwt
                url: ${{ steps.baseproject.outputs.vault_addr }}
                path: ${{ steps.baseproject.outputs.gha_vault_path }}
                role: ${{ steps.baseproject.outputs.gha_vault_role }}
                secrets: |
                  zon/v1/path/to/my-secret my-secret;

            - name: Use Vault secret
              run: echo ${{ steps.vault-secrets.outputs.my-secret }}
```


### Set up docker buildx

For both convenience and consistency this action can also set up a `docker buildx` builder.

This behaviour is controlled by the `setup_buildx` input, which defaults to "do nothing";
set it to "true" to enable.
Setting `gar_docker_auth` also enables this implicitly
(with the assumption, if you want to push a docker image, you probably want to build one first),
if this is not desired, set `setup_buildx` to "false" explicitly.


### Authenticate github.com traffic

The action writes an environment variable `GH_TOKEN` for all following steps, holding the
workflow's own automatic token. This is unconditional and has no input.

That automatic token is the one GitHub issues to every job by itself — readable in a
workflow as `${{ github.token }}` or, identically, `${{ secrets.GITHUB_TOKEN }}`. It is an
app installation token, scoped to the current repository, carrying whatever the job's
`permissions:` block grants, and it expires when the job ends. Nothing needs to be
configured for it to exist; this action only copies it into the environment under a name
that command-line tools look for.

Why: github.com meters anonymous traffic at 60 requests per hour per source IP, and the
whole runner fleet shares one NAT address. Over-quota requests are answered with `401`,
which git reports as `could not read Username for 'https://github.com'` — the failure mode
seen in kustomize remote bases and OpenTofu module downloads, on repositories that are
public. The runner image carries a git credential helper that reads `GH_TOKEN`, so git
retries such a request authenticated and uses the token's per-repository quota instead. The
`gh` CLI reads the same variable.

Three consequences worth knowing:

- Beware the two meanings of the name: `secrets.GITHUB_TOKEN` is the automatic token
  described above and always exists, whereas an *environment variable* called
  `GITHUB_TOKEN` is never set by GitHub — workflows set that themselves by convention. The
  runner image's credential helper accepts either, preferring `GH_TOKEN`, which is the same
  order the `gh` CLI uses.
- The token becomes a plain environment variable from this point on, visible to every
  following step. It is the same token the job already held, so this grants nothing new,
  but it is easier to leak by accident — through a tool that dumps its environment, say.
  Actions masks the value in logs.
- A step or job declaring its own `GH_TOKEN` under `env:` still takes precedence, so
  workflows passing a different token are unaffected. Note that a repository-scoped token
  cannot read *other* private repositories; for that, keep passing your own credential.


## Reference

Here are all the inputs available through `with`:

| Input                | Description                                                                       | Default | Required |
| -------------------- | --------------------------------------------------------------------------------- | ------- | -------- |
| `project_name`       | The Name (`project_name`) of the ZON baseproject                                  |         | ✔        |
| `environment`        | The Environment in which the workflow runs                                        |         | ✔        |
| `unique_id`          | The unique TF baseproject identifier                                              |         |          |
| `google_auth`        | Authenticate to Google Cloud                                                      | `false` |          |
| `gke_auth`           | Authenticate to GKE (Google Kubernetes Engine)                                    | `false` |          |
| `gcr_auth`           | Authenticate to GCR (Google Container Registry)                                   | `false` |          |
| `gar_docker_auth`    | Authenticate to GAR (Google Artifact Registry) for Docker                         | `false` |          |
| `python_registry`    | Setup dependencies for Python Registry (Google Artifact Registry)                 | `false` |          |
| `vault_export_token` | Get a Vault Token and export it as VAULT_TOKEN                                    | `false` |          |
| `setup_buildx`       | Set up docker buildx                                                              | `unset` |          |


## Releases

This action uses [Release Please](https://github.com/googleapis/release-please-action). To create a new release, create a PR and use [Conventional Commits](https://www.conventionalcommits.org/en/v1.0.0/) as described [here](https://docs.zeit.de/ops/terraform-infra/terraform/repos.html#modulversionierung).
