# CI/CD pipeline for Terraform 


```yaml
module "codepipeline" {
  source   = "DTherHtun/codepipeline/aws"
  name     = "iac"
  vcs_repo = var.vcs_repo
  environment = {
    AWS_ACCESS_KEY_ID     = var.aws.access_key
    AWS_SECRET_ACCESS_KEY = var.aws.secret_key
    CONFIRM_DESTROY = 1
  }
  s3_backend_config = module.s3backend.config
}
```

<!-- BEGINNING OF PRE-COMMIT-TERRAFORM DOCS HOOK -->
## Requirements

No requirements.

## Providers

| Name | Version |
|------|---------|
| aws | n/a |
| random | n/a |

## Inputs

| Name | Description | Type | Default | Required |
|------|-------------|------|---------|:--------:|
| auto\_apply | Whether to automatically apply changes when a Terraform plan is successful. Defaults to false. | `bool` | `false` | no |
| environment | A map of environment varaibles to use for this workspace | `map(string)` | `{}` | no |
| name | A project name to use for resource mapping | `string` | `"terraform"` | no |
| s3\_backend\_config | Settings for configuring the S3 remote backend | <pre>object({<br>    bucket         = string,<br>    region         = string,<br>    role_arn       = string,<br>    dynamodb_table = string,<br>  })</pre> | n/a | yes |
| terraform\_version | The version of Terraform to use for this workspace. Defaults to the latest available version. | `string` | `"latest"` | no |
| vcs\_repo | Settings for the workspace's VCS repository. | `object({ identifier = string, branch = string, oauth_token = string })` | n/a | yes |
| working\_directory | A relative path that Terraform will execute within. Defaults to the root of your repository. | `string` | `"."` | no |

## Outputs

No output.

<!-- END OF PRE-COMMIT-TERRAFORM DOCS HOOK -->
