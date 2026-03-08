# 使用 Cloudflare Pages 部署个人网站

## 方式一：直接上传（推荐，无需 Git）

1. **打包站点文件**
   - 将本文件夹内**所有文件**打成 zip（包含 `.html`、图片、PDF 等）。
   - 必须包含：`index.html`、`王泽华_AI产品实习生_个人主页.html`、`project_detail_medical.html`、`project_detail_agent.html`，以及你的图片（如 `户外生活照(1).jpg`）、简历 PDF（如 `王泽华_产品实习生_13133317836.pdf`）等。

2. **登录 Cloudflare**
   - 打开 [dash.cloudflare.com](https://dash.cloudflare.com)，登录或注册账号。

3. **创建 Pages 项目**
   - 左侧菜单选择 **Workers & Pages** → **Create** → **Pages** → **Upload assets**（直接上传）。
   - 项目名称可填：`resume` 或 `wangzehua-portfolio`（会得到 `项目名.pages.dev` 的域名）。
   - 把刚才的 zip 拖入上传框，或点击选择文件上传。
   - 点击 **Deploy site**。

4. **访问站点**
   - 部署完成后会显示 `https://项目名.pages.dev`。
   - 根路径 `/` 会通过 `index.html` 自动跳转到个人主页。

---

## 方式二：通过 Git 仓库（适合后续经常更新）

1. **把项目推到 GitHub**
   - 在 GitHub 新建仓库，把本文件夹里的文件全部推送上去（可包含图片、PDF）。

2. **在 Cloudflare 连接仓库**
   - **Workers & Pages** → **Create** → **Pages** → **Connect to Git**。
   - 选择该 GitHub 仓库，授权 Cloudflare。
   - **Build 配置**：
     - Framework preset：**None**。
     - Build command：留空。
     - Build output directory：`/`（根目录）。
   - 保存并部署。

3. **之后更新**
   - 在本地改完代码后 `git push`，Cloudflare 会自动重新部署。

---

## 自定义域名（可选）

- 在 Pages 项目里进入 **Custom domains**，添加你的域名（如 `www.你的域名.com`）。
- 按提示在域名服务商处添加 Cloudflare 给出的 CNAME 记录即可。

---

## 注意事项

- **简历 PDF 下载**：部署到 Pages 后，PDF 通过 HTTPS 提供，点击「立即下载简历」一般会正常触发保存。
- **链接**：项目详情页的「返回主页」指向 `王泽华_AI产品实习生_个人主页.html#projects`，在 Pages 上可正常使用。
- 若根路径希望直接显示主页内容而不是跳转，可将 `王泽华_AI产品实习生_个人主页.html` 重命名为 `index.html`，并修改两个项目详情页中的返回链接为 `index.html#projects` 或 `/`。
