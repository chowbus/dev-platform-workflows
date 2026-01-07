# dev-platform-workflows

dev-platform 的 GitHub Actions 工作流模板仓库。

## 📁 模板列表

| 模板文件 | 说明 | 引用方式 |
|---------|------|---------|
| `web-deploy-template.yml` | Web 项目部署模板 | `uses: chowbus/web-deploy-test/.github/workflows/web-deploy-template.yml@main` |

## 🚀 使用方法

### Web 项目

在你的 Web 项目中创建 `.github/workflows/dev-platform-deploy.yml`：

```yaml
name: Deploy via dev-platform

on:
  workflow_dispatch:
    inputs:
      environment:
        required: true
        type: string
      bucket_name:
        required: true
        type: string
      # ... 其他参数

jobs:
  deploy:
    uses: chowbus/web-deploy-test/.github/workflows/web-deploy-template.yml@main
    with:
      environment: ${{ inputs.environment }}
      bucket_name: ${{ inputs.bucket_name }}
      node_version: "16.14.2"
      git_ref: ${{ inputs.git_ref }}
    secrets: inherit
```

## 📝 模板参数 (web-deploy-template.yml)

| 参数 | 必填 | 默认值 | 说明 |
|-----|-----|-------|------|
| environment | ✅ | - | staging-01/02/03, production |
| bucket_name | ✅ | - | S3 bucket 名称 |
| node_version | ❌ | "16.18" | Node.js 版本 |
| git_ref | ❌ | "main" | Git 分支/标签 |
| callback_url | ❌ | "" | 部署回调 URL |
| cloudfront_id | ❌ | "" | CloudFront ID |
| custom_build_cmd | ❌ | "" | 自定义构建命令 |

## 🔐 所需 Secrets

- AWS_ACCESS_KEY_ID_STAGING_CI / AWS_SECRET_ACCESS_KEY_STAGING_CI
- AWS_ACCESS_KEY_ID_PROD_CI / AWS_SECRET_ACCESS_KEY_PROD_CI
- AWS_REGION
