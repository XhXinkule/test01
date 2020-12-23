#### **0.**  js的组成部分及作用（相对于浏览器而言）

- \1.  ESMAScript：负责核心语法规范
- \2.  DOM：用于JavaScript与html文档进行交互，加载页面时将文档映射成树状结构，使用DOM提供一些列标准接口(API)来操作文档的结构、样式和行为。
- \3.  BOM：负责客户端浏览器的管理，使JavaScript有能力与浏览器进行交互，但是BOM没有标准化，不同浏览器提供商可以任意扩展。

#### **1.**什么是DOM

-    Document Object Modul ：文档-对象-模型
-    DOM是W3C指定的一套技术规范，用来描述JS脚本语言如何与HTML文档进行交互的标准。
- DOM在加载页面时，web浏览器会生成一个树型结构用于表示页面内部结构。它的最顶层是document对象，下面是html、body
- DOM语法提供了一些标准结构，也称API，就是一些函数和方法，这些接口可以让开发人员对页面文档、样式、行为进行操作。

#### **2.**谈一谈NULL

-    Null值表示一个空对象指针
- Null的常见场景：
- \1.  作为对象原型链的终点（Object.__proto__:null）
- \2.  用于保存一个将来要使用的对象的初始化变量
- \3.  将一个对象设置为垃圾对象（取消地址指向）

#### **3.**谈一谈undefined

- Undefiend代表未定义，一般不会设置undefined值，出错了才会打印出来。
- Undefined的常用场景：
- 1.表量被声明了，但没有赋值 
- 2.调用函数时，应提供参数而没有提供 
- 3.对象没有赋值的属性（扩展属性但没有赋值）
- 4.函数没有返回值或返回值为空，调用时返回undefined

#### **4.DOM**节点类型

-    1.文档节点 document节点 根节点
-    2.元素节点 element节点 html、body···
-    3.文本节点 text节点
-    4.属性节点 attribute节点 叶子节点
-    5.注释节点 comment节点（不常用）

#### **5.DOM**节点的基本属性

-    节点名称：nodeName
- 文档-#document 文本-#text 注释-#comment 
- 元素-标签名大写 属性-属性名 
-    节点类型：nodeType
- 数字表示文档-9 元素-1 文本-3 注释-8 属性-2
-    节点的值：nodeValue
- 元素、文档：null，文本：文本内容（保留空白字符）
- 注释：备注是内容，属性：属性值

####  6.旧获取元素的方法

- 通过id：document.getElementById(“id”);
- 通过类名:document.getElementsByClassName(“类名”);
- 通过标签名:document.getElemtnsByTagName(“标签名”);
- 通过name:document.getElementsByName(“name”);几乎不用                                  

#### **8.**新旧获取元素方法对比

-    旧方法返回的集合为HTMLCollection（HTML集合）
-    新方法返回的集合为nodeList（节点集合）
-    HTMLCollection集合获取元素时是动态的，会随着元素的添加而实时改变集合的长度。
-    nodeList集合是静态的，新元素添加不会马上改变集合长度，nodeList需要重新获取才能得到最新的

#### **9.**通过节点关系获取元素

- 获取所有子元素：ele.children
- 获取第一个子元素：ele.firstChild、ele.firstElementChild
- 获取最后一个子元素:ele.lastChild、ele.lastElementChild
-    获取上一个兄弟元素:
- ele.previousSibling、ele.previousElementSibling
- 获取下一个兄弟元素:
- ele.nextSibling、ele.nextElementSibling
- 获取元素的父节点:ele.parentNode

#### **10.**获取主要节点的方法

- 获取html节点：document.documentElement
- 获取body节点：document.body
- 获取head节点：document.head

#### **11.DOM 0**级绑定事件

```javascript
ele.on+事件类型=function（）{

   //触发事件执行的代码……

}
```

#### **12.DOM 0**级事件类型

- ##### 1.鼠标点击事件：

   -click单击事件

   -contextmenu 鼠标右击

     -dbclick 双击（300ms间隔）

     -mousedown 鼠标按下

     -mouseup 鼠标抬起

- ##### 2.鼠标移动事件：

    -mousemove 鼠标移动

    -mouseover 鼠标移入（冒泡）

    -mouseout 鼠标移出（冒泡）

    -mouseenter 鼠标移入（不冒泡）

    -mouseleave 鼠标移出（不冒泡）

- ##### 3.键盘事件:

     -keydown 键盘按下

     -keyup 键盘抬起

