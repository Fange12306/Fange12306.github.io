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
```console
git --version
```

## 安装Ruby

打开[Ruby官网](https://rubyinstaller.org/downloads/)下载Ruby的安装包（选择Ruby+Devkit），按照指引完成安装（全部设置都选默认的就行）。运行`Start Command Prompt with Ruby`, 输入以下命令查看版本以确定是否安装成功：
```console
ruby -v
```
然后输入以下命令安装jekyII和Bundler：
```console
gem install jekyll bundler
```
安装完可以输入以下命令查看版本：
```console
jekyII -v  
bundler -v
```
# 调用Chirpy模板

官方给出的调用Chirpy模板有两种方式，一种是使用Chirpy Starter直接作为新模板编辑，这种方式比较简单，但是许多功能被阉割了，所以我采用了第二种方式：在Github上fork模板。

## 克隆到本地

在Github打开[模板的网址](https://github.com/cotes2020/jekyll-theme-chirpy)，
点击右上角的fork，然后把`Repository name`改成`Github用户名.github.io`，这是个人主页强制要求的，之后确定fork。随后运行`Git CMD`，输入以下命令：
```console
git clone https://github/Github用户名.github.io #地址为你fork的地址
```
这样就把模板克隆到本地了，地址一般在C://User/Administrator下。

## 初始化模板

运行`Start Command Prompt with Ruby`，输入以下命令将路径转至模板下：
```console
cd C://User/Administrator #地址为模板的本地路径
```
随后输入以下命令为模板安装缺失的bundle:
```console
bundle
```
然后输入以下命令初始化模板：
```console
bash tools/init
```
这是比较重要的一步，根据官方的说法，这个初始化主要是删除了一些文件，如果不执行这一步，发布网页的时候网页会显示异常。

# 发布主页

# 更新配置

# 插入valine评论


