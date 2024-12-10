# Changelog

## [0.11.0](https://github.com/ZeitOnline/gh-action-baseproject/compare/v0.10.8...v0.11.0) (2024-12-10)


### Features

* expose python binary as input ([404fced](https://github.com/ZeitOnline/gh-action-baseproject/commit/404fced77ce51f36b24b07aa1f78896889d72a5b))


### Bug Fixes

* fix package name ([d77a39b](https://github.com/ZeitOnline/gh-action-baseproject/commit/d77a39be468dda223cb8586e3d4575e1ac203f1b))

## [0.10.8](https://github.com/ZeitOnline/gh-action-baseproject/compare/v0.10.7...v0.10.8) (2024-10-25)


### Bug Fixes

* **vault:** increase token TTL ([134f0a1](https://github.com/ZeitOnline/gh-action-baseproject/commit/134f0a157bf926d5cedef336e6dead046477710d))

## [0.10.7](https://github.com/ZeitOnline/gh-action-baseproject/compare/v0.10.6...v0.10.7) (2024-10-15)


### Bug Fixes

* **deps:** update docker/setup-buildx-action action to v3.7.1 ([32ff132](https://github.com/ZeitOnline/gh-action-baseproject/commit/32ff1322a178e50f72329bd274cbda8730bb196f))
* **deps:** update google-github-actions/auth digest to 8254fb7 ([da8e7ba](https://github.com/ZeitOnline/gh-action-baseproject/commit/da8e7bafb88b8ad881d85cc993479f1324d8a107))
* don't set buildkit-flags ([914853f](https://github.com/ZeitOnline/gh-action-baseproject/commit/914853f7db79fe25a86aa18813d4264ebe2554c3))

## [0.10.6](https://github.com/ZeitOnline/gh-action-baseproject/compare/v0.10.5...v0.10.6) (2024-10-02)


### Bug Fixes

* rename buildkit argument ([b906f59](https://github.com/ZeitOnline/gh-action-baseproject/commit/b906f596b4d98bc155cbc699559bcadd557f5f6b))

## [0.10.5](https://github.com/ZeitOnline/gh-action-baseproject/compare/v0.10.4...v0.10.5) (2024-09-10)


### Bug Fixes

* update github-actions ([fdf9bc1](https://github.com/ZeitOnline/gh-action-baseproject/commit/fdf9bc1c328230f1b0d7208ca7c9908671829b8d))

## [0.10.4](https://github.com/ZeitOnline/gh-action-baseproject/compare/v0.10.3...v0.10.4) (2024-07-24)


### Bug Fixes

* use gcr mirror in docker buildx ([8b6d110](https://github.com/ZeitOnline/gh-action-baseproject/commit/8b6d110ccb00c94e1be54d2673fd4866c9539bbe))

## [0.10.3](https://github.com/ZeitOnline/gh-action-baseproject/compare/v0.10.2...v0.10.3) (2024-03-05)


### Bug Fixes

* **deps:** update docker/setup-buildx-action action to v3.1.0 ([0ccdbd8](https://github.com/ZeitOnline/gh-action-baseproject/commit/0ccdbd8dd3edbf6e914016650cb4a21ec2d53fde))
* use fix prefix for action.yml ([70e9f3d](https://github.com/ZeitOnline/gh-action-baseproject/commit/70e9f3d8599f5236e07e09987ff8f8dfd7ee4326))

## [0.10.2](https://github.com/ZeitOnline/gh-action-baseproject/compare/v0.10.1...v0.10.2) (2024-02-13)


### Bug Fixes

* **release:** force release ([5595aa7](https://github.com/ZeitOnline/gh-action-baseproject/commit/5595aa7ca68105f4ef3f31360e9d2371ee94dd2f))

## [0.10.1](https://github.com/ZeitOnline/gh-action-baseproject/compare/v0.10.0...v0.10.1) (2024-02-07)


### Bug Fixes

* typo in d3e323d ([ef7344a](https://github.com/ZeitOnline/gh-action-baseproject/commit/ef7344a6ad092f0370e30ed65d8ab6c4533a01e1))

## [0.10.0](https://github.com/ZeitOnline/gh-action-baseproject/compare/v0.9.0...v0.10.0) (2024-02-01)


### Features

* set up docker buildx builder ([d3e323d](https://github.com/ZeitOnline/gh-action-baseproject/commit/d3e323d54f13140e7c748bf8fb41fe236901be67))

## [0.9.0](https://github.com/ZeitOnline/gh-action-baseproject/compare/v0.8.1...v0.9.0) (2024-01-24)


### Features

* **main:** No need (or rather, counterproductive) to install kubectl ourselves, it's already in our runner image ([5283422](https://github.com/ZeitOnline/gh-action-baseproject/commit/5283422b792bc482210973725d5798c50fd403cc))

## [0.8.1](https://github.com/ZeitOnline/gh-action-baseproject/compare/v0.8.0...v0.8.1) (2023-12-22)


### Bug Fixes

* **release:** test release ([d876383](https://github.com/ZeitOnline/gh-action-baseproject/commit/d8763833630234842199703cfa539728593349af))

## [0.8.0](https://github.com/ZeitOnline/gh-action-baseproject/compare/v0.7.7...v0.8.0) (2023-12-22)


### Features

* **docs:** how to release ([5f3901b](https://github.com/ZeitOnline/gh-action-baseproject/commit/5f3901bf8953fe034202bf4f08f5b42422140045))

## [0.7.7](https://github.com/ZeitOnline/gh-action-baseproject/compare/v0.7.6...v0.7.7) (2023-12-22)


### Bug Fixes

* **release:** combine lint and check jobs ([#61](https://github.com/ZeitOnline/gh-action-baseproject/issues/61)) ([20fdbee](https://github.com/ZeitOnline/gh-action-baseproject/commit/20fdbeebd826622cea71b1f725c8b8e24a54c2fa))

## [0.7.6](https://github.com/ZeitOnline/gh-action-baseproject/compare/v0.7.5...v0.7.6) (2023-12-22)


### Bug Fixes

* **release:** don't tag v0 explicitly ([#59](https://github.com/ZeitOnline/gh-action-baseproject/issues/59)) ([ac3acb7](https://github.com/ZeitOnline/gh-action-baseproject/commit/ac3acb7db7bc0e70df163fe7a43d60f046546ec7))

## [0.7.5](https://github.com/ZeitOnline/gh-action-baseproject/compare/v0.7.4...v0.7.5) (2023-12-22)


### Bug Fixes

* **release:** change id of release step ([#57](https://github.com/ZeitOnline/gh-action-baseproject/issues/57)) ([90f9b47](https://github.com/ZeitOnline/gh-action-baseproject/commit/90f9b472fba45df1008282a89ae4389caf97df41))

## [0.7.4](https://github.com/ZeitOnline/gh-action-baseproject/compare/v0.7.3...v0.7.4) (2023-12-22)


### Bug Fixes

* **release:** perform a checkout before tag step ([#55](https://github.com/ZeitOnline/gh-action-baseproject/issues/55)) ([ecdcd8d](https://github.com/ZeitOnline/gh-action-baseproject/commit/ecdcd8d15777e7eec5218e3899504075c6733ed8))

## [0.7.3](https://github.com/ZeitOnline/gh-action-baseproject/compare/v0.7.2...v0.7.3) (2023-12-22)


### Bug Fixes

* **release:** use id attribute ([#53](https://github.com/ZeitOnline/gh-action-baseproject/issues/53)) ([7a4230c](https://github.com/ZeitOnline/gh-action-baseproject/commit/7a4230cb8bac27368dd950c61a89343fdd03be5c))

## [0.7.2](https://github.com/ZeitOnline/gh-action-baseproject/compare/v0.7.1...v0.7.2) (2023-12-22)


### Bug Fixes

* **release:** fix condition ([#51](https://github.com/ZeitOnline/gh-action-baseproject/issues/51)) ([f7296fa](https://github.com/ZeitOnline/gh-action-baseproject/commit/f7296fa89733a6569a61362c54af27eef38939b6))

## [0.7.1](https://github.com/ZeitOnline/gh-action-baseproject/compare/v0.7.0...v0.7.1) (2023-12-22)


### Bug Fixes

* **release:** run on all pushes to main ([#49](https://github.com/ZeitOnline/gh-action-baseproject/issues/49)) ([36200b0](https://github.com/ZeitOnline/gh-action-baseproject/commit/36200b0179f8022bb8532fb95db0217700e6fdc6))

## [0.7.0](https://github.com/ZeitOnline/gh-action-baseproject/compare/v0.6.1...v0.7.0) (2023-12-22)


### Features

* **release:** set rolling major/minor tags ([#43](https://github.com/ZeitOnline/gh-action-baseproject/issues/43)) ([fba94a9](https://github.com/ZeitOnline/gh-action-baseproject/commit/fba94a9cefc917be20332fbb09b318ad80bf54c8))


### Bug Fixes

* **test:** just testing the updated release workflow ([#44](https://github.com/ZeitOnline/gh-action-baseproject/issues/44)) ([df2d77e](https://github.com/ZeitOnline/gh-action-baseproject/commit/df2d77ecd2530efc7ad3973d49f7afb4115a120e))
* **test:** test release ([#47](https://github.com/ZeitOnline/gh-action-baseproject/issues/47)) ([287321d](https://github.com/ZeitOnline/gh-action-baseproject/commit/287321de220f02b991ef990bb15729a4d668d061))

## [0.6.1](https://github.com/ZeitOnline/gh-action-baseproject/compare/v0.6.0...v0.6.1) (2023-11-23)


### Bug Fixes

* **baseproject:** remove superfluous conditional ([#39](https://github.com/ZeitOnline/gh-action-baseproject/issues/39)) ([8eeb160](https://github.com/ZeitOnline/gh-action-baseproject/commit/8eeb16075c7a541e8cbf3077761b9b0fa6a282d8))

## [0.6.0](https://github.com/ZeitOnline/gh-action-baseproject/compare/v0.5.1...v0.6.0) (2023-10-05)


### Features

* add pre-commit-hook ([4cec76a](https://github.com/ZeitOnline/gh-action-baseproject/commit/4cec76aa8c4090c3ddc3ce20265c1c39efbdbcb3))

## [0.5.0](https://github.com/ZeitOnline/gh-action-baseproject/compare/v0.4.0...v0.5.0) (2023-10-02)


### Features

* add test step ([837d427](https://github.com/ZeitOnline/gh-action-baseproject/commit/837d427a6ff825b60aa10c0b96a59c910b9b5437))

## [0.4.0](https://github.com/ZeitOnline/gh-action-baseproject/compare/v0.3.3...v0.4.0) (2023-10-02)


### Features

* add test step ([4229190](https://github.com/ZeitOnline/gh-action-baseproject/commit/4229190d11b78c34b9eb7e34099df076678c8579))
* add testt step ([e462fb3](https://github.com/ZeitOnline/gh-action-baseproject/commit/e462fb3012d5ce82a1e0f990d983ebd9e728b2e6))

## [0.3.3](https://github.com/ZeitOnline/gh-action-baseproject/compare/v0.3.2...v0.3.3) (2023-09-30)


### Features

* Add test step ([fccd5aa](https://github.com/ZeitOnline/gh-action-baseproject/commit/fccd5aa6348ec1a607aca8217c0bf907dfe71f2d))
