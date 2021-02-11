---
layout: post
title: Github Pages 博客搭建说明
description: 博客搭建
date: 2021-02-10
tags: [Github Pages]
---

本文是一篇使用 Github Pages 搭建博客的说明，并非具体的博客搭建教程。详细教程请参考本文末尾的链接。

<!--more-->

## 关于 Github Pages

Github Pages 是一个静态站点托管服务，它可以直接从你的Github仓库中获取HTML，CSS，JavaScript文件，通过一个构建过程运行这些文件，并发布一个网站。

你可以将你的博客站点托管在Github的`github.io`域名或者你的自定义域名上。

### 站点类型

Github Pages 站点有三种类型：项目、个人、组织。项目站点会关联到你Github上的具体项目，而个人和组织站点则会关联到具体的Github账户。

* 个人站点：想要发布个人站点，必须创建一个名为`<username>.github.io`的仓库来存储站点源文件。如果没有自定义域名，默认情况下，你可以通过`http(s)://<username>.github.io`访问发布后的个人站点。

* 组织站点：想要发布组织站点，必须使用组织账号创建一个名为`<organization>.github.io`的仓库来存储站点源文件。如果没有自定义域名，默认情况下，你可以通过`http(s)://<organization>.github.io`访问发布后的组织站点。

* 项目站点：项目站点的源文件则直接存储在项目仓库中。如果没有自定义域名，默认情况下，个人或组织的项目站点则可以分别通过`http(s)://<username>.github.io/<repository>`和`http(s)://<organization>.github.io/<repository>`进行访问。

**说明：** 这里的`<username>`和`<organization>`分别表示Github个人用户名和组织用户名，`<repository>`表示代码库名称。


### 站点发布源

个人或组织站点的默认发布源为默认分支的根目录；项目站点的发布源为`gh-pages`分支的根目录。

你也可以更改站点的发布源。你可以将发布源更改为任意分支，还可以将源文件目录更改为`/docs`目录。如果你将发布源文件目录改为`/docs`目录，Github Pages 就会从该目录下读取所有文件并发布你的站点，包括*CNAME*文件，这意味着你的自定义域名需要存放在`/docs/CNAME`中。

**说明：** *CNAME*即别名记录，它可以把域名解析到另外一个域名，该文件可以用来解析你的自定义域名。

### 用户限制

GitHub Pages 网站有以下使用限制：

* GitHub Pages 源存储库的建议限制为1GB。

* 已发布的 GitHub Pages 网站不得超过1GB。

* GitHub Pages 站点的软带宽限制为每月100GB。

* Github Pages 会在你push更改后触发自动构建，但是每个站点每小时限制构建10次版本。

详细的 Github Pages 教程请参考[Github Pages指南](https://docs.github.com/cn/github/working-with-github-pages)。

## 静态站点生成器

Github Pages 可以发布你代码库中的任何静态文件，其默认的静态站点生成器是 Jekyll。你也可以使用其他的站点生成器来构建你的静态站点，例如：Hexo、Gitbook。

如果你不想使用 Jekyll 构建你的站点，则需要在你的发布源根目录下创建一个名为`.nojekyll`的空文件。

### Jekyll

Jekyll 是一个简单的静态站点生成器。它有一个模板目录，其中包含原始文本格式的文档，然后通过一个转换器（如 Markdown）和 Liquid 渲染器转化成一个完整的可发布的静态网站。详细的Jekyll教程请参考[jekyllCN](http://jekyllcn.com/docs/home/)。

### Hexo

Hexo 是一个快速、简洁且高效的博客框架，它基于 Node.js，使用 Markdown(或其他渲染引擎)来解析文章，并生成静态网页。详细的 Hexo 教程请参考[Hexo中文官网](https://hexo.io/zh-cn/)。

### Gitbook

Gitbook 是一个使用 Git 和 Markdown 来构建书籍的工具。它可以将你的文档输出很多格式：PDF，ePub，mobi，或者输出为静态网页。详细的 Gitbook 教程请参考[GitBook文档（中文版）](https://chrisniael.gitbooks.io/gitbook-documentation/content/index.html)

## 参考

本文中涉及的静态站点构建技术具体请参考如下链接：

- [Github Pages指南](https://docs.github.com/cn/github/working-with-github-pages)

- [jekyllCN](http://jekyllcn.com/docs/home/)

- [Hexo中文官网](https://hexo.io/zh-cn/)

- [GitBook文档（中文版）](https://chrisniael.gitbooks.io/gitbook-documentation/content/index.html)

- [Markdown语法教程](https://markdown.com.cn/)

- [Liquid模板语言](https://liquid.bootcss.com/)
