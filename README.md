# PICO 4 Ultra · 结构原理课（3D 交互）

纯静态站点，无需后端。直接部署即可访问。

## 部署到 GitHub Pages

### 方式一：`gh-pages` 分支（推荐，源码与产物分离）

```bash
# 在你的仓库目录下
git clone https://github.com/<你的用户名>/<仓库名>.git
cd <仓库名>

git checkout --orphan gh-pages
git rm -rf .
# 把本 release/ 目录里的所有文件复制到当前目录
cp -r /path/to/release/* .
git add -A
git commit -m "deploy: PICO 4 Ultra 3D course"
git push origin gh-pages
```

然后到仓库 **Settings → Pages**：
- Source 选 `Deploy from a branch`
- Branch 选 `gh-pages` / `/ (root)`
- 保存，等 1~2 分钟

访问地址：`https://<你的用户名>.github.io/<仓库名>/`

### 方式二：`docs/` 目录

把 `release/` 里的内容复制到仓库的 `docs/` 目录，推到 main。
**Settings → Pages** 里 Source 选 `Deploy from a branch`，Branch 选 `main` / `/docs`。

## 注意

- 所有资源都用相对路径（`./assets/app.js`），部署在子路径下不用改任何配置
- `.nojekyll` 必须一起上传，否则 GitHub 的 Jekyll 可能吞掉某些文件
- 站点一旦启用 Pages 就是**公开可访问**的，即使仓库是私有的
- 首次部署后可能有几分钟 CDN 缓存延迟

## 本地预览

```bash
node serve.mjs .   # 任意静态服务器均可，例如 npx serve .
```