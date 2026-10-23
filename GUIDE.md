# Branches 实验室官网维护指南

本指南将帮助你了解如何预览、修改内容以及发布你的实验室官网。

## 1. 环境准备

确保你的开发环境中已安装以下工具：
- **Hugo (Extended 版)**: 建议版本 v0.128.0 或更高。
- **Go**: 用于管理 Hugo 模块。
- **Git**: 用于版本控制和发布。

## 2. 本地预览

在项目根目录下运行以下命令启动本地服务器：

```bash
hugo server
```

- **访问地址**: 默认在 `http://localhost:1313/` 预览。
- **实时更新**: 修改任何 Markdown 文件后，页面会自动刷新。

## 3. 内容修改与更新

所有的内容都存放在 `content/en/` 目录下。

### 3.1 更新首页 (Home)
首页由多个组件（Widgets）组成，存放在 `content/en/home/`：
- `hero.md`: 修改实验室名称和口号。
- `intro.md`: 修改实验室简介。
- `news.md`: 配置最新动态的显示数量。
- `projects.md`: 配置精选成果的展示方式。
- `team.md`: 首页成员展示区域。

### 3.2 添加成员 (Members)
1. 在 `content/en/authors/` 下新建一个文件夹（例如 `zhang-san`）。
2. 在该文件夹内创建 `_index.md`。
3. 放入头像文件 `avatar.jpg`。
4. 在 `_index.md` 中填写个人信息和社交链接。

### 3.3 发布科研成果 (Projects)
1. 在 `content/en/projects/` 下新建文件夹（例如 `my-new-project`）。
2. 创建 `index.md` 并填写成果摘要。
3. 放入封面图 `featured.jpg` 或首页展示图 `preview.svg` / `preview.jpg`。
4. 如果想让项目出现在首页第二屏展示区，请在 Front Matter 中增加这些字段：
   ```yaml
   weight: 10
   showcase: true
   showcase_label: Reconstruction Demo
   showcase_format: Image Preview
   showcase_chip: Sparse-to-3D
   showcase_image: preview.svg
   showcase_summary: Short text shown below the preview.
   showcase_points:
     - first highlight
     - second highlight
     - third highlight
   demo_url: https://example.com/demo
   source_url: https://github.com/your-org/your-project
   ```
5. 如果有视频，也可以改为：
   ```yaml
   showcase_video: teaser.mp4
   showcase_image: poster.jpg
   ```
6. 在正文中可以插入更多图片、视频链接或详细介绍。

### 3.4 撰写技术洞察/笔记 (Insights)
1. 在 `content/en/posts/` 下新建文件夹。
2. 创建 `index.md` 撰写内容。
3. 建议统一将“新闻”和“文章/笔记”都放在 `posts/` 下，用 `categories` 区分类型，例如 `News`、`Insight`、`Research`、`Blog`。
4. 推荐的 Front Matter 示例：
   ```yaml
   title: A New Lab Update
   date: 2026-10-22
   categories:
     - News
   tags:
     - 3D Reconstruction
   summary: One paragraph summary.
   ```
5. 首页的 `Latest Updates` 模块默认只展示最近 4 篇内容，超出的内容仍会保留在 `Research & Insights` 列表页中。

## 4. 视觉与配置调整

- **全局配置**: `config/_default/params.yaml` 中可以修改实验室名称、Logo 文本、颜色模式等。
- **菜单导航**: `config/_default/menus.yaml` 中可以调整顶部导航条的链接。
- **自定义样式**: 如果需要微调视觉细节，可以修改 `assets/scss/custom.scss`。

## 5. 发布到 GitHub Pages

项目已配置 GitHub Actions 自动部署。

1. **创建仓库**: 在 GitHub 上创建一个名为 `branches-lab.github.io` 的仓库。
2. **关联并推送**:
   ```bash
   git init
   git add .
   git commit -m "Initial lab website"
   git remote add origin https://github.com/[你的用户名]/branches-lab.github.io.git
   git branch -M main
   git push -u origin main
   ```
3. **自动部署**: 推送成功后，GitHub Actions 会自动触发构建任务。约 1-2 分钟后，你就可以通过 `https://[你的用户名].github.io/` 访问官网。

---
**Branches Lab - 探索 3D 重建、AIGC 与 Agent 的前沿。**
