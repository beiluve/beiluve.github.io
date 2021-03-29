---
layout: post
title: Deepin Linux 环境搭建
description: 折腾
date: 2021-03-29
tags: [linux,deepin]
---

经过一系列尝试和挣扎，决定将国产Deepin系统作为linux系统环境，在此记录下环境构建的过程，以备后用。

<!--more-->

## 环境安装和配置

### 安装Git

```bash
# 安装git
sudo apt install git

# 配置全局 user.name 和 user.email
$ git config --global user.name "username"
$ git config --global user.email "email"

# 执行 ssh-keygen
$ ssh-keygen -t rsa
```

### 安装OpenJDK8

```bash
# 安装
$ sudo apt install openjdk-8-jdk

# 验证安装
$ java -version
openjdk version "1.8.0_212"
OpenJDK Runtime Environment (build 1.8.0_212-8u212-b01-1~deb9u1-b01)
OpenJDK 64-Bit Server VM (build 25.212-b01, mixed mode)
```

### 安装Maven

```bash
# 安装
$ sudo apt install maven

# 验证安装
$ mvn -v
Apache Maven 3.6.0
Maven home: /usr/share/maven
```

配置阿里云镜像：

```bash
# cd到maven安装目录
$ cd /usr/share/maven

# 备份 settings.xml 配置
$ sudo cp conf/settings.xml conf/settings_bak.xml

# 修改 settings.xml 配置，添加阿里云镜像
$ sudo vi conf/settings.xml
```

添加如下配置：

```xml
<mirror>
  <id>aliyunmaven</id>
  <mirrorOf>*</mirrorOf>
  <name>阿里云公共仓库</name>
  <url>https://maven.aliyun.com/repository/public</url>
</mirror>
```

### 安装Nodejs

```bash
# 下载nodejs
# 解压 node-v14.16.0-linux-x64.tar.xz
$ tar xvf node-v14.16.0-linux-x64.tar.xz

# 移动到目录
$ sudo mv node-v14.16.0-linux-x64/ /usr/local/nodejs

# 建立软链接
$ sudo ln -s /usr/local/nodejs/bin/node /usr/local/bin/
$ sudo ln -s /usr/local/nodejs/bin/npm /usr/local/bin/

# 验证安装
$ node -v
v14.16.0
$ npm -v
6.14.11
```

### 安装Python

```bash
# Deepin系统默认已安装了python2和python3，先验证安装
$ python -V
Python 2.7.16

$ python3 -V
Python 3.7.3

# 安装pip
$ sudo apt install python-pip -y
# 安装pip3
$ sudo apt install python3-pip -y

# 验证安装
$ pip3 -V
pip 18.1 from /usr/lib/python3/dist-packages/pip (python 3.7)
```

### 安装Jekyll

```bash
# 安装ruby
$ sudo apt install ruby-full ruby-bundler

# 验证ruby安装版本
$ ruby -v
ruby 2.7.0p0 (2019-12-25 revision 647ee6f091) [x86_64-linux-gnu]

# 验证gem安装版本
$ gem -v
3.1.2

# 配置国内gem source（https://rubygems.org太慢）
$ gem sources --add https://gems.ruby-china.com/ --remove https://rubygems.org/

# 验证gem source配置，确保只有 https://gems.ruby-china.com
$ gem sources -l
https://gems.ruby-china.com

# 安装jekyll
$ sudo gem install jekyll

# 验证jekyll安装版本
$ jekyll -v
jekyll 4.2.0
```

Deepin环境安装Jekyll可能遇到如下问题：

1. make：g++：命令未找到，提示如下：

    ```bash
    make "DESTDIR="
    compiling binder.cpp
    make：g++：命令未找到
    make: *** [Makefile:235：binder.o] 错误 127
    ```

    解决办法：先安装g++

    ```bash
    $ sudo apt install g++
    ```

本地构建Jekyll项目：

```bash
# 修改bundle镜像配置，这样就不用修改Gemfile中的source配置
$ bundle config mirror.https://rubygems.org https://gems.ruby-china.com

# 先使用bundle安装Gemfile配置中的插件
$ bundle install

# 启动项目
$ jekyll serve
```

## 开发工具安装和配置

### Typora

安装和修改主题：

```bash
# 下载gitbook主题：https://theme.typora.io/theme/Gitbook/
# 解压主题
$ unzip gitbook-v1-9-2.zip

# 将解压后的主题文件移 mv 到Typora的主题目录
$ mv gitbook/ gitbook-*.css ~/.config/Typora/themes
```

### VS Code

禁用单击预览文件：`Ctrl +,` -> 去掉勾选`Editor: Enable Preview`

### Intellij IDEA

配置JDK源码

## 问题及处理办法

1.从`apt remove`中恢复被删除的软件

```bash
# 新建 restore 脚本
$ echo '#!/bin/bash' > restore

# 从apt操作日志 /var/log/apt/history.log 文件中查找remove的软件，拼接install命令到 restore 脚本中
$ echo sudo apt install `grep Remove /var/log/apt/history.log | tail -1 | sed -e 's|Remove: ||g' -e 's|([^)]*)||g' -e 's|:[^ ]* ||g' -e 's|,||g'` >> restore

# 修改 restore 为可执行文件
$ chmod +x restore

# 执行 restore 脚本
$ ./restore
```
