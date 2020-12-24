#### 0.commonjs

- 引入模块:`require('第三方模块名/自定义模块路径')`

- 导出模块：

  1.`module.exports={key:value}/module.exports.key=value`

  2.`module.exports=value`

  3.`exports={key:value}/exports.key=value`

- node被一个默认函数包裹，这个函数提供了两个重要的属性

  1.`_filename`:返回当前文件的绝对路径

  2.`_dirname`:返回当前文件所处的文件夹(目录)的绝对路径

#### 1.导出/引入方式：

- 1.module.exports =value 导出一个

  ​								={key:value}导出多个

- 2.module.exports.xxx=value 给导出对象扩展属性,可以多次

- 3.exports ={key:value} 或exports.xxx=value node提供的对象，可以添加多次。

- 引入：require('包名/自定义包的路径')

#### 2.node环境下运行js代码

- node环境下的js代码会被一个默认函数包裹。
- 这个函数中提供了一些默认参数供我们使用：
  - 1.exports：用于导出模块
  - 2.require：用于引入模块
  - 3.module：用于导出模块内容
  - 4.__filename：可获取当前文件的绝对路径
  - 5.__dirname: 可获取当前文件夹的绝对路径

- nodejs外层函数的作用：
  - 1.让我们能够直接使用commonJS语法，不支持commonJS语法是不能进行导出导入操作的。
  - 2.隐藏内部实现（独立作用域）
  - 3.处于安全考虑

- 在函数内部执行，用于查看当前函数的方法：

  `arguments.callee.toString()`

  在node全局中，使用这个方法，可以发现被一个匿名函数包裹着，（anonymous-无名）

#### 3.node中的全局对象—global

- JS的组成部分（浏览器中）：
  - 1.DOM
  - 2.BOM
  - 3.ECMAScript
- JS的组成部分（nodejs中）
  - 1.global
  - 2.ECMAScript

