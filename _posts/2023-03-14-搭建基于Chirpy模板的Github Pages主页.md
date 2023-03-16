---
title: 搭建基于Chirpy模板的Github Pages主页
date: 2023-03-14 18:53:00 +0800
categories: [编程, Github]
tags: [网站搭建, Github Pages]     # TAG names should always be lowercase
---

这篇帖子分享算是我搭建这个主页的过程中的一些经验，希望能帮助到一些也想用这个模板做主页特别是零基础的朋友们。

# 准备工作

在调用模板之前我们首先要在电脑上安装Git和Ruby，Git将用于模板的调用与上传，而由于Chirpy模板由Ruby编写，所以初始化的时候会用到Ruby命令行。

## 安装Git

打开[Git官网](https://git-scm.com/downloads)下载Git的安装包，按照指引完成安装（全部设置都选默认的就行）。运行`Git CMD`, 输入以下命令查看版本以确定是否安装成功：
```yaml
git --version
```

## 安装Ruby

打开[Ruby官网](https://rubyinstaller.org/downloads/)下载Ruby的安装包(选择Ruby+Devkit)，按照指引完成安装（全部设置都选默认的就行）。运行`Start Command Prompt with Ruby`, 输入以下命令查看版本以确定是否安装成功：
```yaml
ruby -v
```
然后输入以下命令安装jekyII和Bundler：
```yaml
gem install jekyll bundler
```
安装完可以输入以下命令查看版本：
```yaml
jekyII -v  
bundler -v
```
# 调用Chirpy模板

## 克隆到本地

## 初始化模板

# 发布主页

# 更新配置

# 插入valine评论


