# YGS blog

基于 [Hugo](https://gohugo.io) + [HugoBlox](https://hugoblox.com)(原 Wowchemy) 的个人博客,中文为主,自动部署到 GitHub Pages。

🔗 在线地址:https://sesbalulisa.github.io/

## 技术栈

- **Hugo**(Extended 版)+ HugoBlox Blog 模板
- **GitHub Pages** 托管 + **GitHub Actions** 自动部署
- 内容用 **Markdown** 编写,支持代码高亮、LaTeX 公式、Mermaid 图表

## 目录结构

```
├── config/_default/   # 站点配置(标题、菜单、语言、主题参数)
├── content/
│   ├── home/          # 首页区块
│   ├── blog/          # 博客文章(Markdown)
│   ├── tags/          # 标签
│   ├── authors/       # 作者信息
│   └── about.md       # 关于页面
├── data/authors/      # 作者档案
├── assets/            # 自定义资源
├── static/            # 静态文件
└── .github/workflows/ # GitHub Actions 部署流水线
```

## 本地开发

前置要求:Hugo Extended、Node.js、Go

```bash
# 安装依赖(首次)
npm install

# 本地预览(默认 http://localhost:1313)
npm run dev
```

## 发布新文章

1. 在 `content/blog/<文章名>/` 下新建 `index.md`
2. 填写 front matter:

```markdown
---
title: 文章标题
summary: 文章摘要
date: 2026-01-01
authors:
  - me
tags:
  - 标签A
---
```

3. 本地预览确认后提交推送:

```bash
git add .
git commit -m "添加新文章:xxx"
git push
```

4. GitHub Actions 会自动构建并发布,几分钟后线上更新

## 自动化部署

`.github/workflows/deploy.yml` 配置了完整流水线:
- 推送 `main` 分支自动触发构建
- Hugo 构建后通过 `actions/deploy-pages` 发布到 GitHub Pages

仓库 Settings → Pages 中,发布源需选择 **GitHub Actions**。

## 常用自定义

- **站点信息 / 配色**:编辑 `config/_default/params.yaml`
- **导航菜单**:编辑 `config/_default/menus.yaml`
- **个人档案**:编辑 `data/authors/me.yaml`

## 授权

基于 [HugoBlox](https://github.com/HugoBlox/kit) 的 MIT License 模板构建,内容版权归作者所有。