- global中的所有属性和方法都可以直接使用：

  ```js
  // 设置立即执行函数
    setImmediate(()=>{
        console.log("Immediate```");
   })
  // 设置计时器
    setTimeout(()=>{
        console.log("timeout~~~");
    });
  。。。
  ```

#### 4.node中的事件轮询（6个阶段）

- 一阶段：timers：设置计时器，执行定时器的回调函数

- 二阶段：pending callbacks ：系统阶段(忽略)
- 三阶段：idle,prepare(准备阶段)
- 四阶段：poll(轮询阶段)：
  - 1.如果回调队列不为空(有回调函数)，则从队列中一个一个执行回调函数，知道队列为空或达到系统最大限度
  - 2.如果回调队列为空(没有回调)，再判断是否设置了setImmdeiate(立即执行函数),如果有则进入下一个阶段(check)，去执行setImmdeiate的回调函数
  - 3.如果回调队列为空，并且每有设置立即执行函数，则在此阶段等待，等待有回调函数进入轮询队列，计时器到点了，进入check阶段，执行定时器回调函数
- 五阶段：check(执行setImmdeiate回调阶段)
- 六阶段：close callbacks(关闭回调阶段)：清除计时器

#### 5.npm—node包管理工具

- `npm（node package manage）`是一个包管理工具，对于开发者来说，可以更方便的下载包、库之类的，而不需要去搜索官网下载。
- npm的基本结构就是必须要有一个`package.json`的配置文件，这个文件中记录了当前包的信息，和依赖项。我们可以自己创建，也可以通过npm指令自动创建。
- 电脑中下载好node之后就可以使用node的基本操作指令了：
  - 1.`npm init` 填入信息创建package.json创建包管理工具
  - 2.`npm init -y`使用默认值创建package.json创建包
  - 3.`npm i`下载package.json中所有依赖包(最新版本)
  - 4.`npm i 包名[@x.x.x]`下载指定包名[可指定版本号,默认最新版]
  - 5.`npm remove 包名`删除指定包
  - 6.`npm i 包名 -g`将包下载到全局(一般工具包)
  - 7.`npm i 包名 -D`将包下载到开发环境下
  - 8.`npm i 包名 `默认下载到生成环境

#### 6.nodejs的文件系统(file system)

- nodejs中给提供了一个文件系统模块(js)，它是内置的核心模块，直接引入就可以使用，可以通过js对本地文件进行增删改查。

- 使用：引入fs：const fs=require('fs')

- fs中的方法：

  - 1.`writeFile(filePath,data[,options],callback)`简单写入文件

  - 2.`readFile(path[,options],callback)`简单读取文件

  - 3.`createWriteStream(path[,options])`创建写入文件流

    - 写入流(ws)的方法:

      1.`ws.on('open',callbak)`监听文件流启动

      2.`ws.on('close',callbak)`监听文件流关闭

      3.`ws.write(data)`写入数据

      4.`ws.end()`关闭文件流（手动关闭节约内存）

  - 4.`createReadStream(path[,options])`创建文件读取流

    - 读取流(rs)的方法:

      1.`rs.on('open',callback)`监听读取流开启

      2.`rs.on('close',callback)`监听读取流关闭(自动关闭)

      3.`rs.on('data',data=>{})`获取读取的数据（data）

#### 7.nodeJS中的path模块

- 内置核心模块，直接引入使用`const path=require('path')`
- 使用：
  - 1.拼接路径:`path.join(__dirname,'abc.txt')`
  - 2.拼接路径有奇效:`path.join(__dirname,'../abc.txt')`

#### 8.数据库的认识

- 数据库：就是一个存储数据的仓库

- 数据库分类：

  - 1.关系型数据库

    - 数据结构：数据库==>表==>数段

    - 例如：MySQL、Oracle、SQL Server

    - 特点：关系紧密,表格存储数据

    - 有点：表格结构，格式一致，便于维护，SQL语句通用

    - 缺点：海量数据读写比较差，固定结构，字段不可随意更

      ​			改，SQL语句高级查询时复杂，学习成本高

  - 2.非关系型数据库

    - 数据结构：数据库==>集合==>文档
    - 例如：MongoDB
    - 特点：关系不紧密，集合存储，有文档、键值对
    - 有点：格式灵活、速度快、不需要学习sql
    - 缺点：不支持SQL语句，不支持事务

#### 9.域名、端口号相关

- ip地址:网络中计算机的位移标识符,一串数字(例:192.0.0.1)，代表着网络中的地址。
- 域名:为了让网址好记，代替ip地址的标识符(例:www.xxx.com)
- localhos代表计算机的本地ip(127.0.0.1)
- 端口号：计算机中启动起来的应用程序的唯一标识符。每个程序不能发生冲突，冲突了会提示端口号被占用，不能运行。
- 端口号公有1—65535个端口号可以选择，不建议使用1—199的端口号,这些是预留给系统使用的，一般使用4为数的，但不能以1开头

- 常见端口号：
  - 21端口：FTP 文件传输服务
        22端口：SSH 端口
        23端口：TELNET 终端仿真服务
        25端口：SMTP 简单邮件传输服务
        53端口：DNS 域名解析服务
        80端口：HTTP 超文本传输服务
        110端口：POP3 “邮局协议版本3”使用的端口
        443端口：HTTPS 加密的超文本传输服务
        1521端口：Oracle数据库服务
        3306端口：MYSQL 默认端口号
        5000端口：MS SQL Server使用的端口
        27017端口：MongoDB实例默认端口

#### 10.连接mongoDB数据库

- 使用：

  - 1.初始化包管理器 `npm init -y`

  - 2.下载mongoose包`npm i mongoose`

  - 3.引入mongoose包`const mongoose=require('mongoose')`

  - 4.连接数据库

    ```js
    //连接（mongodb协议:本机地址:mongodb端口号/数据库名称）
    mongoose.connect('mongodb://127.0.0.1:27017/DBname',{
        //新版本提示我们配置项
        useNewUrlParser:true,//分析url地址
        useUnifiedTopology:true//统一结构
    })
    ```

  - 5.监听数据库连接状态

    ```js
    mongoose.connection.once('open',()=>{
        //连接成功后调用
        console.log('mongodb数据库连接成功~')
    })
    ```

#### 11.express快速搭建服务器

- 操作：

  - 1.初始化npm管理`npm init -y`

  - 2.下载express包`npm i express`

  - 3.引入`const express=require('express')`

  - 4.创建应用对象`const app=express()`

  - 5启动服务器

    ```js
    //参数填入端口号（建议3000,5000）
    app.listen(5000,err=>{
    	if(err)console.log(err)//失败打印错误信息
    	else console.log('express服务器启动成功')//成功
    })
    ```

  - 6.创建路由，监听请求

    ```js
    //监听get请求
    //参数1请求路径 参数2回调函数
    app.get('/',(request,response)=>{
        //用户发送请求时触发回调函数
        //回调函数中有请求对象和响应对象两个形参
        //请求对象用来获取发送过来的请求数据
        //响应对象用于响应客户数据
        console.log('收到请求',request)
        
        response.send('响应完毕')
        //响应一般只能响应一次，下载后面的响应会覆盖前面的响应
        //响应完了，后面的代码就不执行了
        console.log('不执行')
    })
    
    //监听post请求
    app.post('/',(request,response)=>{
        //用户发送请求时触发回调函数
    })
    ```

#### 12.url统一资源定位符

- url--(Uniform Resource Locator),统一资源定位符的意思

- 作用：在互联网中找到指定的资源文件，就需要通过url去寻找，url就相当于互联网中的地址。

- url的组成部分：`协议：//域名：端口号/路径/...?查询字符串#hash值`

  例：`http://localhost:5000/test/app?name=zs&&age=ls#...`

