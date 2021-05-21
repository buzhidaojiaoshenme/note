##### 1. 前端模块化

- 为什么要使用模块化

  早期做网页开发的时候，js只做简单的表单验证，代码量很少，直接将js代码写在script标签中就可以。

  随着ajax异步请求的出现，逐渐形成了前后端分离，前端代码量剧增，为了应对代码量剧增，通常会将js代码分别放在多个.js文件中，然后在html页面中通过多个script标签引入，但是这种方式依然不能避免一些灾难性问题，比如全局变量重名：

  1.aaa.js文件中，小明声明了变量

   var flag = true

  2.bbb.js文件中，小红声明了变量 

  var flag = false

  3.ccc.js文件中，小明想通过flag做一些判断

  if(flag) {

  ​	console.log('小明是天才')

  }

  小明后来发现自己的代码不能正常运行，去检查自己声明的变量，发现确实是true，最后悲剧了，小明加班到2点，还是没找到问题出在哪里

  当然，小明可以通过改变对.js文件的依赖顺序使自己的代码正常运行，但是当.js文件非常多的时候，弄清楚他们的顺序是一件很困难的事情

- 模块化有两个核心，导出和导入

- 模块化的实现方式

1. 匿名函数

   在aaa.js文件中，定义匿名函数，匿名函数内部定义一个对象，给对象添加各种需要暴露到外面的属性和方法，最后将这个对象返回，并且在外面使用一个ModuleA接收

   ```javascript
   //导出
   var MouduleA = (function() {
   	//1.定义一个对象
   	var obj = {}
   	//2.在对象内部添加变量和方法
   	obj.flag = true
   	obj.myFunc = function(info) {
   		console.log(info)
   	}
   	//3.将对象返回
   	return obj
   })()
   ```

   在ccc.js文件中，小明只需要使用属于自己模块的方法和变量就可以了

   ```javascript
   //导入
   if(ModuleA.flag) {
   	console.log('小明是天才')
   }
   ModuleA.myFunc('小明长的真帅')
   ```

2. CommonJS

    通过module.exports和require关键字

   ```javacript
   //导出
   module.exports = {
   	flag: true,
   	test(a, b) {
   		return a + b
   	},
   	demo(a, b) {
   		return a * b
   	}
   }
   ```

   ```javascript
   //导入
   let {test, demo, flag} = require('moduleA')
   //等同于
   let ma = require('moduleA')
   let test = ma.test
   let demo = ma.demo
   let flag = ma.flag
   ```

   

3. ES6

   通过export和import关键字

```

```

