# vscode 配置
>内容涞源网络，收集整合。

##### 保存格式化（缩进4、语句无分号、属性全部单引号），支持html、css、js、jsx。
插件：prettier（发现与Editorconfig部分规则不兼容）
```
// 覆盖默认 tabSize
"editor.detectIndentation": false,
// spaces 大小
"editor.tabSize": 4,
// 保存自动格式化
"editor.formatOnSave": true,
"editor.defaultFormatter": "esbenp.prettier-vscode",
// 单引号
"prettier.singleQuote": true,
// 语句结尾无分号
"prettier.semi": false,
// jsx单引号
"prettier.jsxSingleQuote": true,
// 在jsx中把'>' 是否单独放一行
"prettier.jsxBracketSameLine": true,
// 代码缩进 4
"prettier.tabWidth": 4,
// 箭头函数只有一个属性不用()包裹
"prettier.arrowParens": "avoid",
```

#### 页面注释
插件：koroFileHeader
>文件头部添加注释: window：ctrl+alt+i,mac：ctrl+cmd+i  
>在光标处添加函数注释: window：ctrl+alt+t,mac：ctrl+cmd+t  
>快捷键不可用很可能是被占用了：[参考这里](https://github.com/OBKoro1/koro1FileHeader/issues/5)  
```
"fileheader.configObj": {
     // 保存自动在页面头部添加注释（jsx文件不太兼容）
     "autoAdd": true
},
// 页面头部注释格式
"fileheader.customMade": {
    "Author": "wyj",
    "LastEditors": "wyj",
    "Date": "Do not edit",
    "LastEditTime": "Do not edit",
    "Description": ""
},
// 方法注释格式
"fileheader.cursorMode": {
    "Params": "",
    "Description": ""
},
```
