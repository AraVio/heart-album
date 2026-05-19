# 码云 Pages 部署指南

## 项目结构

```
heart-album/
├── index.html          # 主页面（Three.js + GSAP 单文件入口）
├── images/             # 36 张照片
│   ├── 09048828ad6bd883d21cb2d2f3dd0245.jpg
│   ├── 0ac469d58b86296831589e2d3ca55d69.jpg
│   └── ... （共 36 张）
└── DEPLOY.md           # 本说明
```

## 方案一：码云 Gitee Pages（推荐国内访问）

### 1. 创建码云仓库
- 打开 [gitee.com](https://gitee.com) 并登录
- 点击右上角 `+` → `新建仓库`
- 仓库名称：`heart-album`（可自定义）
- 选择 **公开仓库**（Pages 服务需要）
- 点击 `创建`

### 2. 上传文件到仓库
**方式 A：网页上传（最简单）**
- 进入仓库 → `文件` → `上传文件`
- 把本文件夹内的 `index.html` 和整个 `images/` 文件夹拖进去
- 等待上传完成 → 填写提交信息 → `提交`

**方式 B：Git 命令行**
```bash
cd heart-album
git init
git add .
git commit -m "init heart album"
git remote add origin https://gitee.com/你的用户名/heart-album.git
git push -u origin master
```

### 3. 开启 Pages 服务
- 仓库页面 → `服务` → `Gitee Pages`
- 部署分支选择 `master`（或 `main`）
- 部署目录留空（根目录）
- 点击 `启动`
- 等待约 1-3 分钟，会生成访问链接，如：
  `https://你的用户名.gitee.io/heart-album`

### 4. 微信分享
- 把生成的链接发到微信
- 首次打开可能需要点击右上角 `...` → `在浏览器打开`
- 建议把链接转成二维码，对方扫码即可直接打开

### 注意事项
- 码云免费 Pages **需要实名认证**才能开启
- 如遇到访问提示"已停止服务"，需重新在 Pages 页面点击 `更新` 部署
- 照片总大小若超过 50MB，建议先用工具压缩图片（如 [TinyPNG](https://tinypng.com)）

---

## 方案二：GitHub Pages（免实名，国内较慢）

- 把同样文件推送到 GitHub 仓库
- Settings → Pages → Source 选择分支
- 访问地址：`https://你的用户名.github.io/heart-album`

---

## 方案三：Vercel / Netlify（海外，访问快但需翻墙）

- 注册 [vercel.com](https://vercel.com) 或 [netlify.com](https://netlify.com)
- 直接拖拽 `heart-album` 文件夹上传
- 自动生成 HTTPS 链接

---

## 常见问题

**Q：照片加载很慢？**
- 用图片压缩工具把每张图压到 200KB 以内
- 或在 `index.html` 中降低纹理分辨率：修改 `renderer.setPixelRatio(Math.min(window.devicePixelRatio, 2))` 为 `1`

**Q：微信打不开 / 白屏？**
- 确保链接是 `https`
- 码云 Pages 国内兼容性最好
- 检查是否开启了「纯净模式」拦截了外部 CDN（Three.js / GSAP 来自 jsDelivr）

**Q：想改标题或文字？**
- 用文本编辑器打开 `index.html`
- 搜索 `心动纪念册` 和 `EVERY MOMENT WITH YOU` 替换即可
- 也可以修改 ` roseGold: 0xD4A5A5 ` 来改变边框色调
