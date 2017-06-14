---
title: HTML的标签
date: 2017-06-10 14:35:00
tags:
categories: html
---

HTML是如此的简单，相信大部分学过HTML的人都是这样觉得的，不得不说HTML的确没什么难的，只要几小时甚至几十分钟就能掌握，所以这篇文章我会着重讲一点HTML的学前知识。

<!--more-->

## 1.URL

url的中文翻译是统一资源定位器，通俗来讲，就是我们说的路径，路径又分为相对路径和绝对路径

#### 相对路径
从文件当前所在位置出发查找目标位置
 1、目标文件与当前文件在同一文件夹下，直接写文件名
 ``` bash
 	src="1.jpg"
 ```
 2、目标文件在子文件夹下，子文件夹名/文件名
 ``` bash
 	src="images/1.jpg"
 ```
 3、目标文件在当前文件的上一级目录，../文件名
 ``` bash
 	src="../1.jpg"
 ```
 4、目标文件在当前文件的上一级目录的子目录里  ../子目录名/文件名
 ``` bash
 	src="../images/1.jpg"
 ```

当目标文件是当前站点下的文件时，可使用相对路径。

#### 绝对路径 
``` bash
http://www.sohu.com/images/1.jpg
协议名   主机名     目录名 文件名
```
``` bash
ftp://202.112.111.12/images/1.jpg
协议名  主机IP地址   目录名 文件名
```
从最根本的协议开始完整的表述路径
无论在哪个文件里都能找到目标路径
当目标文件是其他主机上的文件时，必须使用绝对路径。

## 常见的图片格式

GIF  最多只支持256色。支持动画
JPG  支持真彩色
PNG  支持透明和半透明，支持真彩色

## HTML的头部声明

头部声明我们也叫<!DOCTYPE> 声明，在 HTML 4.01 中,<!DOCTYPE> 声明引用 DTD,因为 HTML 4.01 基于 SGML。DTD 是一套关于标记符的语法规则。它是XML1.0版规格得一部分,是html文件的验证机制,属于html文件组成的一部分。 DTD 规定了标记语言的规则，这样浏览器才能正确地呈现内容。

HTML5 不基于 SGML，所以不需要引用 DTD。

DTD：三种文档类型：S（Strict）、T（Transitional）、F（Frameset）。 
Strict：如果您需要干净的标记，免于表现层的混乱，请使用此类型。请与层叠样式表（CSS）配合使用 
``` bash
<!DOCTYPE HTML PUBLIC "-//W3C//DTD HTML 4.01//EN" "http://www.w3.org/TR/html4/strict.dtd">
```
Transitional：DTD 可包含 W3C 所期望移入样式表的呈现属性和元素。如果您的读者使用了不支持层叠样式表（CSS）的浏览器以至于您不得不使用 HTML 的呈现特性时使用 
``` bash
<!DOCTYPE HTML PUBLIC "-//W3C//DTD HTML 4.01 Transitional//EN" "http://www.w3.org/TR/html4/loose.dtd">
```
Frameset： DTD 应当被用于带有框架的文档。除 frameset 元素取代了 body 元素之外，Frameset DTD 等同于 Transitional DTD 
``` bash
<!DOCTYPE HTML PUBLIC "-//W3C//DTD HTML 4.01 Frameset//EN" "http://www.w3.org/TR/html4/frameset.dtd">
```

html5作为现在的主流方向，他的头部声明简单明了
``` bash
<!DOCTYPE HTML>
```
这就是HTML5的头部声明了

## HTML的结构

在HTML的结构中除却头部声明，他由一个html标签包裹，里面分为头标签head和主体标签body

``` bash
<!DOCTYPE HTML>
<html>
	<head>
		这是头部
	</head>
	<body>
		这是主体
	</body>
</html>
```

这些是每个HTML文件必须包含的元素

### head标签

head标签里的内容不会直接显示在页面的内容之中的，他主要是用来包裹用于声明页面性质和引用外部资源标签的父标签

附：父标签与子标签

当标签里面包裹着标签，我们就叫被包裹的标签为子标签，外层包裹的叫父标签，如
``` bash
<html>   // 父标签
	<head>   // 子标签
		这是head
	</head>
</html>
```