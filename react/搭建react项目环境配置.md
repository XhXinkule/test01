# react项目

## 1.项目目录搭建

- src
  - components 公共组件
  - pages  一些页面
  - assets  资源
  - utils 工具函数
  - api   异步请求相关
  - redux  
  - config  配置文件(路由配置)

## 2.项目环境搭建

### 2.1 rem适配环境搭建

```js
// 1.下载依赖包
// react-app-rewired 用于重写脚手架配置 会覆盖react教授架中的配置
// customize-cra 是react-app-rewired依赖的包
// babel-plugin-import 用于ant-mobile按需加载
// postcss-px2rem 将px转成rem
  yarn add react-app-rewired customize-cra babel-plugin-import postcss-px2rem -D
  yarn add antd-mobile
// 2. 修改默认配置:  
  找到package.json将scripts修改成下面的样子
"scripts": {
  "start": "react-app-rewired start",
  "build": "react-app-rewired build",
  "test": "react-app-rewired test"
}

// 3. 在项目根目录创建文件config-overrides.js(用于覆盖脚手架默认配置)
const { override, fixBabelImports,addPostcssPlugins} = require('customize-cra');

module.exports = override(
    // antd按需加载
  fixBabelImports('import', {
    libraryName: 'antd-mobile',
    style: 'css',
  }),
    // rem适配. 将px改为rem
   addPostcssPlugins([require("postcss-px2rem")({ remUnit: 37.5 })])
);

//4. 在index.js中引入适配rem的文件
```



### 2.2 路由搭建

```js
 yarn add react-router-dom 

// config/routes.js

import { lazy } from "react";

// 使用路由懒加载
// lazy不能单独使用，必须配置Suspence组件才能一起使用
const Home = lazy(() =>
  import(
     "../pages/Home"
  )
);

const routes = [
  {
    path: "/",
    component: Home,
  },
];

export default routes;


// App.js
export default class App extends Component {
  render() {
    return (
      <Suspense fallback={<div>loading...</div>}>
        <div id='demo'></div>
      </Suspense>
    )
  }
}

```

## 3.项目开始

### 3.1 搭建页面

>使用antd-mobile组件

- 标题  NavBar
- 文本输入 InputItem 
- 上下空白 WhiteSpace
- 左右空白 WingBlank
- 警告框 Modal

```js
<link

      rel="stylesheet"

      href="http://at.alicdn.com/t/font_2114538_oji84c98ghh.css"

    />

```



### 3.2 表单校验

>使用rc-form库实现

```js
1. 安装
yarn add rc-form

2. 引入高阶组件函数
import { createForm } from 'rc-form'

3. 将要进行表单校验的组件,传入createForm的第二次调用
export default createForm()(VerifyPhone)

4. 在InputItem使用表单校验

const { getFieldProps } = this.props.form
<InputItem
// getFieldProps第一个参数是字段名, 第二个参数可以忽略, 第三个参数是一个对象
    {...getFieldProps('phone', {
        // rules表示当前表单的校验规则
        rules: [
            {
                // validator表示使用自定义校验规则
                validator: this.validator
            }
        ]
    })}
	clear
	placeholder='请输入手机号'
>
</InputItem>

5. 定义validator函数
validator = (rule, value, callback) => {
     // 第一个参数是一个对象.可以获取到表单量字段名
     // 第二个参数是表单项的值
     // 第三个参数是一个回调函数,必须手动调用一个,表示验证成功
    let isDisabled = true
    if (/^1[3456789][\d]{9}$/.test(value)) {
      isDisabled = false
    }
    this.setState({
      isDisabled
    })
    callback()
  }

```





