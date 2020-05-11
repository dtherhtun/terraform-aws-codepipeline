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
