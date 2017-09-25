---
title: hexo的搭建
date: 2017-06-09 09:28:50
tags:
comments: true
categories: Hexo
---

在这里我将简单的介绍什么是hexo和安装hexo,详细的教程请阅读hexo的[官方网站](https://hexo.io/zh-cn/)和[文档](https://hexo.io/zh-cn/docs/)
(本文仅适合Windows平台)
<!--more-->

## 什么是Hexo

Hexo 是一个简单地、轻量地、基于Node.js的一个静态博客框架，可以方便的生成静态网页托管在github和Heroku上，引用Hexo作者 @tommy351 的话：

快速、简单且功能强大的 Node.js 博客框架。A fast, simple & powerful blog framework, powered by Node.js.

## GitHub Pages是什么？

GitHub Pages 可以被认为是用户编写的、托管在github上的静态网页。由于它的空间免费稳定， 可以用于介绍托管在[github](https://github.com)上的Project或者搭建网站。有两种形式: Project Site 和 User/Org Site，二者之间的差异可以戳 [GitHub Pages](https://pages.github.com/) 。基于 GP 创建Site是很方便的，这有一个简单的教程： 学习 [Github Page](https://pages.github.com/) 教你分分钟搭建自己的博客

gp 生成的网站的默认域名是 username.github.io 或者 username.github.io/project-name ，但gp是支持自定义域名的： Custom Domain Name 。购买域名之后，可以和默认的二级域名进行绑定，购买域名和设置DNS请自行百度

更多关于gp的信息，可以戳： [Github Pages Help](https://help.github.com/categories/github-pages-basics/)

## 安装

### 安装前提

``` bash
git
node.js
```

如果您的电脑中已经安装上述必备程序，那么恭喜您！接下来只需要使用 npm 即可完成 Hexo 的安装。
在本地任何一个目录下Ctrl+shift+鼠标右击，选择命令提示符，输入以下命令即可

``` bash
$ npm install -g hexo-cli
```

如果您的电脑中尚未安装所需要的程序，请根据以下安装指示完成安装。

#### 安装git

``` bash
安装 git.
```

下载[git](https://git-scm.com/download/win)请戳这里

#### 安装node.js

``` bash
安装 node.js.
```

下载[node.js](https://nodejs.org/en/)请戳这里


安装好git和node.js，就可以继续安装hexo了（安装node.js是安装hexo所必须的，只有使用node.js的包管理工具npm，才能安装hexo）

``` bash
$ node -v(查看node版本)
$ npm -v(查看npm版本)
$ npm install -g hexo-cli(安装hexo的命令工具)
```

### 初始化hexo
安装好hexo-cli后，就可以初始化hexo了，初始化实际上就是建立一个hexo项目文件夹，所以可以在本地选择一个任意地方，新建一个新的博客文件夹，进入该文件夹，Ctrl+shift+鼠标右击打开命令提示符，输入以下命令
``` bash
$ hexo init
```
当hexo init 按enter键后，出现要填的一些配置，选择默认的配置即可，初始化后会出现一个文件目录，如下

![hexo文件目录](http://orks6qu1s.bkt.clouddn.com/files.png)

这个时候再执行如下命令
``` bash
$ npm install
```
安装hexo依赖的工具

至此你的hexo已经安装完成，如何使用呢？

当你完成安装hexo时，说明已经可以在本地测试你的hexo，只要在博客目录打开命令提示窗，运行以下命令

``` bash
$ hexo server(or hexo s)
```
![hexo server](http://orks6qu1s.bkt.clouddn.com/hexo-server.png)

这样启动hexo的服务，然后在浏览器地址框输入

``` bash
localhost:4000
主机名    端口号
```
这是hexo默认的端口号，端口号可以在hexo的配置文件中修改，当浏览器出现hexo的欢迎页面，说明安装成功

### 新建第一个hexo页面

``` bash
$ hexo new 文件名
```

这样就会在博客目录的source/_post/新建一个.md结尾的文件，用编辑器打开，如下图

![new page](http://orks6qu1s.bkt.clouddn.com/newpage.png)

只要在后面编写，就可以开始你的博客之旅了

### 上传文件到服务器

这只是在本地运行，那么要怎样才能让互联网上的所有人看到呢？

在开始我已经介绍了github这样的免费服务器，它能够支持我们的博客，提供免费的服务，如果你已经在你的github里生成这样的项目，username.github.io的项目，那么就可以将你本地写好的博客上传到这个项目来即可，现在只要在浏览器输入username.github.io就可以访问你的博客了。如果你还没有生成，接下来我将继续提供简单教程，怎么生成github page。

#### 生成github page

首先你要注册一个github账号，[注册地址](https://github.com/)

注册账号后，登录github，这是一个英文网站，英文基础不好的同学不要怕，你们不需要操作很多东西，只要按照方法一步步来，是很简单的，因为我的英语水平也不咋地，可以说很烂

第一步：新建一个仓库，new repository

![new repository](http://orks6qu1s.bkt.clouddn.com/newRepository.png)

第二步：填写仓库的信息

![create repository](http://orks6qu1s.bkt.clouddn.com/createR.png)

第三步：创建完仓库，为github page设置一个默认主题，查看效果，以实验是否生成页面

![create repository](http://orks6qu1s.bkt.clouddn.com/setting.png)
![create repository](http://orks6qu1s.bkt.clouddn.com/theme.png)
![create repository](http://orks6qu1s.bkt.clouddn.com/selectTheme.png)

第四步：在浏览器地址栏输入username.github.io，这时出现你刚才选择的主题欢迎页面，说明已经成功，这时候可以clone下项目，删除里面生成的主题文件，以防止把hexo生成的静态文件传入时覆盖

#### 将hexo生成的静态文件上传至服务器

在完成github page搭建后，我们只要把hexo生成的静态文件上传到github即可，那么怎么生成静态文件和上传呢？这里我们要先了解hexo的配置文件_config.yml。这个文件是用来改变hexo主页的一些属性的，比如作者，博客描述等。如下图：
![config](http://orks6qu1s.bkt.clouddn.com/config.png)

它的路径在你创建的项目的根目录下，用编辑器打开就能进行编辑。

1.生成静态文件

生成静态文件很简单，只要在项目的根目录下打开命令窗口，运行hexo deploy即可

``` bash
$ hexo generate(or hexo g)
```

2.配置_config.yml

打开_config.yml，只要在尾部加上

``` bash
deploy:
  type: git
  repo: https://github.com/yourgithub/yourgithub.github.io.git(你的github项目地址)
  branch: master
```

![deploy](http://orks6qu1s.bkt.clouddn.com/deploy.png)

保存好后，在命令窗口执行hexo deploy


``` bash
$ hexo deploy(or hexo d)
```
执行hexo d过程中会让你输入github的密码，输入密码回车即可，如果上传成功的话，会在github项目里看到如下目录
![deploysuccess](http://orks6qu1s.bkt.clouddn.com/deploysuccess.png)

<font color=#0099ff size=4 face="黑体">最后的最后，只要在浏览器里输入yourgithubname.github.io查看效果即可</font>