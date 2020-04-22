# javascript 规范
>内容不是自创，只做收集整合。

### 基本书写
##### 使用两个空格进行缩进
```
function hello (name) {
  console.log('hi', name)   // ✓ 正确
    console.log('hello', name)   // ✗ 错误
}
```

##### 除了缩进，不要使用多个空格
```
function hello (name) {
    const id =    1234    // ✗ 错误
    const id = 1234       // ✓ 正确
}
```

##### 不要在句末使用分号
```
function hello (name) {
    const a = 'a'   // ✓ 正确
    const a = 'a';  // ✗ 错误
}
```

##### 字符串统一使用单引号
```
console.log('hello there')
// 如果遇到需要转义的情况，请按如下三种写法书写
const x = 'hello "world"'
const y = 'hello \'world\''
const z = `hello 'world'`
```

##### 代码块中避免多余留白
```
if (user) {
                            // ✗ 错误
    const name = getName()
 
}

if (user) {
    const name = getName()    // ✓ 正确
}
```

##### 关键字后面加空格
```
if (condition) { ... }   // ✓ 正确
if(condition) { ... }    // ✗ 错误
```

##### 函数声明时括号与函数名间加空格
```
function name (arg) { ... }   // ✓ 正确
function name(arg) { ... }    // ✗ 错误

run(function () { ... })      // ✓ 正确
run(function() { ... })       // ✗ 错误
```

##### 展开运算符与它的表达式间不要留空白
```
fn(... args)    // ✗ 错误
fn(...args)     // ✓ 正确
```

##### 遇到分号时空格要后留前不留
```
for (let i = 0 ;i < items.length ;i++) {...}    // ✗ 错误
for (let i = 0; i < items.length; i++) {...}    // ✓ 正确
```

##### 代码块首尾留空格
```
if (admin){...}     // ✗ 错误
if (admin) {...}    // ✓ 正确
```

##### 圆括号间不留空格
```
getName( name )     // ✗ 错误
getName(name)       // ✓ 正确
```

##### 注释首尾留空格
```
//comment           // ✗ 错误
// comment          // ✓ 正确

/*comment*/         // ✗ 错误
/* comment */       // ✓ 正确
```

##### 逗号后面加空格
```
// ✓ 正确
const list = [1, 2, 3, 4]
function greet (name, options) { ... }
// ✗ 错误
const list = [1,2,3,4]
function greet (name,options) { ... }
```

##### 不允许有连续多行空行
```
// ✓ 正确
const value = 'hello world'
console.log(value)
// ✗ 错误
const value = 'hello world'



console.log(value)
```

##### 键值对当中冒号与值之间要留空白
```
const obj = { 'key' : 'value' }    // ✗ 错误
const obj = { 'key' :'value' }     // ✗ 错误
const obj = { 'key':'value' }      // ✗ 错误
const obj = { 'key': 'value' }     // ✓ 正确
```

### 变量定义
##### 使用 const/let 定义变量
```
const a = 'a'
a = 'b'   // ✗ 错误，请使用 let 定义

let test = 'test'

var noVar = 'hello, world'   // ✗ 错误，请使用 const/let 定义变量
```

##### 每个 const/let 关键字单独声明一个变量
```
// ✓ 正确
const silent = true
let verbose = true

// ✗ 错误
const silent = true, verbose = true

// ✗ 错误
let silent = true,
    verbose = true
```

##### 不要使用 undefined 来初始化变量
```
let name = undefined    // ✗ 错误

let name
name = 'value'          // ✓ 正确
```

##### 对于变量和函数名统一使用驼峰命名法
```
function my_function () { }    // ✗ 错误
function myFunction () { }     // ✓ 正确

const my_var = 'hello'           // ✗ 错误
const myVar = 'hello'            // ✓ 正确
```


###基本类型
##### 不要省去小数点前面的 0
```
const discount = .5      // ✗ 错误
const discount = 0.5     // ✓ 正确
```

##### 不要使用多行字符串
```
const message = 'Hello \
                 world'     // ✗ 错误
```

##### 检查 NaN 的正确姿势是使用 isNaN()
```
if (price === NaN) { }      // ✗ 错误
if (isNaN(price)) { }       // ✓ 正确
```

##### 用合法的字符串跟 typeof 进行比较操作
```
typeof name === undefined       // ✗ 错误
typeof name === 'undefined'     // ✓ 正确
```


### 对象与数组
##### 对象中定义了存值器，一定要对应的定义取值器
```
const person = {
    set name (value) {    // ✗ 错误
        this._name = value
    }
}

const person = {
    set name (value) {
        this._name = value
    },
    get name () {         // ✓ 正确
        return this._name
    }
}
```

##### 使用数组字面量而不是构造器
```
const nums = new Array(1, 2, 3)   // ✗ 错误
const nums = [1, 2, 3]            // ✓ 正确
```

##### 不要解构空值
```
const { a: {} } = foo         // ✗ 错误
const { a: { b } } = foo      // ✓ 正确
```

##### 不要扩展原生对象
```
Object.prototype.age = 21     // ✗ 错误
```

##### 外部变量不要与对象属性重名
```
let score = 100
function game () {
  score: while (true) {      // ✗ 错误
    score -= 10
    if (score > 0) continue score
    break
  }
}
```

##### 避免使用不必要的计算值作对象属性
```
const user = { ['name']: 'John Doe' }   // ✗ 错误
const user = { name: 'John Doe' }       // ✓ 正确
```

### 函数
##### 不要定义冗余的函数参数
```
function sum (a, b, a) {  // ✗ 错误
  // ...
}

function sum (a, b, c) {  // ✓ 正确
  // ...
}
```

