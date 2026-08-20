---
title: 🎉 博客搭建完成，欢迎来到 YGS blog
summary: 从零开始搭建一个属于自己的静态博客网站，并托管到 GitHub Pages。
date: 2026-08-20

# Featured image
# Place an image named `featured.jpg/png` in this page's folder and customize its options here.
image:
  caption: ''

authors:
  - me

tags:
  - Hugo
  - 博客搭建
---

欢迎来到 **YGS blog** 👋

这是我使用 [Hugo](https://gohugo.io) 与 [HugoBlox](https://hugoblox.com)(原 Wowchemy) 构建的个人博客。

{{< toc mobile_only=true is_open=true >}}

## 为什么选择 Hugo + HugoBlox

1. **完全静态**：构建后只有 HTML/CSS/JS 文件，无服务器、无数据库，免费托管
2. **极速构建**：Hugo 由 Go 编写，上千篇文章也能秒级构建
3. **Markdown 写作**：用最简单的方式记录内容，还能支持 LaTeX 公式、代码高亮
4. **易于部署**：推送到 GitHub 即可通过 GitHub Actions 自动发布

## 如何发布新文章

1. 在 `content/blog/` 目录下新建文件夹与 `index.md`
2. 在 Markdown 顶部填写 front matter（标题、日期、标签）
3. 本地 `hugo server` 预览
4. `git push` 后自动部署上线

## 更多功能

- 🏷️ 标签归档
- 📡 RSS 订阅
- 🌙 深色 / 浅色模式
- 🔍 站内搜索
- 📖 阅读时间统计

祝你阅读愉快！