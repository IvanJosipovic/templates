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