##### 不要使用多余的括号包裹函数
```
const myFunc = (function () { })   // ✗ 错误
const myFunc = function () { }     // ✓ 正确
```

##### 嵌套的代码块中禁止再定义函数
```
if (authenticated) {
  function setAuthUser () {}    // ✗ 错误
}
```

##### 禁止使用 Function 构造器
```
const sum = new Function('a', 'b', 'return a + b')    // ✗ 错误
```

##### 自调用匿名函数 (IIFEs) 使用括号包裹
```
const getName = function () { }()     // ✗ 错误

const getName = (function () { }())   // ✓ 正确
const getName = (function () { })()   // ✓ 正确
```

### 类定义
##### 类名要以大写字母开头
```
class animal {}
const dog = new animal()    // ✗ 错误

class Animal {}
const dog = new Animal()    // ✓ 正确
```

##### 避免对类名重新赋值
```
class Dog {}
Dog = 'Fido'    // ✗ 错误
```

##### 子类的构造器中一定要调用 super
```
class Dog {
  constructor () {
    super()   // ✗ 错误
  }
}

class Dog extends Mammal {
  constructor () {
    super()   // ✓ 正确
  }
}
```

##### 使用 this 前请确保 super() 已调用
```
class Dog extends Animal {
  constructor () {
    this.legs = 4     // ✗ 错误
    super()
  }
}
```

##### 禁止多余的构造器
```
class Car {
  constructor () {      // ✗ 错误
  }
}

class Car {
  constructor () {      // ✗ 错误
    super()
  }
}
```


##### 无参的构造函数调用时要带上括号
```
function Animal () {}
const dog = new Animal    // ✗ 错误
const dog = new Animal()  // ✓ 正确
```

##### new 创建对象实例后需要赋值给变量
```
new Character()                     // ✗ 错误
const character = new Character()   // ✓ 正确
```

### 模块
##### 同一模块有多个导入时一次性写完
```
import { myFunc1 } from 'module'
import { myFunc2 } from 'module'          // ✗ 错误

import { myFunc1, myFunc2 } from 'module' // ✓ 正确
```

##### import, export 和解构操作中，禁止赋值到同名变量
```
import { config as config } from './config'     // ✗ 错误
import { config } from './config'               // ✓ 正确
```

##### import, export 和解构操作中，禁止赋值到同名变量
```
import { config as config } from './config'     // ✗ 错误
import { config } from './config'               // ✓ 正确
```

### 语句
##### 避免在 return 语句中出现赋值语句
```
function sum (a, b) {
  return result = a + b     // ✗ 错误
}
```

##### 禁止使用 with
```
with (val) {...}    // ✗ 错误
```

##### 不要随意更改关键字的值
```
let undefined = 'value'     // ✗ 错误
```

##### return，throw，continue 和 break 后不要再跟代码
```
function doSomething () {
  return true
  console.log('never called')     // ✗ 错误
}
```

### 逻辑与循环
##### 始终使用 === 替代 ==
>例外： obj == null 可以用来检查 null || undefined
```
if (name === 'John')   // ✓ 正确
if (name == 'John')    // ✗ 错误
if (name !== 'John')   // ✓ 正确
if (name != 'John')    // ✗ 错误
```

##### 避免将变量与自己进行比较操作
```
if (score === score) {}   // ✗ 错误
```

##### 多行 if 语句的的括号不能省略
```
// ✓ 正确
if (options.quiet !== true) console.log('done')
// ✓ 正确
if (options.quiet !== true) {
  console.log('done')
}
// ✗ 错误
if (options.quiet !== true)
  console.log('done')
```

##### 对于三元运算符 ? 和 : 与他们所负责的代码处于同一行
```
// ✓ 正确
const location = env.development ? 'localhost' : 'www.api.com'

// ✓ 正确
const location = env.development
  ? 'localhost'
  : 'www.api.com'

// ✗ 错误
const location = env.development ?
  'localhost' :
  'www.api.com'
```

##### 请书写优雅的条件语句（avoid Yoda conditions）
```
if (42 === age) { }    // ✗ 错误
if (age === 42) { }    // ✓ 正确
```

##### 循环语句中注意更新循环变量
```
for (let i = 0; i < items.length; j++) {...}    // ✗ 错误
for (let i = 0; i < items.length; i++) {...}    // ✓ 正确
```

##### 如果有更好的实现，尽量不要使用三元表达式
```
let score = val ? val : 0     // ✗ 错误
let score = val || 0          // ✓ 正确
```

##### switch 语句中不要定义重复的 case 分支
```
switch (id) {
  case 1:
    // ...
  case 1:     // ✗ 错误
}
```

##### 避免不必要的布尔转换
```
const result = true
if (!!result) {   // ✗ 错误
  // ...
}

const result = true
if (result) {     // ✓ 正确
  // ...
}
```

##### 避免使用逗号操作符
```
if (doSomething(), !!test) {}   // ✗ 错误
```


### 错误处理
##### 不要丢掉异常处理中 err 参数
```
// ✓ 正确
run(function (err) {
  if (err) throw err
  window.alert('done')
})
// ✗ 错误
run(function (err) {
  window.alert('done')
})
```

##### catch 中不要对错误重新赋值
```
try {
  // ...
} catch (e) {
  e = 'new value'             // ✗ 错误
}

try {
  // ...
} catch (e) {
  const newVal = 'new value'  // ✓ 正确
}
```

##### 用 throw 抛错时，抛出 Error 对象而不是字符串
```
throw 'error'               // ✗ 错误
throw new Error('error')    // ✓ 正确
```

##### 使用 Promise 一定要捕捉错误
```
asyncTask('google.com').catch(err => console.log(err))   // ✓ 正确
```





