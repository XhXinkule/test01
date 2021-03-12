### 1.Vue3介绍

- Vue3支持vue2中大多数特性
- 更好的支持Typescript
- 性能优化很大的提升
- 使用ES6中的Proxy代理替代了defineProperty实现响应式数据
- 重写虚拟DOM的实现和树摇（Tree-Shaking，vue拆分成了很多个模块，没用上的模块都会被摇掉，最小单位是一个js文件）
- 创建Vue3项目需要`vue-cli 4.5以上版本`

### 2.Vue3代码结构变化

- `main.js`
  - 按需引入vue中的createApp模块

```js
createApp(App).use(store).use(router).mount('#app')
//上面一行代码相当于下面vue2.x时
Vue.use(Vuex)
Vue.use(VueRouter)
new Vue({
    render:h=>h(App),
    store,
    router
})
vm.mount('#app')
```

- `store->index.js`按需引入vuex中的createStore模块

```js
//创建store对象并导出
export default createStore({
    state:{},
    mutations:{},
    actions:{},
    modules:{}
})
```

- `router->index.js`从vue-router中引入createRouter模块、createWebHistory模块、RouterRecordRaw模块

```js
//routes必须是一个数组，数组里面的放的必须是一个RouterRecordRaw-纯路由对象（必须有component属性和path属性）
const routes:Array<RouterRecordRaw>=[
    {
        path:'/',
        name:'Home',
        compoent:Home
    }
]

//创建路由器实例 new VueRouter({})
const router=createRouter({
    //相当于 mode:'history'
    history:createWebHistory(process.env.BASE_URL)
    routers
})

```

- `xxx.vue`组件 从vue中引入defineComponent模块

```js
//lang=ts 可以解析typescript 
<script lang="ts">
export default defineComponent({
	name:'Home',
    data(){
        a:123
    }
})
</script>
```

### 3.Vue3的新生命周期setup

- `setup`生命周期比`beforeCreate`之前先执行，并且只执行一次

- 并且在这个生命周期中，组件实例还未创建，不能使用this

- `setup`必须是一个同步函数，async函数的返回值是一个promise

- `setup一般返回一个对象`为模板提供数据，如果同时使用了data定义响应式数据，又

  使用了setup返回响应式数据，则会一起合并到组件对象的属性中，如果有重名，setup优先

- setup中的默认参数`props`和`context`
  - `props`参数接收了标签属性传递的数据
  - `context`参数，上下文对象，里面包含了attrs（接收没有在props中声明的属性）、slots（接收插槽数据）、emits（自定义事件的分发）

### 4.setup中创建响应式数据

- 从vue中引入`ref`和`reactive`方法

```js
setup(){
    //num 变成响应式数据
    //ref看的是num.value的值或地址的改变来响应 一般针对基本数据类型
    const num=ref(1)
    //obj 变成响应式对象 
    //reacive会深层次递归定义响应式数据 一般针对对象使用
    const obj=reactive({'name':'hgc'})
    return {
        num,
        obj
    }
}
```

