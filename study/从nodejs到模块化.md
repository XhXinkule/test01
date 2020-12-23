### 1.commonjs

- 引入模块:`require('第三方模块名/自定义模块路径')`

- 导出模块：

  1.`module.exports={key:value}/module.exports.key=value`

  2.`module.exports=value`

  3.`exports={key:value}/exports.key=value`

- node被一个默认函数包裹，这个函数提供了两个重要的属性

  1.`_filename`:返回当前文件的绝对路径

  2.`_dirname`:返回当前文件所处的文件夹(目录)的绝对路径