# 前端代码优化
##### 数组和对象操作避免使用构造函数
```
// ✗ 不推荐
const list = new Array(1, 2, 3)

// ✗ 不推荐
let arr = new Array()
arr[0] = 1
arr[1] = 2
arr[2] = 3

// ✗ 不推荐
const map = new Object({
    name: '张三',
    age: 18
})

// ✗ 不推荐
let obj = new Object()
obj.name = '张三'
obj.age = 18


// ✓ 推荐
const list = [1, 2, 3, 4, 5]

// ✓ 推荐
const map = {
    name: '张三',
    age: 18
}
```

##### 数组和对象深浅拷贝(对象同理)
>浅拷贝：改一个，另一个也会变  
>深拷贝：改一个，另一个不会变  
```
// 浅拷贝
let list = ['a', 'b', 'c']
let list_2 = list
list_2[0] = 'd'
console.log(list === list_2)  // true
console.log(list)     // ['d', 'b', 'c']
console.log(list_2)   // ['d', 'b', 'c']

// 深拷贝
let list = ['a', 'b', 'c']
let list_2 = [...list]
list_2[0] = 'd'
console.log(list === list_2)  // false
console.log(list)     // ['a', 'b', 'c']
console.log(list_2)   // ['d', 'b', 'c']
```

##### 数组去重
```
const arr = [5, 4, 1, 9, 5, 1, 6, 5]
const list = new Set(arr)   // [5, 4, 1, 9, 6]
```

##### 避免全局查找
> 访问局部变量比全局变量快(单次访问可以省略)
```
// ✗ 不推荐
const width = document.body.clientWidth
const width = document.body.clientHeight

// ✓ 推荐
const body = document.body
const width = body.clientWidth
const width = body.clientHeight
```

##### switch语句相对if较快
>通过将case语句按照最可能到最不可能的顺序进行组织
```
// ✗ 不推荐
if(type === 'a') {
    // ...
}else if(type === 'b'){
    // ...
}else if(type === 'c'){
    // ...
}

// ✓ 推荐
switch(type) {
    case 'a':
        // ...
        break
    case 'b':
        // ...
        break
    case 'c':
        // ...
        break
}
```