- ##### 4.表单事件：

     -input 表单内发生变化

     -change 表单失去焦点时判断表单内是否发生变化

- ##### 5.滚动条事件：

     -scroll 鼠标滚轮滚动

- ##### 6.加载事件：

     -load 加载事件（资源全部加载完毕才触发）

- ##### 7.调整大小事件

     -resize 窗口大小发生变化

- ##### 8.焦点事件：

    -focus 获得焦点

    -blur 失去焦点

#### **13.**谈一谈window对象

-    Window对象有两重身份：
- \1.  作为ECMAScript规定的Global全局对象的替代，全局的变量和函数都是window的属性和方法。
- \2.  在DOM中作为顶层对象，代表浏览器的实例

#### **14.BOM**中提供的三种弹框方式

-    1.alert（提示弹框）
-    2.confirm（确认弹框）
-    3.prompt（输入弹框）

#### **15.BOM**打开和关闭窗口

-    Window.open()打开新的窗口 也可以跳转到指定url
-    -参数1：url 地址（跳转地址）
-    -参数2：_self（覆盖当前窗口）  _blank(默认，打开新窗口)
-    Window.close（）关闭自身

#### **16.BOM**中的其他对象 

​     **1.navigator（导航者）对象**

-    属性：onLine（是否连接网络）
- ​        Platform（平台、操作系统）
- ​        userAgent（用户代理、浏览器识别码）

​     **2.location（位置）对象**

