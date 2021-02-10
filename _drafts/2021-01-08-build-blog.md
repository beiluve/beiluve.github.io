---
layout: post
title: Github Pages 博客搭建指南
description: 博客搭建
date: 2021-02-08
tags: [Github Pages]
---

## 关于 Github Pages

[Github Pages](https://docs.github.com/cn/github/working-with-github-pages) 是一个静态站点托管服务，它可以直接从你的GitHub仓库中获取HTML，CSS，JavaScript文件，通过一个构建过程运行这些文件，并发布一个网站。

你可以将你的博客站点托管在Github的`github.io`域名或者你的自定义域名上。

<!--more-->

### 站点类型

Github Pages 站点有三种类型：项目、个人、组织。项目站点会关联到你Github上的具体项目，而个人和组织站点则会关联到具体的Github账户。

* 个人站点：想要发布个人站点，必须创建一个名为`<username>.github.io`的仓库来存储站点源文件。如果没有自定义域名，默认情况下，你可以通过`http(s)://<username>.github.io`访问个人站点。

* 组织站点：想要发布组织站点，必须使用组织账号创建一个名为`<organization>.github.io`的仓库来存储站点源文件。如果没有自定义域名，默认情况下，你可以通过`http(s)://<organization>.github.io`访问组织站点。

* 项目站点：项目站点的源文件则直接存储在项目仓库中。如果没有自定义域名，默认情况下，个人或组织的项目站点则可以分别通过`http(s)://<username>.github.io/<repository>`和`http(s)://<organization>.github.io/<repository>`进行访问。

**说明：** 这里的`<username>`和`<organization>`分别表示Github个人用户名和组织用户名。

### 站点发布源

个人或组织站点的默认发布源为默认分支的根目录；项目站点的发布源为`gh-pages`分支的根目录。

你也可以更改站点的发布源。你可以将发布源更改为任意分支，还可以将源文件目录更改为`/docs`目录。如果你将发布源文件目录改为`/docs`目录，Github Pages 就会从该目录下读取所有文件并发布你的站点，包括*CNAME*文件，这意味着你的自定义域名需要存放在`/docs/CNAME`中。

### 用户限制

GitHub Pages 网站有以下使用限制：

* GitHub Pages 源存储库的建议限制为1GB。

* 已发布的 GitHub Pages 网站不得超过1GB。

* GitHub Pages 站点的软带宽限制为每月100GB。

* GGithub Pages会 在你push更改后触发自动构建，但是每个站点每小时限制构建10次版本。

## Jekyll

[jekyllCN](http://jekyllcn.com/docs/home/)
