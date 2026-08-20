---
title: "如何把博客托管到 GitHub Pages"
summary: "利用 GitHub Actions 实现推送代码后自动构建并发布到 GitHub Pages，全程零服务器成本。"
date: 2026-08-18
image:
  caption: ''

authors:
  - me

tags:
  - GitHub
  - 部署
---

GitHub Pages 可以为静态网站提供**免费托管**，配合 GitHub Actions 可以实现「推代码即发布」的自动化流程。

## 托管原理

```
本地写 Markdown ── git push ──▶ GitHub 仓库(main 分支)
                                      │
                              GitHub Actions 自动构建
                                      │
                              GitHub Pages 发布上线
```

## 核心配置

1. 仓库 `Settings → Pages` 中选择 **GitHub Actions** 作为发布来源
2. 在仓库中放置 `.github/workflows/deploy.yml` 部署流水线
3. 推送代码后,在 `Actions` 标签页即可看到自动构建进度

## 自定义域名(可选)

在仓库 `Settings → Pages → Custom domain` 中绑定自己的域名,然后在域名服务商添加 CNAME 记录指向 `<用户名>.github.io` 即可。

## 小结

整个部署链路零成本、零维护,文章写好推送即可,非常适合个人博客。想了解本地写作流程可以看[这篇](/blog/get-started/)。