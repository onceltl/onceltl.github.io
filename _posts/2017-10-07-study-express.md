#原理

## 路由

定义：路由是指如何定义应用的端点（URIs）以及如何响应客户端的请求

使用方法

```javascript

var express = require('express');

var app = express();

// 没有挂载路径的中间件，应用的每个请求都会执行该中间件

app.use(function (arg) {});

// 挂载至 /user/:id 的中间件，任何指向 /user/:id 的请求都会执行它
app.use('/user/:id', function (arg) {});

// 路由和句柄函数(中间件系统)，处理指向 /user/:id 的 GET 请求
app.get('/user/:id', function (arg) {});
});

```
app.use是有顺序的，错误中间件需要最后定义

## 中间件

中间件（Middleware） 是一个函数，它可以访问请求对象（request object (req)）, 响应对象（response object (res)）, 和 web 应用中处于请求-响应循环流程中的中间件，一般被命名为 next 的变量.使用next会跳到下一个中间件，否则就不会继续传递。

### 路由级中间件

Router()和app用法类似， 实例是一个完整的中间件和路由系统，因此常称其为一个 “mini-app”，作用是模块化路由。

```javascript

	var router = express.Router();

```

### 错误中间件

如果向 next() 传入参数（除了 ‘route’ 字符串），Express 会认为当前请求有错误的输出
如果路由句柄有多个回调函数，可使用 ‘route’ 参数跳到下一个路由句柄。


##渲染引擎

使用一下代码就能改为html模板

```javascript

app.set('views', path.join(__dirname, 'views'));
app.engine("html", require("ejs").__express); // or   app.engine("html",require("ejs").renderFile);
//app.set("view engine","ejs");
app.set('view engine', 'html');

```

#使用

##Windows

1.官网下载msi安装node.js+npm

2.用npm install XXX安装包。如：npm install express安装express,安装的只会在当前的models里面，全局安装-g。npm install则可按照当前目录package.json文件安装所有包。

3.vs带有node.js插件NTVS,2017版之后可以直接使用vs自带的安装器安装。

4.命令行自动建立express项目：express -e express_test

5.express项目文件：

```
	
	bin是项目的启动文件，配置以什么方式启动项目，默认 npm start(www中是绑定端口和监听等)

	public是项目的静态文件，放置js css img等文件

	routes是项目的路由信息文件,控制地址路由(一般是js文件，模块化的路由中间件)

	views是视图文件，放置模板文件ejs或jade等（其实就相当于html形式文件啦~)

```

#MongoDB数据库

node.js中可以使用mongoose包驱动数据库。


##mongoose使用

	简要介绍见：http://www.cnblogs.com/winyh/p/6682039.html
	官方文档：http://www.nodeclass.com/api/mongoose.html






