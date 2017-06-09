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

## 安装前提

``` bash
git
node.js
```

如果您的电脑中已经安装上述必备程序，那么恭喜您！接下来只需要使用 npm 即可完成 Hexo 的安装。

``` bash
$ npm install -g hexo-cli
```

如果您的电脑中尚未安装所需要的程序，请根据以下安装指示完成安装。

## 安装git

``` bash
安装 git.
```

下载[git](https://git-scm.com/download/win)请戳这里

## 安装node.js

``` bash
安装 node.js.
```

下载[node.js](https://nodejs.org/en/)请戳这里


安装好git和node.js，就可以继续安装hexo了（安装node.js是安装hexo所必须的，只有使用node.js的包管理工具npm，才能安装hexo）

``` bash
$ npm install -g hexo-cli
```