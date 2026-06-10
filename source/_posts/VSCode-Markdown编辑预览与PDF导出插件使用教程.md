---
title: VS Code 中 Markdown 编辑、预览与 PDF 导出插件使用教程
date: 2026-06-10 16:00:00
tags:
  - VS Code
  - Markdown
  - PDF
  - 写作工具
categories:
  - 工具教程
---

# VS Code 中 Markdown 编辑、预览与 PDF 导出插件使用教程

这篇笔记主要记录我在 VS Code 中编辑 Markdown、浏览 Markdown、导出 PDF 时常用的三个插件：

1. **Markdown All in One**：主要负责 Markdown 写作增强。
2. **Markdown Preview Enhanced**：主要负责增强预览、公式、图表和复杂文档查看。
3. **Markdown PDF**：主要负责把 Markdown 稳定导出为 PDF、HTML、PNG、JPEG。

<!-- more -->

如果只是平时写博客、整理实验记录、写说明文档，我推荐的组合是：

```text
Markdown All in One 负责写
Markdown Preview Enhanced 负责看
Markdown PDF 负责导出
```

## 一、安装插件

在 VS Code 左侧点击 **扩展**，分别搜索并安装下面三个插件。

| 插件名称 | 插件 ID | 主要用途 |
| --- | --- | --- |
| Markdown All in One | `yzhang.markdown-all-in-one` | 快捷键、目录、列表、表格、写作增强 |
| Markdown Preview Enhanced | `shd101wyy.markdown-preview-enhanced` | 增强预览、公式、流程图、Mermaid、导出辅助 |
| Markdown PDF | `yzane.markdown-pdf` | 导出 PDF、HTML、PNG、JPEG |

也可以在 VS Code 中按 `Ctrl + P`，输入下面命令安装：

```text
ext install yzhang.markdown-all-in-one
ext install shd101wyy.markdown-preview-enhanced
ext install yzane.markdown-pdf
```

官方资料：

