# 部署与更新手册（给未来的维护者 / AI 智能体）

任何新会话的 AI 或开发者，读本文件即可独立完成更新部署。

## 架构

```
本仓库：github.com/Toukaitetsuya3150-code/alpha-hunter（唯一真相源）
    ↓ push / 网页上传到 main 分支
GitHub Pages 自动部署（约 1 分钟）
    ↓
固定 URL：https://toukaitetsuya3150-code.github.io/alpha-hunter/
```

- `index.html`：单文件应用本体（无构建步骤，纯静态）
- `version.json`：版本清单，应用启动时拉取它检查更新（VERSION_URL 已指向本仓库的 Pages 地址）
- 更新链路：用户浏览器 → 拉 `version.json` → 发现新版本 → 提示刷新 → 拿到新 `index.html`

## 更新流程（每次改代码必须走完）

1. 修改 `index.html`
2. **同步两处版本信息**：
   - `index.html` 里的 `APP_VERSION` 常量
   - `version.json` 的 `version`、`changelog`、`updatedAt`
   - 语义化版本：大功能.小功能.修复（如 3.3.0 → 3.3.1），版本号只升不降
3. push 到 main 分支（或网页上传覆盖），等 1 分钟验证

## 有 git 权限时（推荐）

```bash
git clone https://github.com/Toukaitetsuya3150-code/alpha-hunter.git
cd alpha-hunter
# 改代码、升版本号
git add -A && git commit -m "vX.Y.Z 说明" && git push
```

AI 智能体需要认证时：让用户在 GitHub → Settings → Developer settings → Personal access tokens (fine-grained) 生成一个**仅授予本仓库 Contents 读写权限**的令牌，用完即删。

## 没有 git 权限时（网页操作）

仓库页面 → Add file → Upload files → 拖入新文件 → Commit。Pages 自动重新部署。

## 注意事项

- 用户数据全部在浏览器 localStorage，服务器无状态，随意覆盖部署不丢用户数据（代码内置 migrateData 迁移）
- `.nojekyll` 必须保留
- 版本号只能升不能降，否则老用户收不到更新提示
