---
layout: post
title: Jekyll安装与本地构建
description: Jekyll
date: 2021-01-25
tags: [Jekyll]
---

我们可以通过Github提供的Github-Pages很方便地搭建个人博客，而Github-Pages默认的构建工具是Jekyll。

本文主要介绍如何在Ubuntu系统上安装配置Jekyll环境，用于在本地构建和调试你的Github-Pages项目。

<!--more-->

## 预安装

Jekyll依赖Ruby环境，在安装Jekyll之前要先安装好Ruby和RubyGems。

```shell
# 1.安装ruby
$ sudo apt install ruby-full ruby-bundler

# 2.验证ruby安装版本
$ ruby -v
ruby 2.7.0p0 (2019-12-25 revision 647ee6f091) [x86_64-linux-gnu]

# 3.验证gem安装版本
$ gem -v
3.1.2

# 4.配置国内gem source（https://rubygems.org太慢）
$ gem sources --add https://gems.ruby-china.com/ --remove https://rubygems.org/

# 5.验证gem source配置，确保只有 https://gems.ruby-china.com
$ gem sources -l
https://gems.ruby-china.com
```

至此，安装Jekyll的准备工作就完成了，接下来开始安装Jekyll。

## 安装Jekyll

安装Jekyll的步骤很简单：

```shell
# 使用gem安装jekyll
$ sudo gem install jekyll

# 验证jekyll安装版本
$ jekyll -v
jekyll 4.2.0
```

至此，Jekyll就已经安装好了。

## 在本地构建Github-Pages项目

1. 将你的Github-Pages项目`clone`到本地，并切换到正确分支

1. 开始构建

    ```shell
    # 修改bundle镜像配置，这样就不用修改Gemfile中的source配置
    $ bundle config mirror.https://rubygems.org https://gems.ruby-china.com

    # 先使用bundle安装Gemfile配置中的插件
    $ bundle install

    # 启动项目
    $ jekyll serve
    ```

1. 本地默认访问地址：`http://127.0.0.1:4000`
