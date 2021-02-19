## 其他组件

- 缓存组件：`<keep-alive include="Life1"></keep-alive>`中
- 可以设置include属性，代表只会缓存Life1组件。
- 也可以设置exclude属性，代表除了哪个组件不缓存，值可以时一个包含组件名称的数组。



- 动态组件：通过`const Home=()=>import('./components/Home')`引入的组件就是动态组件

- 异步组件：在异步代码中使用import引入一个组件并返回一个promise对象

  ```javascript
  setTimeout(()=>{
      import ('./components/AsyncComp').then(module=>{console.log(module)})
  },0)
  ```

- 函数组件：组件中只有一个`<script>`标签，并且配置`functional：true`，无状态，无法实例化，没有任何生命周期钩子，轻量的，渲染性能高

  ```js
  //渲染的dom结构在render函数中
  render(createElement,context){
      //不能使用this，可以使用context对象，
      //context对象中的props属性中接受了传递到该组件中的数据
      const {title,imgUrl}=context.props
      //在render里面可以写jsx语法写虚拟DOM
      const vNodes=[];
      if(title){
          vNodes.push(<h2>{title}</h2>)
      }
      if(imgUrl){
          vNodes.push(<img src={imgUrl}/>)
      }
      return vNodes //返回需要渲染的虚拟DOM
  }
  ```

- 递归组件：组件内部使用组件自己，可以做树形结构图，

