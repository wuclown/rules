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

##### 避免使用不必要的计算值作对象属性
```
const user = { ['name']: 'John Doe' }   // ✗ 错误
const user = { name: 'John Doe' }       // ✓ 正确
```





