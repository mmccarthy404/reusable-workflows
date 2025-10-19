# reusable-workflows

GitHub reusable workflows used across all projects.

## scanning

### Usage

```
permissions:
  pull-requests: write

jobs:
  scanning:
    uses: mmccarthy404/reusable-workflows/.github/workflows/scanning.yaml@v2.0.0
    secrets: inherit
```

## terraform-ci

### Usage

```
permissions:
  id-token: write
  contents: read
  issues: write
  pull-requests: write

jobs:
  terraform-ci:
    uses: mmccarthy404/reusable-workflows/.github/workflows/terraform-ci.yaml@v2.0.0
    secrets: inherit
    with:
      terraform-version: 1.5.0
      terraform-directory: .
      terraform-var-file: terraform.tfvars
      terraform-backend-config: backend.tfvars
      aws-region: us-east-1
      aws-role: arn:aws:iam::004351562122:role/github-oidc-terraform-remote-state
```

### Inputs
* `terraform-version` (string) - Terraform version used in workflow
* `terraform-directory` (string) - Terraform directory to run workflow
* `terraform-var-file` (string) - Terraform variable file used during planning
* `terraform-backend-config` (string) - Terraform backend variable file used during initialization
* `aws-region` (string) - AWS region used for getting STS credentials
* `aws-role` (string) - AWS IAM role used for getting STS credentials

## terraform-cd

### Usage

```
permissions:
  id-token: write
  contents: read

jobs:
  terraform-cd:
    uses: mmccarthy404/reusable-workflows/.github/workflows/terraform-cd.yaml@v2.0.0
    secrets: inherit
    with:
      terraform-version: 1.5.0
      terraform-directory: .
      terraform-var-file: terraform.tfvars
      terraform-backend-config: backend.tfvars
      aws-region: us-east-1
      aws-role: arn:aws:iam::004351562122:role/github-oidc-terraform-remote-state
```

### Inputs
* `terraform-version` (string) - Terraform version used in workflow
* `terraform-directory` (string) - Terraform directory to run workflow
* `terraform-var-file` (string) - Terraform variable file used during planning
* `terraform-backend-config` (string) - Terraform backend variable file used during initialization
* `aws-region` (string) - AWS region used for getting STS credentials
* `aws-role` (string) - AWS IAM role used for getting STS credentials

## terraform-docs

### Usage

```
permissions:
  id-token: write
  contents: read

jobs:
  terraform-docs:
    uses: mmccarthy404/reusable-workflows/.github/workflows/terraform-docs.yaml@v2.0.0
    secrets: inherit
    with:
      working-dir: .
      output-file: README.md
```

### Inputs
* `working-dir` (string) - Comma separated list of directories to generate docs for
* `output-file` (string) - File in module directory where the docs should be placed