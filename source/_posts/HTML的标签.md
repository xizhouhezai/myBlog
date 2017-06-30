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

## HTML文件

HTML文件就是以.html、.htm、.xhtml等结尾的文件，用来编写HTML代码的

#### 如何在HTML文件中编写代码和运行HTML文件

编写HTML代码没有那么多纷繁复杂的配置和安装软件，在windows系统中只需要用自带的文本编辑器即能完成HTML代码的编写，也不需要编译，可以直接在浏览器中运行

用文本编辑器打开HTML文件，右击 --> 打开方式 --> 选择记事本，即可在记事本开始编写HTML文件

编写完HTML代码并保存后在浏览器中运行，同样右击 --> 打开方式 --> 选择浏览器，即可在浏览器中查看到效果

附：当然，在实际工作中很少会直接使用系统自带的编辑器编写，初学者我推荐使用的编辑器可以是EditPlus，sublime text等编辑器

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

## HTML标签的属性和属性值

HTML标签的属性是用来描述标签的一些特性的，前一篇文章我们介绍到，标签就像一个个盒子，那么这些盒子必定会有不同的作用和形态以及材料，比如装水的瓶，它可以是玻璃的材料，长圆柱形；装饼干的盒子，它可以是铁的，长四方体。HTML的标签也是如此，不过它是用属性来描述这些特性，用属性值表现这些特性，比如一个标签它有长高，那么就用width描述长，height描述高，接受属性值表现特性，也可以为其加入边框或者背景颜色，如下
``` bash
<p width="100px" height="100px" background="red">
	这是文本标签
</p>
```
说明这个文本标签在页面中占有100px的长和100px的高

附：px是像素点单位，网页中常用的长度单位，除此之外还有cm，rem等

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

#### head里常见的声明和外部资源引用标签

##### 1.meta标签

meta标签的作用有：搜索引擎优化（SEO），定义页面使用语言，自动刷新并指向新的页面，实现网页转换时的动态效果，控制页面缓冲，网页定级评价，控制网页显示的窗口等！meta可以接受各种属性值，以确定网页在浏览器中的一些性质，这里我只说一个必不可少的，就是编码的声明，这个是确定页面能否在浏览器中解析正确，如果设置了不正确的编码格式，页面将会乱码（关于编码，可以百度HTML的编码格式，了解更多）

``` bash
<html>
	<head>
		<meta charset="UTF-8">
	</head>
	<body>
		这是主体
	</body>
</html>
```
charset就是设置编码的格式的属性，UTF-8是通用的编码格式，中文编码格式为GBK

##### 2.title标签

title标签是用来设置页面在浏览器标签栏中的标题的

``` bash
<html>
	<head>
		<meta charset="UTF-8">
		<title>这是标题</title>
	</head>
	<body>
		这是主体
	</body>
</html>
```
![title](http://orks6qu1s.bkt.clouddn.com/title.png)

##### 3.引用外部资源的标签

1.link标签
引用样式标签，这里我不会讲解样式标签的作用，这将会在css时着重讲解
``` bash
<link rel="stylesheet" href="样式文件所在目录的路径">
```
2.script标签
引用脚本文件，这将会在JavaScript中着重讲解
``` bash
<script src="脚本文件所在目录的路径"></script>
```

## 主体body标签中的内容

body标签里的内容将是呈现在页面中用户看到的实际内容

#### 图像img标签

  必备属性：
  src 定义图像的url

  可选属性：
  width  宽
  height 高
  alt  替代文字（多数情况下用title可替代alt，如果图片加载失败，显示在网页上的文字）
``` bash
<img src="路径" alt="替代文字">
```
#### 链接a标签
  必备属性：
  href  链接的目标路径

  可选属性：
  name  命名。命名后的a称之为锚点，可以作为链接目标
  target  指定链接在什么样的窗口中打开
      _self  默认。当前窗口
	  _blank  在新建的窗口中打开链接
  （title、id、class）
``` bash
<a href="www.baidu.com" target="_self">这是一个链接</a>
```

  锚点链接：这是一个特殊的链接方式，可跳到本页面中一个特定位置，这个指向是一个标签属性中的命名锚记或是id。
```bash
<a href="#name">点击跳转</a>

<p id="name">这是要跳转到地方</p>
```

  邮件链接：可以创建一个点击后发送邮件的链接
```bash 
    <a href="mailto:senica@126.com?subject=邮件标题&cc=xxx@126.com&mcc=yyy@126.com">发邮件</a>
```
####  Table标签
table是 HTML里的布局工具，前期可用于简单布局
```bash 
  <table>
    <tr>
      <td>编号</td>
      <td>姓名</td>
    </tr>
    <tr>
    	<td>1</td>
    	<td>Tom</td>
    </tr>
    <tr>
    	<td>1</td>
    	<td>Lucy</td>
    </tr>
  </table>
```
![table](http://orks6qu1s.bkt.clouddn.com/table.png)

table的组成由外层的table和横行tr，纵行td组成，
  table的属性  width、height、border、bordercolor、bgcolor
         background、cellspacing、cellpadding、align

  tr的属性  height  align  vlign
  td的属性  width height align vlign colspan  rowspan 

  table的可选标签：
  caption  表格标题
  ``` bash
	<table>
		<caption>这是表格标题</caption>
	</table>
  ```
  thead  表格头部
  ``` bash
	<table>
		<thead>
			<tr>
				<td>这是表头</td>
			</tr>
		</thead>
	</table>
  ```
  tbody  表格主体
  ``` bash
	<table>
		<thead>
			<tr>
				<td>这是表头</td>
			</tr>
		</thead>
		<tbody>
			<tr>
				<td>这是表的主体</td>
			</tr>
		</tbody>
	</table>
  ```
  tfoot  表格尾部
  ``` bash
	<table>
		<thead>
			<tr>
				<td>这是表头</td>
			</tr>
		</thead>
		<tbody>
			<tr>
				<td>这是表的主体</td>
			</tr>
		</tbody>
		<tfoot>
			<tr>
				<td>这是表尾</td>
			</tr>
		</tfoot>
	</table>
  ```
#### 文本标签

文本标签除了p标签外，还有span、i、b等标签

#### <font color=#0099ff size=4 face="黑体">行内元素与块级元素</font>
<font color=#0099ff size=3 face="黑体">
	在这里，我将着重讲解一下行内元素与块级元素，这将有助于我们更好的理解HTML元素
</font>
<font color=#97CC89 size=3 face="黑体">
	什么是行内元素和块级元素？
	行内元素，顾名思义，就是多个元素能排在一行，当大于一行的长度，才会挤向下一行，就像一个大盒子，里面可以放小盒子，这个小盒子就是行内元素
	块级元素，自然就是那个大盒子，它是独占一行的元素，块级元素可以包裹行内元素，也可以包裹块级元素，但是行内元素不可以包裹块级元素
	常见的块级元素：p、div、h1等
	常见的行内元素：span、i、b等
</font>


<font color=#0099ff size=5 face="黑体">
	一篇文章对于HTML标签的分享是有限的，更多的标签使用可以查看w3cSchool的html在线文档，[在线文档地址](https://www.w3cschool.cn/html/)
</font>    