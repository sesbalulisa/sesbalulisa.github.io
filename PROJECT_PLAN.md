# 个人博客网站项目规划书

> 参考项目:Wowchemy(现名 **HugoBlox**) —— GitHub 上最流行的 Hugo 学术/博客网站构建器
> 参考地址:https://github.com/HugoBlox/hugo-blox-builder
> 演示站:https://hugoblox.com/templates/

---

## 一、项目概述

构建一个基于 **Hugo + HugoBlox 主题** 的静态博客网站,以**中文为主**,部署在 **GitHub Pages**,通过 **GitHub Actions** 实现「推代码即自动发布」。

- **技术栈**:Hugo(静态站点生成器,Go 编写,秒级构建,零后端依赖)
- **主题**:HugoBlox Blog 模板(Bootstrap 版或 Tailwind 新版,内置 50+ 配色主题、深色模式、SEO、RSS)
- **内容格式**:Markdown(可支持 LaTeX 数学公式、代码高亮、图表、PDF 展示)
- **托管**:GitHub Pages(`yourname.github.io`)免费无限流量
- **CI/CD**:GitHub Actions 自动构建并部署

## 二、技术选型说明

| 组件 | 选择 | 理由 |
|------|------|------|
| 静态生成器 | Hugo | 构建极快,无 Node 依赖,生态成熟 |
| 主题框架 | HugoBlox(原 Wowchemy) | 模块化页面搭建,支持博客/项目/出版物,自带 SEO/RSS/深色模式 |
| 版本控制 | Git + GitHub | 代码托管 + 免费静态托管 |
| 自动化部署 | GitHub Actions | push 到 main 分支自动构建发布 |
| 编辑器 | VS Code + Hugo 插件 | 本地写作预览实时刷新 |

## 三、项目目录结构(规划)

```
my-blog/                      # 项目根目录
├── config/_default/          # 站点全局配置
│   ├── hugo.yaml             # 站点语言、标题、时间格式等
│   ├── menus.yaml            # 顶部导航菜单
│   ├── params.yaml           # 主题参数(配色、字体、SEO)
│   └── languages.yaml        # 多语言配置
├── content/
│   ├── home/                 # 首页区块(欢迎语、最新文章、标签墙)
│   ├── post/                 # 博客文章(Markdown 源文件)
│   ├── tags/                 # 标签索引页
│   ├── authors/              # 作者(个人信息、头像、社交链接)
│   └── admin/                # Decap CMS 配置(可选,网页端发文)
├── assets/                   # 自定义 CSS/JS/图片资源
├── layouts/                  # 自定义布局(覆盖主题默认样式)
├── static/                   # 静态文件(favicon、下载文件等)
├── .github/workflows/
│   └── hugo.yaml             # GitHub Actions 自动部署流水线
├── go.mod                    # Hugo 模块依赖声明
├── hugo.toml                 # 入口配置
└── README.md                 # 项目说明
```

## 四、功能规划

**首期(本次实现)**
1. 首页:个人简介 + 最新文章列表 + 标签云
2. 博客文章列表页(分页)
3. 标签/分类归档
4. 关于我页面(可选)
5. 深色/浅色模式切换
6. RSS 订阅、SEO 基础配置

**后期可选**
- 项目作品展示、出版物列表
- 中英双语切换(i18n)
- Decap CMS 网页后台在线发文
- 评论系统(Giscus/Disqus)
- 站内搜索(Fuse.js)

## 五、开发阶段规划

### 阶段 0:环境准备 ✅ 已完成
- [x] 安装 Hugo Extended 版(winget,当前 v0.164.0)
- [x] 创建 GitHub 账号/确认账号(seabalulisa),配置 gh CLI 认证
- [x] 安装 gh CLI 与 Go(用于 Hugo 模块下载)

### 阶段 1:初始化项目 ✅ 已完成
- [x] 用 HugoBlox 官方 starter 初始化项目(technical-blog 模板)
- [x] 配置站点信息(标题 YGS blog、作者 Ygs、语言设为中文、主题配色)
- [x] 本地 `hugo server` 预览确认
- [x] 提交到 GitHub 仓库 sesbalulisa/sesbalulisa.github.io(已清理模板历史)

### 阶段 2:搭建栏目与内容 ✅ 已完成
- [x] 编写首页区块(欢迎语、最新文章、标签)
- [x] 创建作者信息(头像、社交链接)
- [x] 撰写 3 篇中文示例文章(博客搭建/代码示例/部署教程)
- [x] 定制中文导航菜单与关于页

### 阶段 3:部署上线 ✅ 已完成
- [x] 配置 GitHub Actions 工作流(模板自带 deploy.yml)
- [x] Pages 切换为 workflow 模式
- [x] 验证 HTTPS、SEO、RSS 正常(线上已可访问)
- [x] 验证「推送后自动部署」全流程

### 阶段 4:持续运营 ⬜ 进行中
- [ ] 撰写 Git 提交规范、写作工作流说明(见 README)
- [ ] 维护 README,记录文章发布步骤 ✅
- [ ] 视需求开启 CMS、评论、站内搜索

## 六、部署架构

```
本地写 Markdown ──git push──▶ GitHub 仓库(main)
                                    │
                              GitHub Actions
                              (checkout + hugo build)
                                    │
                                public/ 产物
                                    │
                            GitHub Pages 发布
                                    │
                        https://<用户名>.github.io/
```

## 七、写作工作流(日常发文章)

1. 在 `content/post/` 新建 `.md` 文件,填好 front matter(标题/日期/标签)
2. `hugo server -D` 本地预览
3. `git add + commit + push`
4. GitHub Actions 自动构建 → 几分钟后线上更新

## 八、风险与注意事项

| 风险 | 应对 |
|------|------|
| Wowchemy 已更名为 HugoBlox,旧教程可能过时 | 以官方文档 docs.hugoblox.com 为准;Bootstrap 旧模板与新版 Tailwind 模板选择其一,不混用 |
| Hugo 与主题版本不兼容 | 使用主题官方 go.mod 锁定的 Hugo 版本;建议直接装 Extended 版 |
| 坚果云同步目录不适合直接跑 git | 本项目建议在独立目录初始化 git,避免云盘同步干扰 `.git` |
| GitHub Pages 仓库名规则 | 用户页必须叫 `<用户名>.github.io` 才能直接访问;项目页需开启 Pages 并选分支 |
| 国内访问 GitHub Pages 速度 | 可选绑定自定义域名或加 CDN(后期优化项) |

## 九、交付物清单

1. 可直接运行的 Hugo 博客项目(含配置与主题)
2. 3-5 篇中文示例文章
3. GitHub Actions 自动部署流水线
4. README 使用说明(本地开发/发布文章步骤)
5. 上线后的线上地址

---

*计划版本:v1.0 | 更新时间:2026-08-20*