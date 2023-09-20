# github-reusable-workflows
Reusable workflows for use with Github Actions

## ```driftctl.yml``` Workflow Caller Example
```
name: "TF Drift CTL"
run-name: TF Drift CTL

on:
  workflow_dispatch:
    branches:
    - main
    paths:
        - 'prd/**'
        - '.github/workflows/**'

jobs:
    TF-Drift-CTL:
        name: tf-drift-CTL
        secrets: inherit
        uses: kicka5h/github-reusable-workflows/.github/workflows/terraformm/driftctl.yml@main
```

## ```tfdeploy.yml``` Workflow Caller Example
```
name: "TF Deploy"
run-name: TF Deploy

on:
  workflow_dispatch:
    branches:
    - main
    paths:
        - 'prd/**'
        - '.github/workflows/**'

jobs:
    TF-Deploy:
        name: tf-deploy
        secrets: inherit
        uses: kicka5h/github-reusable-workflows/.github/workflows/terraformm/tfdeploy.yml@main
        with:
            plan_args: -var="admin_password=${{ secrets.admin_password }}"
```

## ```tfsec.yml``` Workflow Caller Example

```
name: "PR TF Sec"
run-name: Pull Request TF Sec

on:
  pull_request:
    branches:
    - main
    paths:
        - 'prd/**'
        - '.github/workflows/**'

jobs:
    TF-Sec:
        name: tf-sec
        secrets: inherit
        uses: kicka5h/github-reusable-workflows/.github/workflows/terraformm/tfsec.yml@main
        with:
            sarif_file: prd_tfsec.sarif
```
## ```tfvalidate.yml``` Workflow Caller Example
```
name: "PR TF Validate"
run-name: Pull Request TF Validate

on:
  pull_request:
    branches:
    - main
    paths:
        - 'prd/**'
        - '.github/workflows/**'

jobs:
    TF-Validate:
        name: tf-validate
        secrets: inherit
        uses: kicka5h/github-reusable-workflows/.github/workflows/terraformm/tfvalidate.yml@main
        with:
            plan_args: -var="admin_password=${{ secrets.admin_password }}"
```