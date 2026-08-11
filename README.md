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


### Use the GCloud access token

The GCloud access token is exposed as the `gcloud_access_token` output. It is deliberately *not*
exported into the job environment (writing secrets to `GITHUB_ENV` makes them visible to every
subsequent step of the job); map it onto the steps that need it instead:

```yaml
            - name: Baseproject
              id: baseproject
              uses: ZeitOnline/gh-action-baseproject@v0
              with:
                project_name: ${{ env.PROJECT }}
                environment: ${{ env.ENVIRONMENT }}
                google_auth: true

            - name: Use the token
              env:
                GCLOUD_TOKEN: ${{ steps.baseproject.outputs.gcloud_access_token }}
              run: curl -H "Authorization: Bearer ${GCLOUD_TOKEN}" ...
```

### Set up docker buildx

For both convenience and consistency this action can also set up a `docker buildx` builder.

This behaviour is controlled by the `setup_buildx` input, which defaults to "do nothing";
set it to "true" to enable.
Setting `gar_docker_auth` also enables this implicitly
(with the assumption, if you want to push a docker image, you probably want to build one first),
if this is not desired, set `setup_buildx` to "false" explicitly.


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
