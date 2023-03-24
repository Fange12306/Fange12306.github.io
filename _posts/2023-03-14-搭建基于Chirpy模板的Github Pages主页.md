---
title: 搭建基于Chirpy模板的GitHub Pages主页
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

官方给出的调用Chirpy模板有两种方式，一种是使用Chirpy Starter直接作为新模板编辑，这种方式比较简单，但是许多功能被阉割了，所以我采用了第二种方式：在GitHub上fork模板到仓库。

## 克隆到本地

在GitHub打开[模板的网址](https://github.com/cotes2020/jekyll-theme-chirpy)，
点击右上角的fork，然后把`Repository name`改成`GitHub用户名.github.io`，这是个人主页强制要求的，也将作为之后发布的主页的域名，之后确定fork。随后运行`Git CMD`，输入以下命令：
```console
git clone https://github/GitHub用户名.github.io  #地址为你fork后的仓库的地址
```
这样就把模板克隆到本地了，地址一般在C://User/Administrator下。

## 初始化模板

运行`Start Command Prompt with Ruby`，输入以下命令将路径转至模板下：
```console
cd C://User/Administrator/xxx  #地址为模板的本地路径
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

在上传发布之前我们首先，我们首先打开本地模板根目录下的`config.yml`，补全其中的
```console
url = 'https://GitHub用户名.github.io'  #地址即填写为主页的域名
```
然后我们要把初始化好的模板传上GitHub仓库覆盖掉原来的模板。运行`Git CMD`，输入以下命令将路径转至模板下：
```console
cd C://User/Administrator/xxx  #地址为模板的本地路径
```
然后按顺序输入以下四步命令：
```console
git add .  #将本地文件存到暂存区  
git commit -m “excu”  #将暂存区文件提交到本地仓库  
git remote add origin https://github/GitHub用户名.github.io  #将本地仓库关联到GitHub仓库  
git push -u origin master  #本地仓库上传到GitHub仓库（可能会要求输入用户名和密码）
```
这样我们就把初始化完成的模板上传完成了。之后打开GitHub仓库网址，点击上访工具栏最右边的`Settings`，之后点击左侧菜单列的`Pages`，在`Build and Development`中将`Source`选项选择`GitHub Actions`。
这意味着可以通过文件的修改来触发主页的发布，之后一般等一段时间就可以在`Pages`页面右上角看到主页已发布的信息。

# 更新配置

之后主页的各种更新也可以直接更改本地文件，然后上传至GitHub仓库，步骤同上，只不过不用重复将本地仓库关联到GitHub仓库。全局配置的更改可以通过更改根目录下的`_config.yml`文件来实现，下面列出一些可供自定义的配置:
```console
lang: zh-CN  #系统语言，格式对应根目录下的`_data/locales`。  
   
title: Fange  #主标题  
tagline: 一个简单的个人主页  #主标题的简单介绍  
  
github:    
  username: fange12306  #左下角GitHub标志对应的跳转页面       
twitter:  
  username: fange12123  #左下角Twitter标志对应的跳转页面    
  
social:
  name: Yufan Wang  #网页中间最下面的保留权利人姓名  
  email: 11910902@mail.sustech.edu.cn  #左下角Email标志对应的跳转页面  
  links:  
    # 点击前面姓名跳转的页面，-为开启，#为关闭，若开启多个，展示最前面的一个  
    # https://twitter.com/username      
    - https://github.com/fange12306      
    # https://www.facebook.com/username  
    # https://www.linkedin.com/in/username   
  
theme_mode:  #色调模式，有黑和白两种，若不填写左下角会有切换按钮  
  
avatar: '/assets/img/avatar.png'  #左上角头像  
  
  
```
{: file="_config.yml" }

# 插入valine评论

Chirpy模板自带有disqus评论系统，但是由于disqus无法支持匿名评论，且需要挂梯子，所以我选择了valine评论。首先打开[LeanCloud](https://console-e1.leancloud.cn/)，这里选择华东和华北区都行，但是不要选择国际版，
因为国际版的评论链接已经不可用了。点击右上角`Console`注册账号，登陆后选择`创建应用`，并选择开发版，创建好了点进应用`设置`里的`应用凭证`，查看`AppID`、`AppKey`以及`REST API 服务器地址`。编辑位于模板根目录的`_config.yml`，键入以下字段：
```console
valine:
  enable: true  #是否启用valine
  leancloud_appid: xxxxxxxxxxxxx  #LeanCloud应用的AppID
  leancloud_appkey: xxxxxxxxxxxxx  #LeanCloud应用的AppKey
  placeholder: "点击发表一条评论："  #评论区的占位文本
  avatar: mp  #评论用户的头像
  serverURLs: 'https://xxxxxxxxxxxx'  #LeanCloud应用的REST API 服务器地址
```
{: file="_config.yml" }

之后在根目录`_includes`文件夹下创建文件`valine.html`，键入以下字段（复制粘贴后删除`\{\%}`的`\`）：

```console
\{\% if site.valine.enable %}
<div id="comments"></div>
<script src="//cdn1.lncld.net/static/js/3.0.4/av-min.js"></script>
<script src='//unpkg.com/valine/dist/Valine.min.js'></script>
<script>
  new Valine({
    el: '#comments',
    app_id: '{{ site.valine.leancloud_appid }}',
    app_key: '{{ site.valine.leancloud_appkey }}',
    placeholder: '{{ site.valine.placeholder }}',
    avatar: '{{ site.valine.avatar }}',
    serverURLs: '{{ site.valine.serverURLs }}',
    visitor: true
  });
</script>
\{\% endif %}
```
{: file="_includes/valine.html" }

之后在根目录`_layouts`文件夹下打开文件`page.html`，键入以下字段（复制粘贴后删除`\{\%}`的`\`）：

```console
\{\% if site.valine_comment.enable and page.comments %}
<div class="row">
  <div class="col-12 col-lg-11 col-xl-8">
    <div class="pl-1 pr-1 pl-sm-2 pr-sm-2 pl-md-4 pr-md-4">
      \{\% include valine.html %}
    </div> <!-- .pl-1 pr-1 -->
  </div> <!-- .col-12 -->
</div> <!-- .row -->
\{\% endif %}
```
{: file="_layouts/page.html" }
上传更新后主页就可以在帖子下使用评论功能了。




