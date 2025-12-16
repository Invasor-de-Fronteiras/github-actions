# Reusable Release GitHub Action

This workflow automatically publishes releases for each reusable GitHub Actions workflow defined in **.github/workflows/reusable-*.yml**.
It generates both major ({workflow-name}-v{major}) and semver ({workflow-name}-v{major}.{minor}.{patch}) tags and updates an individual changelog for each workflow at **docs/workflows/{workflow-name}.CHANGELOG.md**.

## Usage

```yml
name: Release Github Action's Version's
on:
  push: {}

jobs:
  release:
    uses: Invasor-de-Fronteiras/github-actions/.github/workflows/reusable-release-gh.yml@v1
    permissions:
      contents: write # to be able to publish a GitHub release
      issues: write # to be able to comment on released issues
      pull-requests: write # to be able to comment on released pull requests
      id-token: write # to enable use of OIDC for trusted publishing and npm provenance
    secrets: inherit
```

## Examples:

Reusable workflows

```sh
.github/workflows/
├─ reusable-release.yml
├─ reusable-docker-build.yml
└─ reusable-helm-publish.yml
```

Generated tags

```sh
reusable-release@v1
reusable-release@v1.0.0

reusable-docker-build@v2
reusable-docker-build@v2.3.1
```

Generated changelogs

```
docs/workflows/
├─ reusable-release.CHANGELOG.md
├─ reusable-docker-build.CHANGELOG.md
└─ reusable-helm-publish.CHANGELOG.md
```


