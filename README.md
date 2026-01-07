# Web Deploy Test

简单的测试项目，用于验证 dev-platform Web 部署流程。

## 文件结构

```
web-deploy-test/
├── index.html              # 测试页面
├── package.json            # 构建脚本
└── .github/
    └── workflows/
        └── dev-platform-deploy.yml  # 部署 workflow
```

## 构建命令

```bash
npm run build_staging-02    # 构建到 build/ 目录
```

## 测试步骤

1. 在 GitHub 创建仓库 `chowbus/web-deploy-test`
2. 推送代码到 main 分支
3. 在 dev-platform 创建项目，配置 Web 部署
4. 触发部署，验证流程
