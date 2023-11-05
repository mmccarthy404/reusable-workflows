# reusable-workflows

GitHub reusable workflows used across all projects.

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
    uses: mmccarthy404/reusable-workflows/.github/workflows/terraform-ci.yaml@v1.0.0
    with:
      terraform-version: 1.5.0
      terraform-directory: .
      terraform-var-file: terraform.tfvars
      terraform-backend-config: backend.tfvars
      aws-region: us-east-1
      aws-role: arn:aws:iam::004351562122:role/github-oidc-terraform-remote-state
    secrets:
      token: ${{ secrets.GITHUB_TOKEN }}
```

### Inputs
* `terraform-version` (string) - Terraform version used in workflow
* `terraform-directory` (string) - Terraform directory to run workflow
* `terraform-var-file` (string) - Terraform variable file used during planning
* `terraform-backend-config` (string) - Terraform backend variable file used during initialization
* `aws-region` (string) - AWS region used for getting STS credentials
* `aws-role` (string) - AWS IAM role used for getting STS credentials

### Secrets
* `token`

## terraform-cd

### Usage

```
permissions:
  id-token: write
  contents: read

jobs:
  terraform-cd:
    uses: mmccarthy404/reusable-workflows/.github/workflows/terraform-cd.yaml@v1.0.0
    with:
      terraform-version: 1.5.0
      terraform-directory: .
      terraform-var-file: terraform.tfvars
      terraform-backend-config: backend.tfvars
      aws-region: us-east-1
      aws-role: arn:aws:iam::004351562122:role/github-oidc-terraform-remote-state
    secrets:
      token: ${{ secrets.GITHUB_TOKEN }}
```

### Inputs
* `terraform-version` (string) - Terraform version used in workflow
* `terraform-directory` (string) - Terraform directory to run workflow
* `terraform-var-file` (string) - Terraform variable file used during planning
* `terraform-backend-config` (string) - Terraform backend variable file used during initialization
* `aws-region` (string) - AWS region used for getting STS credentials
* `aws-role` (string) - AWS IAM role used for getting STS credentials

### Secrets
* `token`