- [Markdown All in One](https://marketplace.visualstudio.com/items?itemName=yzhang.markdown-all-in-one)
- [Markdown Preview Enhanced](https://marketplace.visualstudio.com/items?itemName=shd101wyy.markdown-preview-enhanced)
- [Markdown PDF](https://marketplace.visualstudio.com/items?itemName=yzane.markdown-pdf)

## 二、Markdown All in One：负责高效写作

这个插件适合用来提升 Markdown 的编辑效率。它提供快捷键、自动目录、列表编辑、表格格式化、任务列表等功能。

### 1. 常用功能

| 功能 | 作用 | 使用场景 |
| --- | --- | --- |
| 加粗、斜体快捷键 | 快速设置文字格式 | 写博客、说明文档、实验记录 |
| 自动生成目录 | 根据标题生成目录 | 长文档、教程、论文笔记 |
| 自动更新目录 | 保存时自动更新目录 | 文章结构经常修改时 |
| 列表自动补全 | 回车后自动延续列表 | 写步骤、清单、流程 |
| 表格格式化 | 自动对齐 Markdown 表格 | 写参数表、结果表 |
| 任务列表 | 支持 `- [ ]` 和 `- [x]` | 写待办事项 |

### 2. 常用快捷键

| 快捷键 | 作用 |
| --- | --- |
| `Ctrl + B` | 加粗 |
| `Ctrl + I` | 斜体 |
| `Ctrl + Shift + ]` | 提升标题级别 |
| `Ctrl + Shift + [` | 降低标题级别 |
| `Ctrl + Shift + V` | 打开或关闭预览 |
| `Ctrl + K` 后按 `V` | 在右侧打开预览 |

### 3. 生成目录

打开 Markdown 文件后，按 `Ctrl + Shift + P`，输入：

```text
Markdown All in One: Create Table of Contents
```

插件会根据文档中的标题自动生成目录。以后只要保存文件，目录通常会自动更新。

建议文章标题使用清晰的层级：

```markdown
# 一级标题

## 二级标题

### 三级标题
```

不要为了让字体变大而乱用标题级别。标题层级越清楚，目录越稳定，博客显示也越好看。

### 4. 表格格式化

写表格时可以先写成下面这样：

```markdown
| 插件 | 作用 |
| --- | --- |
| Markdown All in One | 编辑增强 |
| Markdown PDF | 导出 PDF |
```

然后右键或通过命令面板执行格式化，表格会变得更整齐。

### 5. 推荐设置

打开 VS Code 的 `settings.json`，可以加入下面配置：

```json
{
  "markdown.extension.toc.updateOnSave": true,
  "markdown.extension.toc.levels": "2..4",
  "markdown.extension.orderedList.autoRenumber": true,
  "markdown.extension.tableFormatter.enabled": true
}
```

这些设置的含义是：

| 设置 | 含义 |
| --- | --- |
| `toc.updateOnSave` | 保存时自动更新目录 |
| `toc.levels` | 控制目录收录哪些标题级别 |
| `orderedList.autoRenumber` | 自动修正有序列表编号 |
| `tableFormatter.enabled` | 启用表格格式化 |

## 三、Markdown Preview Enhanced：负责增强预览

Markdown Preview Enhanced 更适合查看复杂 Markdown。它支持滚动同步、数学公式、Mermaid 图、PlantUML、代码块、PDF 导出等功能。

### 1. 适合什么场景

| 场景 | 是否推荐 |
| --- | --- |
| 写普通博客 | 推荐 |
| 写带公式的文档 | 推荐 |
| 写流程图、结构图 | 推荐 |
| 写实验流程记录 | 推荐 |
| 只想简单导出 PDF | 可以用，但更推荐 Markdown PDF |

### 2. 打开预览

打开 Markdown 文件后，可以使用：

```text
Ctrl + Shift + V
```

或者按 `Ctrl + Shift + P`，输入：

```text
Markdown Preview Enhanced: Open Preview
```

如果想一边写一边看，可以选择在右侧打开预览。

### 3. 数学公式

Markdown Preview Enhanced 适合写公式，例如：

```markdown
行内公式：$E = mc^2$

独立公式：

$$
y = ax + b
$$
```

这类功能适合写科研笔记、数据分析说明、实验方法文档。

### 4. Mermaid 图

可以直接在 Markdown 中写流程图：

````markdown
```mermaid
flowchart LR
    A[写 Markdown] --> B[预览]
    B --> C[导出 PDF]
```
````

适合画流程、技术路线、实验步骤、数据处理过程。

### 5. 在浏览器中查看

如果 VS Code 预览窗口显示正常，但想在浏览器中检查排版，可以在预览窗口中右键，选择：

```text
Open in Browser
```

如果浏览器打开后是空白，通常检查下面几点：

1. Markdown 文件是否保存。
2. 文件路径中是否有特殊字符。
3. 图片路径是否正确。
4. VS Code 是否信任当前工作区。
5. 插件是否需要重启 VS Code 才能生效。

### 6. 关于 PrinceXML 提示

有时 Markdown Preview Enhanced 导出 PDF 会提示：

```text
"princexml" is required to be installed.
```

这是因为它的某些 PDF 导出方式依赖外部工具 PrinceXML。对于普通用户来说，不一定需要安装 PrinceXML。更简单的办法是：

```text
用 Markdown Preview Enhanced 负责预览
用 Markdown PDF 负责导出 PDF
```

这样通常更省事，也更稳定。

## 四、Markdown PDF：负责导出 PDF

Markdown PDF 的目标很明确，就是把 Markdown 转换为 PDF，也可以导出 HTML、PNG、JPEG。

### 1. 常用导出格式

| 格式 | 适合用途 |
| --- | --- |
| PDF | 正式传阅、打印、提交材料 |
| HTML | 网页查看、保留样式 |
| PNG | 截图式分享 |
| JPEG | 图片式分享 |

### 2. 导出 PDF 的方法

打开 Markdown 文件后，右键点击编辑区，选择：

```text
markdown-pdf: Export (pdf)
```

也可以按 `Ctrl + Shift + P`，输入：

```text
markdown-pdf: Export (pdf)
```

导出的 PDF 通常会保存在 Markdown 文件所在文件夹中。

### 3. 一次导出多种格式

如果想同时导出 PDF、HTML、PNG、JPEG，可以选择：

```text
markdown-pdf: Export (all: pdf, html, png, jpeg)
```

也可以在 `settings.json` 中设置：

```json
{
  "markdown-pdf.type": [
    "pdf",
    "html"
  ]
}
```

这样导出时会同时生成 PDF 和 HTML。

### 4. 推荐设置

```json
{
  "markdown-pdf.type": "pdf",
  "markdown-pdf.outputDirectory": "",
  "markdown-pdf.convertOnSave": false,
  "markdown-pdf.printBackground": true,
  "markdown-pdf.format": "A4",
  "markdown-pdf.margin.top": "20mm",
  "markdown-pdf.margin.bottom": "20mm",
  "markdown-pdf.margin.left": "18mm",
  "markdown-pdf.margin.right": "18mm"
}
```

这些设置适合大多数中文文档：

| 设置 | 含义 |
| --- | --- |
| `type` | 默认导出 PDF |
| `outputDirectory` | 留空表示输出到当前文件夹 |
| `convertOnSave` | 保存时不自动导出，避免生成太多文件 |
| `printBackground` | 保留背景色和代码块背景 |
| `format` | 使用 A4 页面 |
| `margin` | 控制页边距 |

### 5. 自定义 PDF 样式

如果希望 PDF 更像正式文档，可以新建一个 CSS 文件，例如：

```text
markdown-pdf.css
```

写入：

```css
body {
  font-family: "Microsoft YaHei", "SimSun", Arial, sans-serif;
  font-size: 11pt;
  line-height: 1.75;
  color: #222;
}

h1, h2, h3 {
  color: #1f4e79;
}

table {
  width: 100%;
  border-collapse: collapse;
}

th, td {
  border: 1px solid #cccccc;
  padding: 6px 8px;
}

code {
  font-family: Consolas, "Courier New", monospace;
}
```

然后在 `settings.json` 中添加：

```json
{
  "markdown-pdf.styles": [
    "markdown-pdf.css"
  ]
}
```

这样导出的 PDF 会使用自定义样式。

## 五、我的推荐工作流程

### 1. 写博客

```text
用 Markdown All in One 写正文
用 Markdown Preview Enhanced 检查预览
用 Hexo 生成博客页面
```

适合发布到个人博客、GitHub Pages、实验室网站。

### 2. 写可传阅材料

```text
用 Markdown All in One 写正文
用 Markdown Preview Enhanced 检查版式
用 Markdown PDF 导出 PDF
```

适合公司简介、项目介绍、操作说明、实验记录。

### 3. 写科研笔记

```text
Markdown All in One：整理标题、表格、目录
Markdown Preview Enhanced：查看公式、流程图、图表
Markdown PDF：导出正式 PDF
```

适合方法记录、数据分析流程、论文阅读笔记。

## 六、常见问题

### 1. 为什么导出的 PDF 是空白？

可能原因：

1. Markdown 文件没有保存。
2. 图片路径错误，导致导出卡住或显示异常。
3. 文档中有复杂 HTML，导出插件没有正常解析。
4. 插件冲突，建议禁用其它 Markdown 插件后再试。
5. VS Code 没有信任当前工作区。
6. Markdown PDF 需要可用的 Chrome、Edge 或 Chromium。

解决顺序建议：

```text
保存文件
重启 VS Code
换一个最简单的 Markdown 文件测试
检查图片路径
使用 Markdown PDF 导出
```

### 2. 为什么浏览器打开预览是空白？

通常先检查：

1. 文件是否保存。
2. 预览窗口本身是否正常。
3. 浏览器是否拦截本地资源。
4. 图片路径是否用了错误的绝对路径。
5. 插件是否需要重新加载窗口。

可以在 VS Code 中执行：

```text
Developer: Reload Window
```

然后重新打开预览。

### 3. 为什么 Markdown Preview Enhanced 要求安装 PrinceXML？

这是某些 PDF 导出方式需要的外部程序。普通写作不一定要装。更推荐把职责分开：

```text
Markdown Preview Enhanced 只负责预览
Markdown PDF 负责导出 PDF
```

### 4. 图片应该怎么写路径？

建议把图片放在 Markdown 文件附近，例如：

```text
文章.md
images/
  figure1.png
```

然后在 Markdown 中写：

```markdown
![图片说明](images/figure1.png)
```

这样无论预览、导出 PDF，还是发布到博客，都更容易管理。

### 5. 中文文件名可以用吗？

可以用，但如果导出或浏览器预览出现问题，可以先测试英文路径。比如把：

```text
D:\我的文档\公司简介.md
```

临时改成：

```text
D:\docs\company-profile.md
```

如果英文路径正常，说明问题可能来自路径编码或插件对特殊字符的兼容性。

## 七、推荐组合总结

| 需求 | 推荐插件 |
| --- | --- |
| 快速写 Markdown | Markdown All in One |
| 自动生成目录 | Markdown All in One |
| 写表格 | Markdown All in One |
| 预览公式 | Markdown Preview Enhanced |
| 预览 Mermaid 图 | Markdown Preview Enhanced |
| 导出 PDF | Markdown PDF |
| 导出 HTML、PNG、JPEG | Markdown PDF |
| 写博客 | Markdown All in One + Markdown Preview Enhanced |
| 做可传阅 PDF | Markdown All in One + Markdown PDF |

最省心的使用方式是：不要让一个插件承担所有任务，而是让三个插件各做自己最擅长的事。

```text
写作：Markdown All in One
预览：Markdown Preview Enhanced
导出：Markdown PDF
```

这样在 VS Code 中就可以完成从 Markdown 写作、实时预览到 PDF 导出的完整流程。
