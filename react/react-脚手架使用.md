# react脚手架使用

>react中写代码,写完的代码,也要打包. 自己配置webpack非常繁琐,所以直接使用react脚手架工具,帮我们直接配置好webpack以及项目的目录结构 

## create-react-app 

- 自定义创建react项目

  使用: 

1. 下载  npm i create-react-app -g
2. 使用这个工具  create-react-app 项目名称 



- 自动化创建react项目：

   npm中提供了一个新的指令: npx 

  npx create-react-app 项目名称 

  npx做的事情: 

1. 先往全局下载create-react-app这个脚手架工具
2. 自动通过这个脚手架工具,下载项目所有的所有文件 
3. 项目处理完毕,自动将create-react-app从全局中删除掉



