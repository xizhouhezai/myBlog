---
title: css前传
date: 2017-06-20 15:53:32
tags:
categories: css
---

css是什么？为什么会出现css？它有什么神奇之处？
初学者肯定都会有这几个疑问，这篇文章我会一一介绍，顺便解决在HTML中留下的几个坑。

<!--more-->

## css是什么？

在HTML中我介绍过用HTML的属性为HTML增加一些让我们在网页中可见的一些外观，比如长高，背景色等等，但是当我们使用了大量的属性的时候，会发现标签变得臃肿，且不易维护，代码中内容和属性杂糅，无法阅读，使用大量属性又无法重用，比如两个p，都是一样的背景色，却要连续使用两次属性去设置同样的值，而在实际项目中，都会要求代码可读性强，易维护，可重用，这时候css自然的应运而生，css可以把HTML表现的样式分开，而HTML只关注内容，从而使得代码更加简洁明了，易维护，可重用。

CSS全称Cascading Style Sheet，翻译过来就是层叠样式表，又称级联样式表，简称样式表。

### css的特点

1、实现内容与表现相分离
2、提高了代码的可重用性和可维护性

### HTML属性 与 CSS 样式的使用原则:
1、W3C 建议尽量使用 CSS样式取代HTML属性
2、HTML中的专有属性，无法通过CSS取代的只能选择html属性，如 rowspan、colspan

## 如何使用CSS

既然已经知道了CSS的好处，那么如何在HTML中使用CSS呢？

### 1、内联方式
     别名：行内样式、内联样式
	 特点：将样式属性定义在html标签中
	 语法：
	    将样式定义在标签的 style 属性中<div style=""></div>
	    style属性值 ： 是以 ; 隔开的多个 属性/值 对的内容
	    属性 与 值 之间 通过  :  连接
	    <div style="属性:值;属性:值;"></div>

	    常用的属性和值:
	    属性            值
	    color           颜色英文名称
	    font-size       以 px/pt 作为单位的数字
	    background-color 颜色英文名称
``` bash
<p style="background-color:red;font-size:16px">
	这里是一段文本
</p>
```
### 2、内部样式表
         特点：将 "样式规则" 放在 <style>的元素内
	     1、在 <head>中添加<style>元素
	     2、在 <style> 中增加若干样式规则

	 样式规则:
	    1、选择器 : 规范页面中哪些元素能够使用定义好的样式（在这里我不会解释选择器，大家只要按
	    着这样定义即可，我会在css选择器着重讲解css选择器）
	    2、样式声明 : 到底元素长的什么样

	    选择器{
		样式声明;
		样式声明;

		color:red;
		font-size:18px;
		background-color:green;
	    }
``` bash
<head>
    	.
    	.
    	.
	<style>
	    p {
			color:red;
			font-size:18px;
			background-color:green;
		}
	</style>
</head>
<body>
	<p>这里是一段文本</p>
</body>
```
### 3、外部样式表
          特点：
	    1、将样式定义在 一个外部的 CSS文件中(以 .css 作为后缀名称的文本文件)
	    2、在 css 文件中 添加若干 样式规则
	    3、在任何html网页中 引入 独立的 css 文件
	       在 head 中 增加以下标记 对外部样式表进行引入
	       <link rel="stylesheet" type="text/css" href="css文件地址">