- 端口号是计算机中应用程序的唯一标识符，每个程序启动都会占用一个端口号，并且不能重复，重复的端口号不能运行。
- 查询字符串和hash值是客户端上传给服务器的数据，可以忽略

#### 13.http协议

- 协议：指网络中两台计算机进行通信必须准守的规则

- http协议:

  - 特点：无状态(需要缓存才能记住)

  - 版本：http1.0(不支持长连接)

    ​			http1.1(主流版本，支持长连接)

    ​			http2.0(最新版，并发量大，兼容性差)

    ​			https(传输数据加密处理，适用于银行等事务,较http安全)

- http协议规定了通信规则，客户端和服务器需要通过发送指定格式的请求报文和响应报文的方式进行交互。

#### 14.用户在地址栏中输入url地址，按下回车后，一直到界面响应，这个过程发生了什么？

- 1.解析DNS（优先找缓存）

  -寻找域名匹配的IP地址

  -浏览器DNS缓存==》本地==》路由==》运营商=》全球13台DNS服务器(找不到就不存在)

- 2.TCP进行三次握手

  - 浏览器发给服务器：你在吗？
  - 服务器发给浏览器：我在
  - 浏览器发给服务器：我要跟你说话了

- 3.客户端发送请求报文

- 4.服务器生成响应报文

- 5.解析返回的数据

  -解析外部资源请求

  -解析HTML：生成DOM树

  -解析CSS：生成CSSOM树

  -合成一个render渲染树

  -js是否操作了DOM？进行重绘重排？

- 6.TCP四次挥手

  - 浏览器发给服务器：我数据发送完了，断开连接吧
  - 服务器发给浏览器：等一等我在检查一遍，没有传输完则再继续传输一会
  - 服务器发给浏览器：数据都完整了，你断开吧
  - 浏览器发给服务器：好的我断开了

#### 15.手写ajax请求

- 1.实例化对象`const xhr=new XMLHttpRequest()`

- 2.请求首行`xhr.open('get/post'，'http://localhost:5000/ajax[?name=zs&age=14]')`

- 3.请求头

  `xhr.setRequestHeader('content-type',;application/x-www-form-urlencoded)`

- 4.请求请 并发送请求至服务器

  `xhr.send(['name=zs&age=14'])`

- 5.监听状态变化事件

  ```js
  xhr.onreadystatechange=function(){
  
  	//只监听了状态2、3、4
  
  	if(xhr.readyState===4){
          //状态为4表示请求完成
          console.log(xhr.responseText)//打印响应数据文本(字符串格式)
      }
  
  }
  ```

  