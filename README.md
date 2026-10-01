# 转债事件通 · 落地页

纯静态落地页：`index.html` + `style.css` + `site.js`，无外部依赖，离线可打开。

## 本地预览

```bash
cd ~/workspace/independent/cb-alerts/landing
python3 -m http.server 8000
# 浏览器打开 http://localhost:8000
```

## 上线前必须替换的占位（都在 `site.js`）

| 配置项 | 说明 | 状态 |
|---|---|---|
| `AFDIAN_URL` | 爱发电商品/赞助页链接（Pro ¥18/月、¥168/年付款入口） | TODO |
| `CONTACT_EMAIL` | 对外联系邮箱（订阅申请、退订、自选债修改） | TODO |

替换后无需改其他文件：页面内所有"开通 Pro"按钮、联系邮箱链接会自动注入。

## 当前未接后端

- 免费订阅表单：前端校验 + 存 `localStorage`，并提示"内测中"。正式上线前需接后端（或改用邮件申请流程，页面已备有 mailto 备选）。
- Pro 开通：当前流程为"爱发电付款 → 用户发订单截图到联系邮箱 → 人工开通"，FAQ 里已如实说明。

## 部署（三选一）

### 方案 A：GitHub Pages（推荐，需新 GitHub 账号）
1. 新账号建公开仓库（如 `cb-alerts-landing`），把本目录三个文件推到 `main` 分支根目录。
2. 仓库 Settings → Pages → Source 选 `Deploy from a branch` → `main` / `/ (root)`。
3. 得到 `https://<user>.github.io/cb-alerts-landing/`，即可作为落地页地址。

### 方案 B：Cloudflare Pages（需 Cloudflare 账号，免费）
1. Cloudflare Dashboard → Pages → 上传本目录（直接拖文件夹上传，无需 git）。
2. 得到 `https://<name>.pages.dev`，可绑自定义域名。

### 方案 C：Netlify（需 Netlify 账号，免费）
1. `npx netlify-cli deploy --dir=. --prod` 或网页端拖文件夹到 app.netlify.com/drop。
2. 得到 `https://<name>.netlify.app`。

三个方案都是纯静态托管，零成本，无需服务器。

## 合规要点（已落实在文案中）

- 全站"只同步公开披露事实，不做解读、不推荐买卖，不构成任何投资建议"。
- 数据来源明确标注：巨潮资讯（法定信息披露平台）公开接口。
- 无收益承诺、无涨跌预测、无 hype 话术。