-    属性：href（超文本引用）设置或获取当前文档完整URL地址（可以重向）
- ​        Protocol（协议）  协议包括后面的冒号 http：
- ​        host （主机）主机+端口号
- ​        port (端口) 端口号
- ​         pathname (路径名称) 路径部分
- ​        search（查询）查询字符串部分（？键值对）
- ​        hash（哈希、散表） 锚点（#）
-    方法：assign(“http://网址”) 分派到某个网址
- ​        Replace(“http://网址”)替换当前地址，不留下历史记录
- ​        Reload() 重新加载、刷新

​    **3.history（历史记录）对象**

- 方法：back()（后面的）返回上一个页面
- ​      forward()（前面的）去前一个页面
- ​      go(数字) 跳转任意 整数为前进 负数是后退

#### **17.**设置计时器和清除计时器

- 1.设置延时计时器 setTimeout（code,time）
-    Code：需要执行的代码
-    Time：延迟的时间
- 清除延时计时器：clearTimeout（timer）
- 2.设置间歇计时器 setInterval（code,time）
-    Code:需要执行的代码
-    Time:间隔执行的时间
-    清除间歇计时器：clearIterval（timer）

#### **18.**常见计时器面试题

```javascript
for (var i = 0; i < 5; i++) {
            setTimeout(function () {
                console.log(i); //5 5 5 5 5 
            }, 0)
}
/*
 问题所在：
      1.所有定时器使用的是同一个i
      2.定时器是在i变成5的时候才能执行
 解决方案：
      1.让每一个计时器都有自己的i
      2.所以在计时器外边嵌套一层IIFE，并把i传参传进去
*/
for (var i = 0; i < 5; i++) {
            (function (i) {
                setTimeout(function () {
                    console.log(i); //0 1 2 3 4
                }, 0)
            })(i)
}

```

#### **19.DOM**节点的增删改查

- 创建元素节点：document.creatElement(“标签名”)
- 创建文本节点：document.creatTextNode(“文本内容”)
- 把B节点插入A的最后一个字节点：
- A.  appendChild（B）
- 把new节点插入到父节点为A的old节点的前面
- A.  insertBefore(new,old)
- 浅克隆：复制一个A节点的最外层
- A.  cloneNode()
- 深克隆：复制一个A节点及其下面的所有子节点
- A.  cloneNode(true)
- 删除A节点的子节点B(删除B节点)
- A.  removeChild(B)或B.parent.removeChild(B)
- 将new节点替换A节点下的old节点
- A.  replaceChild(new,old)

#### **20.offsetWidth**、clientWidth、scrollWidth属性

- 获取元素的内容区+内边距+边框 ele.offsetWidth
- 获取元素的内容区+内边距 ele.clientWidth
- 获取元素的内容区和内边距完整的宽度（包括超出父元素部分）scrollWidth

#### **21.** **获取窗口的高度**

- 主流浏览器是html元素的clientHeight
- Document.documentElement.clientHeight
- 低版本浏览器（ie6以下）是body元素的高度
- Document.body.clientHeight

#### **22.** **获取和设置滚动条位置**

- Window.pageYOffset(ie8以下不兼容)
- Document.documentElement.scrollTop(ie6以下不兼容)
- Document.body.scrollTop(ie6及以下才兼容)
- Window.scrollTo(x,y) (全兼容)

- **补充：clientLeft和clientTop代表边框的宽度和高度**

#### **23.** **获取和设置元素的位置**

- offsetLeft：当前元素与定位不为static的父级元素之间的距离，没有到根元素的距离
- offsetParent：获取当前元素最近的定位不为static的父元素

#### **24.** **获取窗口边界对象方法—全兼容**

- **Ele.getBoundingClientRect()**
- 对象中的属性分别是：
- Left：当前元素左边框外边界到窗口左边缘的距离
- Right：当前元素右边框外边到窗口左边缘的距离
- Top：当前元素上边框外边到屏幕上边缘的距离
- Bottom: 当前元素下边框外边到屏幕下边缘的距离
- Width:元素的内容区+内边距+边框宽度
- Height：元素内容区+内边距+边框高度

#### **25.innerHTML**、innerText、outerHTML、outerText、textContent属性的区别

- InnerHTML-设置：替换元素的文本内容，会解析HTML代码

  ​			       -获取：获取文本内容，会显示HTML代码

- InnertText-设置：替换元素的本文内容，不解析HTML代码

  ​		          -获取：获取文本内容，不会显示HTML代码

- outerHTML-设置：直接覆盖当前元素，会解析HTML代码

  ​			       -获取：获取当前元素的内容，包含当前标签及其所有子标签内容，显示HTML代码

- outerText-设置：直接覆盖当前元素，不解析HTML代码

  ​			        -获取：只获取当前标签的内容，不显示HTML代码

- textContent-设置：替换文本内容，不解析HTML代码

  ​					-获取：获得文本内容，不显示HTML代码，但可以获取隐藏元素的内容和空白字符（不兼容ie8以下）

#### **26.** **属性节点的增删改查**

- 设置属性值：ele.属性名=value;
- 获取属性值：ele.属性名
- 创建属性：ele.setAttribute(key,value)
- 获取属性：ele.getAttribute(key)
- 删除属性：ele.removeAttribute(key)

#### **27.H5**新提供自定义属性的方法

- 声明为每个自定义属性前面加上data-的前缀
- 每个元素都有一个dataset属性，调用会返回一个对象，对象里面包含所有的自定义属性。通过操作对象的方法来获取里面的自定义属性。
- 创建属性：ele.dataset.属性名=value
- 获取属性：ele.dataset.属性名
- 删除属性：delete ele.dataset.属性名

#### **28.**重绘和重排 

- 重绘：当渲染树中更新属性只会影响元素的外观、风格，不会影响元素的布局时，浏览器需要重新绘制当前元素的样式，这个过程叫做重绘。
- 重排（回流）：当渲染树中的一部分或者全部，因为元素的尺寸、布局、隐藏等改变引起了页面的重新排列，这个过程叫做重排。
- 重新排列后，浏览器又会重新绘制收到影响的元素，即重排一定会引起重绘，但是重绘不一定会引起重排。
- 在页面布局越来越复杂时，一个元素的重排会带来一系列的反应，触发整个页面的重绘重排，性能代价是高昂的。
- 但是重绘和重排我们是不可避免的，我们能做的只是减少重绘和重排。

#### **29.**创建文档碎片节点方法--createDocumentFragment 

- Document.creatDocumentFragment();
- 文档碎片节点作用：提供中转站作用，用来保存将要操作的节点，等节点全部准备完毕，在进行整体操作，就只会有一次重绘重排了。（告诉我们:能先用数据处理好的操作，先用数据操作，等操作完毕了再进行页面显示操作。）

#### **30.**什么是事件流（事件机制、事件模型）

- 事件流：多个节点对同一事件响应的先后顺序。
- 事件流的顺序分为三种：
- \1.  冒泡：事件执行从最精确的目标元素依次向外传播到最不精确的元素。
- \2.  捕获：事件执行从最不精确的元素依次向里传播到最精确的元素。
- \3.  W3C事件流：第一步先执行捕获、第二步执行目标元素、第三步执行冒泡。

#### **31.DOM0**级事件和DOM2级事件的区别

- DOM0级事件：给一个元素绑定同一个事件多次，后面绑定的事件会覆盖前面绑定的事件。并且会默认触发冒泡。
- DOM2级事件：事件类型前面不需要再加on，统一元素可以绑定同一事件多次且不覆盖，还可以当前事件为冒泡还是捕获。

#### **32.**绑定DOM2级事件

- Ele.addEventListener(type,fn,boolean)

- -参数1：绑定事件类型（DOM0级事件名）

  ​        		新增DOM2级事件：DOMContentLoaded

- -参数2：事件函数Function(){}、fn

- -参数3：布尔值 设置当前事件流方式 

  ​				true为捕获 false为冒泡 默认false 

#### **33.**注销（销毁）事件

- DOM0级事件：ele.onclick=null (让事件函数不再被指向)
- DOM2级事件：ele.removeEventListener(type,fn)

#### **34.event**事件对象

-    在事件函数调用时，会产生arguments参数对象（伪数组），event事件对象会当做arguments伪数组中第一个值传入。
- Event事件对象中保存的是当前事件发生时的一系列信息。
- Event事件对象中的常用属性：
- \1.  clientX：鼠标到浏览器窗口的距离
- \2.  offset：鼠标到当前定位不为static元素的距离
- \3.  pageX：鼠标到文档边缘的距离
- \4.  screenX：鼠标到电脑屏幕的边缘的距离
- \5.  target：鼠标精确点击的目标元素
- \6.  type：事件类型

#### **35.**阻止传播兼容封装方法

- e.stopPropagation()—主流浏览器

- cancelBubble---IE低版本

  ```javascript
  //兼容性封装
  function xxx (){
    Returne.stopPropagation()e.stopPropagation:cancelBubble=true;
  }
  //是否存在阻止传播？如果是返回阻止传播：不是返回取消冒泡
  ```

#### **36.**阻止默认事件的方法

- 1.e.preventDefault（）-可书写到任意位置
- 2.return false（只能书写到当前函数最后）

#### **37.**数据类型检测

- 1.typeof（a）或typeof a 一般检测基本类型值（除了null）
- 2.=== 全等判断 null和undefined适用
- 3.全能检测方法：
- [object Date]
- [object String]
- [object Number]
- [object Array]
- [object Object]
- [object RegExp]
- [object Function]
- [object Boolean]
- [object Null]
- [object Undefined]
- Object.prototype.toString.call(需要检测的类型).slice(8, -1)

#### **38.**如何判断this怎么调用的

- 1.观察有没有显式绑定 call apply bind
- 2.观察函数是否是被实例化调用 new
- 3.观察函数调用的时候 有没有上下文对象
- 4.排除以上 this指向window

#### **39.call\apply\bind**

- 函数调用call、apply、bind方法都可以改变this的指向（它们的第一个参数）。
- 第一个参数后面的参数都是给调用的函数传递参数的。（可以省略）
- 1.fn.call.(obj,1,2,3)（arg1,arg2,arg3） 会调用顺便函数
- 2.fn.apply(obj,[1,2,3]) ([arg1,arg2,arg3]) 会顺便调用函数
- 3.fn.bind(obj,1,2,3) (arg1,arg2,arg3) 会返回一个改变this后的函数等待被调用

#### **40.**什么是闭包，闭包的产生，闭包的作用，闭包的缺点，闭包的解决方案

- **闭包**：

  ​	1.闭包是内部嵌套的函数

  ​      2.闭包是存在在内部函数中的

  ​      3.深入理解，闭包是包含被引用变量的closure对象

- **闭包的产生**：

  ​	1.函数嵌套函数

​           2.内部函数使用外部函数的变量或函数

​           3.外部函数被调用了

- **闭包的作用**：

  ​	1.延长了局部变量的声明周期（让局部变量可以长期驻留在内存中）

​           2.外部可以修改内部的局部变量

- **闭包的缺点**：

  ​	1.程序运行完后，局部变量仍会驻留在内存中，占用资源，导致内存泄漏（内存有一部分空间被占用无法使用）

- **解决方案**：

  ​	1.减少使用闭包（无法避免嵌套函数）

  ​    2.及时释放（内部函数指向null，被引用的外部函数就不再被引用，这样闭包不存在了，就都释放了）

#### **41.**写一个继承（构造函数）

```javascript
function Father(name){
  this.name=name;
}
Father.prototype.do=function(){“冲”}
function Child(name,age){
   //继承父类的属性
   Father.call(this,name);
   this.age=age;
}
//原型链继承
//父类的实例化对象可以找到子类的原型
Child.prototype=new Father();
//修正原型链
Child.prototype.constructor=Father;
```

#### **42.**写一个节流

```javascript
function throttle(fn,time){
   //初始时间
   Var startTime=0;
   Return function(){
      //获取当前时间
      var nowTime=Date.now();
      //判断事件是否大于延迟时间
      if(nowTime-startTime>time){
        //大于时才调用核心事件函数，并传入event对象
        fn.call(this.arguments[0]);
        lastTime=nowTime;
      }
	}
}
```

#### **43.**写一个防抖

```javascript
function debounce(fn,time){
   var time=null;
   return function(){
       //每次进入清除上次没有执行完的计时器
   		var _this=this;//获取核心函数的this
   		var _arguments=arguments;//获取核心函数的形参对象
   		//设置计时器，延迟执行核心函数
   		timer=setTimeout(function()){
      		//调用核心函数，替换this，传入核心形参对象
  			fn.call(_this._arguments[0]);
		},time)
	}
}
```

#### **44.new**操作符过程

```javascript
function New(construc){
   //1.创建空对象（实例化的得到的对象）
   var obj={};
   //2.链接原型链（空对象隐式连接构造函数的显示）
   obj.__proto__=construc.prototype;
   //3.调用构造函数并替换this为obj
   //传入参数从构造函数后面开始计算
   var result=construc.apply(obj,Array.from(arguments.slice(1)))
   //4.判断构造函数的返回值类型（）
   var isObj=typeof(result)===’object’&&result!=null;
   var isFun=typeof(result)===’function’;
   //如果是引用类型且不为null 
   if(isObj||isFun){
       //返回该引用类型
       return result;
   }
	//否则直接返回
	return obj;
}
```

#### **45.**写一个深拷贝

```javascript
//创建类型检测函数
function checkType(obj){
   //返回指定类型的字符串
   return Object.prototype.toString.call(obj).slice(8,-1);
}
//传入obj原生对象进行深拷贝
function deepClone(obj){
    //创建克隆对象（不确定对象类型）
    var cloneObj;
   	//判断对象类型
   	if(checkType(obj)===’Object’){
        //确定克隆对象类型为对象
       	cloneObj={};
   	}else if(checkType(obj)===’Array’){
       	//确定克隆对象类型为数组
       	cloneObj=[];
   	}else{
       	//基本类型直接返回
   	   	return obj;
   	}
    //遍历obj对象的属性
	for(var key in obj){
        //接受对象的属性值
   		var val=obj[key];
        //判断对象的属性值类型
        if(checkType(val)===’Object’||checkType(val)===’Array’){
            //如果是对象或数组递归调用深克隆
            cloneObj[key] = deepClone(val)
    	}else{
            //基本类型直接赋值
            cloneObj[key]=val;
        }
    }
    //返回克隆对象
    return cloneObj;  
}
```

#### **46.label**语句

- label语句就是给for循环前面加上一个名称，在break退出时可以控制退出哪一层for循环，而不是默认退出最近的for循环。

```javascript
//将外层循环标识为outer
outer:
for(var i=0;i<10;i++){
    //内存循环标识为inner
    inner:for(var j=0;j<10;j++){
        if(i==5&&j==5){//95
            break inner;//退出了内层循环
        }
    }
}
```

#### 47.instanceof 实例运算符

- L instanceof R
- 判断L的`prototype`（显示原型）是否经过了R的`_proto_`（隐式原型）
- 也代表R是否是L的实例化对象

#### **48.**变量对象（VO-- Variable Object）

- 1.变量对象是在创建执行上下文时才生成的。变量对象中保存的是当前上下文中需要的变量和函数
- 2.变量对象分为全局上下文VO（window）和函数上下文VO。
- 3.函数上下文VO的产生过程：
  - （1）收集所有的形参和实参，将他们一一对应以键值对形式保存在VO中。
  - （2）收集所有的局部函数，以键值对形式保存在VO中，如果有重名，则将其覆盖。
  - （3）收集所有的局部变量，以键值对形式保存VO中，如果变量与函数、形参重复，则不干扰它们。

#### **49.终极原型链**

![终极原型链](D:\feiqiu\feiq\Recv Files\面试题\终极原型链.png)

#### **50.**事件轮询机制

- Js是一个单线程语言。Js中的代码分为同步代码和异步代码。
- 同步代码：正常执行代码for循环，声明变量、函数、设置计时器、绑定事件等。
- 异步代码：计时器、事件、ajax中的回调函数等。
- 执行时机：进入全局，开始执行同步代码，当碰到设置定时器、绑定事件等操作需要等待才能调用回调函数时，就会将它们的回调函数交给DOM管理模块中去，DOM管理模块，会将这些回调函数进行排序（哪个先执行，哪个后执行），然后放入回调队列中（Event Loop）等待同步代码执行完毕再依次从回调队列中循环执行这些回调函数。

![事件轮询机制图](D:\feiqiu\feiq\Recv Files\面试题\事件轮询机制图.png)

#### **51.**写一个快排

```javascript
var arr=[4,2,1,-1,0,8,21,4,2];
//快排函数 传入数组
function quickSort(arr){
    //如果当前数组只剩一个值则返回当前数组无需比较
    if(arr.length<=1){
        return arr;
    }
    //获取中间值下标
    var cenIndex=Math.floor(arr.length/2);
    //获取中间值 并从数组中移除
    var cenVal=arr.splice(cenIndex,1);
    //创建小于数组、大于数组的容器
    var left=[],right=[];
    //遍历数组
    arr.forEach((item,index)=>{
        //当前值与中间值比大小
        if(item>=cenVal){
            //大于等于放入右边数组
            right.push(item);
            //退出进行下一次遍历
            return;
        }
        //小于放入左边数组
        left.push(val);
    });
    //左右数组进行递归快排 获得最终排好的结果数组
    var resLeft=quickSort(left);
    var resRight=quickSort(right);
    //返回结果数组与中间值合并的数组
    return resLeft.concat=(cenVal,resRight);    
}
```

#### **52.JSON**对象

- 1.JSON对象转换成json串：JSON.stringify(jsonObj)；
- JSON对象——>json串：undefiend会被忽略，函数也会被忽略
- 2.Json串转换成JSON对象：JSON.parse(jsonStr);
- Json串——>JSON对象：对象的属性和方法都必须加上双引号，单引号会报错。所有字符串的都必须是双引号。

#### 53.(H5)Web Worker分线程

- H5规范提供了JS分线程的实现，取名为：Wbe Worker。
- 可以将js代码到分线程中去运行，不影响主线程的代码正常执行。
- 不足（基本上只能进行运算数据等操作）：
  - 1.分线程中不能操作DOM
  - 2.不能跨域加载JS
  - 3.兼容性差

```javascript
/*使用方法*/
//主线程中:
//实例化一个新线程 参数为分线程js文件路径
var worker=new Worker('xxx.js');
//向分线程发送数据
worker.postMessage(data);
//接受分线程的数据
worker.onmessage=function(mes){
    console.log('主线程接受到分线程的数据:',mes.data);
    //主线程中关闭分线程
    worker.terminate();
}
```

```javascript
//分线程中(xxx.js文件):
//直接使用onmessage通讯事件（当其他线程向当前线程发送数据就会触发）
onmessage=function(mes){
    //mes为messageEvent对象 消息对象
    //data属性中存放了其他线程发来的数据
    console.log('分线程接收到数据:',mes.data);
    var sum=1+mes.data;
    //将数据发送给主线程
    postMessage(sum);
    //在分线程中关闭自己
    close();
}
```

#### 54.严格模式

- 严格模式下的js：声明定义变量更严格更安全。
- 可以提高js解析的性能、js代码运行的速度（载体运行js时不需要过多的去判断确认）。

- 使用方法：

```javascript
"use strict"//作用域的首行书写
a='我不想var';
console.log(a);//1.声明变量必须加上声明类型
function fn(){
    "use strict";
    console.log(this);//2.函数中this指向undefined
}
var b=3;//3.严格区分全局作用域和eval作用域
eval('var b;alert(b)');//undefiend
```

#### 55.let变量（作用于块级作用域）

- 可以减少使用全局变量的风险（全局变量容易被串改，产生闭包占用内存）

- 特点：
  - 1.let变量不能变量提升
  - 2.同一个作用域中不能重复声明
  - 3.块级作用域可以任意嵌套，let变量可以区分

- 特殊的for循环作用域问题:

```javascript
//for循环中的括号是介于全局和循环体之间的一个独立作用域
for (let i = 0; i < 3; i++) {
    //声明i没有报错
    let i = "a";
    console.log(i);//a a a
}
```

- let解决计时器问题

```javascript
for(let i=0;i<3;i++){
    setTimeout(function(){
        console.log(i);//0 1 2
    })
}
```

#### 56.const常量（不会变化的数据）

- const声明数据方式相对于其他的声明方式更安全，因为const声明的数据是不允许发生改变的。