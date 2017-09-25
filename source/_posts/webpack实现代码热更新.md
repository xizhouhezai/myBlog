---
title: webpack实现代码热更新
date: 2017-09-15 16:54:30
tags: 
categories: node.js
---

前端开发日异月新，怎么可以使我们更好或者更舒服的去做开发呢？我想作为前端开发者来说，肯定都会思考这个问题。在没有接触node.js前，我在做一些静态页面时，经常会来回的切换到浏览器刷新页面，来查看页面效果，这种感觉实在让人崩溃，但是在接触node.js后，发现了一些非常好用的工具，webpack就是其中之一，webpack的火爆，正因为他简单的配置，丰富的集成，使得gulp和grunt都在逐渐逊色，这里我将讲讲webpack实现代码的热更新和生成一个前端工程化项目。

<!--more-->

### 一.安装webpack

安装webpack的前提是需要node的npm包管理的支持，在这里我就不赘述node的安装了，大家可以自行去[node](http://nodejs.cn/)(<font color="#f00">戳这里去node中文网下载和查看帮助文档</font>)官网下载安装。

如果你已经安装好node，那么安装webpack将十分容易，任意地方，打开命令行工具，我们先进行全局安装，输入以下命令即可安装

```bash

$npm install -g webpack

```

<font color="#f00">
附：
如果安装失败，很可能因为是使用国外的资源，导致安装失败，在这里我们可以使用一个好用的切换镜像资源的工具nvm，同样他也需要使用npm安装
```bash

$npm install -g nvm

```
安装好nvm后，就可以任意切换镜像了，比如使用淘宝的镜像
```bash

$nvm use cnpm

```
切换成淘宝镜像后安装包依然使用npm install
</font>

### 二.初始化一个项目

初始化一个项目是搭建工程化前端项目的基础，他会创建一个重要的文件来描述项目的一些重要信息，这个文件是一个json文件，叫package.json,初始化项目要先建一个你即将要在里面工作的文件夹,然后切换到这个文件夹。在工作文件夹打开命令行工具，输入初始化命令

```bash

$npm init

```

回车后，会让填写一些信息，默认回车即可

这个时候工作目录，就会多出一个文件，package.json文件。package.json文件的作用我就不赘述了，大家可以参考朴灵的《深入浅出Node.js》一书，有详细描述。在此我们再新建一个存放入口文件的目录，比如我建了一个src文件夹。然后在src文件夹依次建一个index.html文件、一个index.js文件、一个index.css文件，建好后，我们即可安装局部webpack，及一些必要模块。


### 三.安装局部webpack和模块以及插件

局部安装webpack，只要输入以下命令

```bash

$npm install webpack --save-dev

```

安装完成后，继续安装必要的模块，第一个webpack-dev-server,这个模块主要为页面提供一个服务器和实现热更新主要模块，安装依旧简单

```bash

$npm install webpack-dev-server --save-dev

```

安装完webpack-dev-server后，继续安装html-webpack-plugin，这个插件是用来向入口文件index.html里插入js脚本的，这样就不需要在index.html里引入js，安装依然使用npm

```bash

$npm install html-webpack-plugin --save-dev

```

之后再安装css加载模块，style-loader和css-loader,安装

```bash

$npm install style-loader css-loader --save-dev

```

这样基本完成我们所需要的模块和插件了

### 四.完成webpack.config.js的配置

如何使整个项目运行起来，webpack.config.js起着至关重要的作用，webpack如何加载css，如何打包文件，都是查询这个文件后才会执行的，因此正确配置webpack.config.js非常重要，在工作目录新建一个文件webpack.config.js，如下
![webpack.config.js](http://orks6qu1s.bkt.clouddn.com/webpack.config.js.png)

#### 1.在文件头部引入必要模块

	let path = require('path'), //这个模块是node的自有模块，直接引用即可，它是用来解析路径的
    	HtmlWebpackPlugin = require('html-webpack-plugin');

#### 2.开始配置

	module.exports = {
	    entry: {
	        app: path.resolve(__dirname, 'src', 'index.js')
	    },
	    output: {
	        filename: '[name].js',
	        path: path.resolve(__dirname, 'dist')
	    },
	    plugins: [
	        new HtmlWebpackPlugin({
	            template: path.resolve(__dirname, 'src', 'index.html')
	        })
	    ],
	    module: {
	        rules: [
	            {
	                test: /\.css$/,
	                loader: ['style-loader', 'css-loader'],
	                include: path.resolve(__dirname, 'src')
	            }
	        ]
	    }
	};

这个是整个配置，我将逐个介绍他们的意义。

#### 3.各个配置的意义

##### 1.module.exports

module.exports就是提供一个向外的接口，所有的配置都挂载在module.exports上，供webpack去查询

##### 2.entry（入口文件）和output（出口文件）

entry是用来配置入口文件的，

	entry: {
	        app: path.resolve(__dirname, 'src', 'index.js')
	    }

这里app: path.resolve(__dirname, 'src', 'index.js')的意思是插入到入口文件index.html的js文件路径

	output: {
        filename: '[name].js',
        path: path.resolve(__dirname, 'dist')
    }

filename: '[name].js'这是出口文件的命名，即index.js,path: path.resolve(__dirname, 'dist')这是打包后静态资源所存放的目录文件，如果没有，webpack打包后自动创建

##### 3.plugins插件的配置

	plugins: [
	        new HtmlWebpackPlugin({
	            template: path.resolve(__dirname, 'src', 'index.html')
	        })
	    ]

plugins是一个数组，接受多个插件，HtmlWebpackPlugin在前面已经提到，它是将出口文件插入到入口文件index.html的插件，template: path.resolve(__dirname, 'src', 'index.html')即是将出口文件解析到入口文件的路径。

##### 4.module模块

	module: {
	        rules: [
	            {
	                test: /\.css$/,
	                loader: ['style-loader', 'css-loader'],
	                include: path.resolve(__dirname, 'src')
	            }
	        ]
	    }

模块是一个对象，可以接受多个属性，rules是用来配置js和css等文件的规则，test接受的是一个正则表达式，判断文件的类型，loader即是加载的模块的名称，接受的是一个数组，include是解析的文件所在的目录

完成配置后，我们就可以进行页面的简单编写了。

### 五.开始项目的编写

这里我们将直接使用js去渲染DOM，css完成样式。

打开index.html,写入基本元素即可。

	<!DOCTYPE html>
	<html lang="en">
	<head>
	    <meta charset="UTF-8">
	    <meta name="viewport" content="width=device-width, initial-scale=1.0">
	    <meta http-equiv="X-UA-Compatible" content="ie=edge">
	    <title>MyApp</title>
	</head>
	<body>
	    
	</body>
	</html>

之后编写index.js

	import './index.css'; //引入css文件

	var el = document.createElement('div'),
	    text = document.createTextNode( 
	        'Welcome to my app!'
	     );

	el.appendChild(text);
	el.id = 'app';
	document.body.appendChild(el);

最后编写index.css文件

	#app {
	    color: #f00;
	}

### 六.运行webpack-dev-server

在工作目录打开命令窗口，直接运行

```bash

$webpack-dev-server --port 3003

```

运行成功后，在浏览器里地址栏输入localhost:3003，查看效果，不出意外将会看到页面上的文字。

到此我们其实已经完成工程化项目的基本构造，那么如何让它进行热更新呢？其实很简单，只要把命令稍稍修改就行

```bash

$webpack-dev-server --inline --hot --port 3003

```

这时候重新加载页面，然后，在css文件里改改字体颜色，直接保存，你会发现，不需要刷新浏览器，也会立刻看到页面文字的颜色变了，这就实现了代码的热更新

<font color="#f00" font-size="16px">
	附：
		如何更加简单的使用命令，只要在起初我们创建的package.json里配置即可，package.json的内容
</font>

	{
	  "name": "my-app",
	  "version": "1.0.0",
	  "description": "构建一个舒适的前端开发环境",
	  "main": "index.js",
	  "scripts": {
	    "test": "echo \"Error: no test specified\" && exit 1"
	  },
	  "repository": {
	    "type": "git",
	    "url": "git+https://github.com/xizhouhezai/my-app.git"
	  },
	  "author": "",
	  "license": "ISC",
	  "bugs": {
	    "url": "https://github.com/xizhouhezai/my-app/issues"
	  },
	  "homepage": "https://github.com/xizhouhezai/my-app#readme",
	  "devDependencies": {
	    "babel-core": "^6.26.0",
	    "babel-loader": "^7.1.2",
	    "babel-preset-env": "^1.6.0",
	    "css-loader": "^0.28.7",
	    "html-webpack-plugin": "^2.30.1",
	    "node-sass": "^4.5.3",
	    "sass-loader": "^6.0.6",
	    "style-loader": "^0.18.2",
	    "webpack": "^3.5.5",
	    "webpack-dev-server": "^2.7.1"
	  },
	  "dependencies": {
	    "express": "^4.15.4"
	  }
	}


<font color="#f00" font-size="16px">
	我们只要在scripts加入
</font>

	"start": webpack-dev-server --inline --hot --port 3003

<font color="#f00" font-size="16px">
	最后我们只要运行
</font>

```bash

$npm run start

```

<font color="#f00" font-size="16px">
	这只是测试环境，如何上线，我们只要运行
</font>

```bash

$webpack

```

<font color="#f00" font-size="16px">
	这时候工作目录就会多出一个dist文件夹，我们只要把环境配置到dist，就可以运行项目了
</font>