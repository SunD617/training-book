# 训练簿 V15 · 在线 PWA 开发版

## 目录
- `index.html`：主应用
- `manifest.webmanifest`：PWA 安装配置
- `sw.js`：离线缓存与自动更新
- `qa.html`：一键自动化验收（仅使用隔离测试数据）
- `icon-192.png` / `icon-512.png`：桌面图标

## 推荐部署：GitHub Pages
1. 在 GitHub 新建一个 **Public** 仓库（仓库名可用 `training-book`）。仓库只放应用代码，不要上传个人数据备份；免费 GitHub Pages 通常使用公开仓库。
2. 上传本目录中的全部文件到仓库根目录。
3. 在仓库 Settings → Pages 中，选择 Deploy from a branch，分支 `main`，目录 `/ (root)`，保存。
4. 等待 GitHub Pages 发布，得到固定 HTTPS 地址。
5. 打开 `https://<账号>.github.io/training-book/` 测试主应用。
6. 打开同一地址下的 `qa.html`，点击“运行一键验收”。

## 版本更新
- 后续将新版本文件提交到同一个仓库、同一目录。
- 保持正式数据键 `trainingBook_v3` 不变；不要更换域名/协议/端口/路径基址。
- `sw.js` 中的 `CACHE_NAME` 每次发布递增，例如 `trainingbook-pwa-v16`。
- Service Worker 会安装新缓存、接管页面并刷新到新版本。
- 同一 HTTPS 来源下的 localStorage 数据会跨版本保留，不需要每次导出/导入。

## 数据边界（重要）
- 这是**本地优先 PWA**：数据保存在当前浏览器/设备的本地存储中。
- 在线访问和自动更新不等于云端同步；不同设备、不同浏览器的数据不会自动合并。
- 从旧的 `file://` 本地 HTML 迁移到新的 HTTPS 地址时，浏览器存储隔离，需做**一次性**旧版 JSON 导出并在新站导入。此后同一网址更新无需重复导入。
- 仍建议偶尔导出备份；卸载浏览器、清理网站数据或换设备可能导致本地数据丢失。
- 自动验收页面使用独立测试键 `trainingBook_v3_test`，不会覆盖正式键 `trainingBook_v3`。

## 当前限制
- GitHub Pages 发布需要用户自己的 GitHub 账户授权/仓库操作。本版文件部署到 GitHub Pages 后即可获得公开 HTTPS 网址。
- 如需真正的跨设备云同步，需要另行配置登录身份与云数据库；本版没有伪装成已实现云同步。
