---
title: Hexo博客创建与发布流程
date: 2026-05-28 00:00:00
tags:
  - Hexo
  - GitHub Pages
  - 博客
categories:
  - 博客搭建
---

# Hexo博客创建与发布流程

<!-- more -->

## 第一章 准备工作

搭建博客之前，需要先准备好下面几个软件：

1. Node.js

   官网地址：

   ```text
   https://nodejs.org
   ```

   安装 Node.js 后，会同时安装 npm。

   查看版本：

   ```powershell
   node -v
   npm -v
   npx -v
   ```

2. Git

   官网地址：

   ```text
   https://git-scm.com
   ```

   查看版本：

   ```powershell
   git --version
   ```

3. VS Code

   用来编辑博客文章和配置文件。

   查看是否可以在命令行中打开 VS Code：

   ```powershell
   code -v
   ```

## 第二章 创建本地博客

选择一个本地文件夹保存博客资料，本次博客文件夹为：

```text
D:\code data\my-blog
```

进入上一级目录：

```powershell
cd "D:\code data"
```

使用 Hexo 初始化博客：

```powershell
npx hexo-cli init "D:\code data\my-blog"
```

进入博客目录：

```powershell
cd "D:\code data\my-blog"
```

安装项目依赖：

```powershell
npm install
```

查看生成的目录：

```powershell
dir
```

常见目录和文件包括：

```text
_config.yml
package.json
source
scaffolds
themes
```

其中：

```text
_config.yml：博客主配置文件
source/_posts：存放博客文章
themes：存放博客主题
```

## 第三章 本地预览博客

启动本地预览服务：

```powershell
npx hexo server
```

浏览器打开：

```text
http://localhost:4000/
```

如果能看到博客首页，说明本地博客已经创建成功。

停止本地预览服务：

```text
Ctrl + C
```

## 第四章 创建第一篇文章

在博客目录中执行：

```powershell
npx hexo new "我的第一篇博客"
```

文章会生成在：

```text
D:\code data\my-blog\source\_posts
```

可以使用 VS Code 打开博客文件夹：

```powershell
code .
```

然后编辑 `source/_posts` 目录下的 Markdown 文件。

编辑完成后，再次启动本地预览：

```powershell
npx hexo server
```

浏览器打开：

```text
http://localhost:4000/
```

确认文章可以正常显示。

## 第五章 创建 GitHub 仓库

打开 GitHub 新建仓库页面：

```text
https://github.com/new
```

本次仓库信息：

```text
Owner: taojinlab
Repository name: my-blog
Visibility: Public
```

下面三个选项不要勾选：

```text
Add a README file
Add .gitignore
Choose a license
```

创建完成后，仓库地址为：

```text
https://github.com/taojinlab/my-blog
```

## 第六章 初始化 Git 并上传源码

进入博客目录：

```powershell
cd "D:\code data\my-blog"
```

初始化 Git 仓库：

```powershell
git init
```

将默认分支改为 `main`：

```powershell
git branch -M main
```

添加远程仓库：

```powershell
git remote add origin https://github.com/taojinlab/my-blog.git
```

保存本地源码：

```powershell
git add .
git commit -m "Initialize Hexo blog"
```

上传到 GitHub：

```powershell
git push -u origin main
```

如果 Git 提示 `detected dubious ownership`，说明 Git 认为当前目录的所有者和当前用户不一致。可以执行：

```powershell
git config --global --add safe.directory "D:/code data/my-blog"
```

然后重新执行：

```powershell
git push -u origin main
```

## 第七章 安装发布插件

Hexo 需要安装 Git 发布插件，才能把生成后的网页发布到 GitHub：

```powershell
npm install hexo-deployer-git --save
```

安装完成后，保存依赖变化：

```powershell
git add package.json package-lock.json
git commit -m "Add Hexo Git deployer"
git push
```

## 第八章 配置博客发布信息

打开博客配置文件：

```text
D:\code data\my-blog\_config.yml
```

修改站点基础信息：

```yaml
title: Taojin Lab
subtitle: '个人博客'
description: '记录学习、思考与实践'
keywords: 博客, 学习, 技术, 记录
author: taojinlab
language: zh-CN
timezone: 'Asia/Shanghai'
```

修改网站地址：

```yaml
url: https://taojinlab.github.io/my-blog
```

修改发布配置：

```yaml
deploy:
  type: git
  repo: https://github.com/taojinlab/my-blog.git
  branch: gh-pages
```

说明：

```text
main 分支：保存 Hexo 源码、Markdown 文章、配置文件
gh-pages 分支：保存 Hexo 生成后的静态网页
```

保存配置修改：

```powershell
git add _config.yml
git commit -m "Update Hexo config"
git push
```

## 第九章 生成并发布网站

清理旧的生成文件：

```powershell
npx hexo clean
```

重新生成网页：

```powershell
npx hexo generate
```

发布到 GitHub：

```powershell
npx hexo deploy
```

发布成功后，GitHub 仓库中会出现 `gh-pages` 分支。

## 第十章 开启 GitHub Pages

打开仓库页面：

```text
https://github.com/taojinlab/my-blog
```

进入：

```text
Settings -> Pages
```

在 `Build and deployment` 中设置：

```text
Source: Deploy from a branch
Branch: gh-pages
Folder: /root
```

保存后等待一会儿，访问博客：

```text
https://taojinlab.github.io/my-blog/
```

如果页面可以打开，说明博客已经发布成功。

## 第十一章 清理默认文章

Hexo 默认会生成一篇 `hello-world.md` 示例文章。

如果不需要，可以删除：

```text
D:\code data\my-blog\source\_posts\hello-world.md
```

删除后重新生成并发布：

```powershell
npx hexo clean
npx hexo generate
npx hexo deploy
```

同时保存源码变化：

```powershell
git add .
git commit -m "Remove sample post"
git push
```

## 第十二章 今后发布博客的操作流程

以后写新文章时，进入博客目录：

```powershell
cd "D:\code data\my-blog"
```

新建文章：

```powershell
npx hexo new "文章标题"
```

编辑文章：

```text
D:\code data\my-blog\source\_posts
```

本地预览：

```powershell
npx hexo server
```

浏览器打开：

```text
http://localhost:4000/
```

确认无误后，先保存源码到 GitHub：

```powershell
git add .
git commit -m "Add new post"
git push
```

然后发布网站：

```powershell
npx hexo clean
npx hexo generate
npx hexo deploy
```

最终访问：

```text
https://taojinlab.github.io/my-blog/
```

简单记忆：

```text
写文章 -> 本地预览 -> git push 保存源码 -> hexo deploy 发布网站
```
