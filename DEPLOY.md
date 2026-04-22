# 部署指南 - Netlify/Vercel

## 1. 构建项目

首先确保项目能够成功构建：

```bash
npm run build
```

## 2. 部署到 Netlify

### 方法一：通过 Git 部署（推荐）

1. **将代码推送到 GitHub/GitLab/Bitbucket**
   ```bash
   git init
   git add .
   git commit -m "Initial commit"
   git remote add origin <你的仓库地址>
   git push -u origin main
   ```

2. **在 Netlify 中导入项目**
   - 登录 [Netlify](https://app.netlify.com)
   - 点击 "Add new site" → "Import an existing project"
   - 选择 Git 提供商（GitHub/GitLab/Bitbucket）
   - 授权并选择你的仓库

3. **配置构建设置**
   - **Build command**: `npm run build`
   - **Publish directory**: `.next`
   - 点击 "Deploy site"

### 方法二：部署到 Vercel（推荐）

1. **将代码推送到 GitHub/GitLab/Bitbucket**

2. **在 Vercel 中导入项目**
   - 登录 [Vercel](https://vercel.com)
   - 点击 "Add New" → "Project"
   - 选择 Git 提供商（GitHub/GitLab/Bitbucket）
   - 授权并选择你的仓库
   - Vercel 会自动检测 Next.js 项目并配置正确的构建设置
   - 点击 "Deploy"

### 方法三：手动部署到 Netlify

1. **构建项目**
   ```bash
   npm run build
   ```

2. **在 Netlify 中手动部署**
   - 登录 [Netlify](https://app.netlify.com)
   - 点击 "Add new site" → "Deploy manually"
   - 将 `.next` 文件夹拖放到上传区域
   - 或者点击上传按钮选择 `.next` 文件夹

## 3. 环境变量配置（可选）

如果项目需要环境变量，在 Netlify 的 Site settings → Environment variables 中添加：

- `NEXT_PUBLIC_API_URL` - API 地址
- 其他需要的变量

## 4. 自定义域名（可选）

1. 在 Netlify 的 Domain settings 中
2. 点击 "Add custom domain"
3. 输入你的域名并按照提示配置 DNS

## 5. 项目信息

- **项目名称**: 木叶-魔龙的后宫
- **框架**: Next.js 14
- **构建输出**: `out` 文件夹
- **密码**: dragon123（隐蔽空间）

## 6. 功能清单

✅ 视频上传和播放功能
✅ 视频时长和观看次数统计
✅ 相册功能（支持图片和视频）
✅ 聊天功能
✅ 音乐播放功能
✅ 日历功能
✅ 论坛功能
✅ 响应式设计
✅ 暗色模式支持

## 7. 注意事项

1. 项目使用 localStorage 存储数据，部署后数据会保存在用户浏览器中
2. 视频和图片上传使用 Data URL 格式，大文件可能会占用较多存储空间
3. 确保浏览器支持 HTML5 video 标签以正常播放视频

## 8. 故障排除

如果部署后出现问题：

1. 检查构建日志是否有错误
2. 确认 `.next` 文件夹包含所有必要文件
3. 检查浏览器控制台是否有 JavaScript 错误
4. 验证所有资源文件（图片、视频）是否正确加载

## 9. 更新部署

当代码更新后：

1. 重新构建项目：`npm run build`
2. 如果是 Git 部署，推送代码后会自动重新部署
3. 如果是手动部署，需要重新上传 `out` 文件夹

---

**部署完成后，您将获得一个类似 `https://xxx.netlify.app` 的网址。**
