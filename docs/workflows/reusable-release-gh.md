# Reusable Release GitHub Action

This workflow automatically publishes releases for each reusable GitHub Actions workflow defined in **.github/workflows/reusable-*.yml**.
It generates both major (v{major}) and semver (v{major}.{minor}.{patch}) tags and updates an individual changelog for each workflow at **docs/workflows/{workflow-name}.CHANGELOG.md**.