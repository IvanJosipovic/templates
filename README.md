# templates
GitHub Templates



## Validate Renovate Config

```yaml
name: Validate Renovate Config

on:
  pull_request:
    paths:
      - .github/renovate.json
    types: [opened, reopened, synchronize]
  merge_group:

jobs:
  call-workflow:
    permissions:
      contents: read
    uses: IvanJosipovic/templates/.github/workflows/validate-renovate-config.yaml@main
```

## CSharp Publish Nuget

```yaml
name: CICD

on:
  workflow_dispatch:
  push:
    branches:
      - 'main'
      - 'alpha'
      - 'beta'
  pull_request:
    types: [opened, reopened, synchronize]
  merge_group:

jobs:
  call-workflow:
    permissions:
      id-token: write
      contents: write
      actions: write
      checks: write
      issues: write
      packages: write
      pull-requests: write
    uses: IvanJosipovic/templates/.github/workflows/csharp-publish-nuget.yaml@main
```
## Lint PR

```yaml
name: "Lint PR"

on:
  pull_request_target:
    types:
      - opened
      - edited
      - synchronize
      - reopened

permissions:
  pull-requests: read

jobs:
  main:
    name: Validate PR title
    runs-on: ubuntu-latest
    steps:
      - uses: amannn/action-semantic-pull-request@v6
        env:
          GITHUB_TOKEN: ${{ secrets.GITHUB_TOKEN }}
```
