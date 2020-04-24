# jsx 规范

### 基本书写
##### 代码缩进
>使用两个空格进行缩进，不要混合使用空格与制表符作为缩进
```
import Taro, { Component } from '@tarojs/taro'
import { View, Text } from '@tarojs/components'

class MyComponent extends Component {
  render () {
    return (
      <View className='test'>     // ✓ 正确
        <Text>12</Text>     // ✗ 错误
      </View>
    )
  }
}
```

##### 代码缩进
>JSX 属性均使用单引号
```
import Taro, { Component } from '@tarojs/taro'
import { View, Input } from '@tarojs/components'

class MyComponent extends Component {
  render () {
    return (
      <View className='test'>     // ✓ 正确
        <Text className="test_text">12</Text>     // ✗ 错误
      </View>
    )
  }
}
```

##### 对齐方式
>JSX 多个属性，多行书写，每个属性占用一行，标签结束另起一行
```
// ✗ 错误
<Foo superLongParam='bar'
     anotherSuperLongParam='baz' />

// ✓ 正确
<Foo
  superLongParam='bar'
  anotherSuperLongParam='baz'
/>

// 如果组件的属性可以放在一行就保持在当前一行中
<Foo bar='bar' />

// 多行属性采用缩进
<Foo
  superLongParam='bar'
  anotherSuperLongParam='baz'
>
  <Quux />
</Foo>
```

##### 空格使用
>终始在自闭合标签前面添加一个空格
```
// ✗ 错误
<Foo/>

// ✗ 错误
<Foo                 />

// ✗ 错误
<Foo
 />
 
// ✓ 正确
<Foo />
```

##### 属性书写
>属性名称始终使用驼峰命名法
```
// ✗ 错误
<Foo
  UserName='hello'
  phone_number={12345678}
/>

// ✓ 正确
<Foo
  userName='hello'
  phoneNumber={12345678}
/>
```

##### JSX 与括号
>用括号包裹多行 JSX 标签
```
// ✗ 错误
render () {
  return <MyComponent className='long body' foo='bar'>
           <MyChild />
         </MyComponent>
}

// ✓ 正确
render () {
  return (
    <MyComponent className='long body' foo='bar'>
      <MyChild />
    </MyComponent>
  )
}

// ✓ 正确
render () {
  const body = <div>hello</div>
  return <MyComponent>{body}</MyComponent>
}
```

##### 标签
>当标签没有子元素时，始终使用自闭合标签
```
// ✗ 错误
<Foo className='stuff'></Foo>

// ✓ 正确
<Foo className='stuff' />
```
>如果控件有多行属性，关闭标签要另起一行
```
// ✗ 错误
<Foo
  bar='bar'
  baz='baz' />

// ✓ 正确
<Foo
  bar='bar'
  baz='baz'
/>
```
  
### 书写顺序.
>在 Taro 组件中会包含类静态属性、类属性、生命周期等的类成员，其书写顺序最好遵循以下约定（顺序从上至下)  
1、static 静态方法  
2、constructor  
3、componentWillMount  
4、componentDidMount  
5、componentWillReceiveProps  
6、shouldComponentUpdate  
7、componentWillUpdate  
8、componentDidUpdate  
9、componentWillUnmount  
10、点击回调或者事件回调 比如 onClickSubmit() 或者 onChangeDescription()  
11、render  


### 通用约束与建议
##### 所有内置组件均需要引入后再使用
```
import React from 'react'
import { View } from '@/components'

class MyComponent extends React.Component {
  render () {
    return (
      <View className='test'>     // ✓ 正确
        <Text>12</Text>     // ✗ 错误
      </View>
    )
  }
}
```

##### 推荐使用对象解构的方式来使用 state、props
```
import React from 'react'
import {  View, Input } from '@/components'

class MyComponent extends Component {
  state = {
    myTime: 12
  }
  render () {
    const { isEnable } = this.props     // ✓ 正确
    const { myTime } = this.state     // ✓ 正确
    return (
      <View className='test'>
        {isEnable && <Text className='test_text'>{myTime}</Text>}
      </View>
    )
  }
}
```

##### 不要以 class/id/style 作为自定义组件的属性名
```
<Hello class='foo' />     // ✗ 错误
<Hello id='foo' />     // ✗ 错误
<Hello style='foo' />     // ✗ 错误
```

##### 不要使用 HTML 标签
```
<div className='foo'></div>     // ✗ 错误
<span id='foo' /></span>    // ✗ 错误
```

##### 不要在调用 this.setState 时使用 this.state
>由于 this.setState 异步的缘故，这样的做法会导致一些错误，可以通过给 this.setState 传入函数来避免
```
this.setState({
  value: this.state.value + 1
})   // ✗ 错误


this.setState(prevState => ({ value: prevState.value + 1 }))    // ✓ 正确
```

##### map 循环时请给元素加上 key 属性
```
list.map(item => {
  return (
    <View className='list_item' key={item.id}>{item.name}</View>
  )
})
```

##### 尽量避免在 componentDidMount 中调用 this.setState
>因为在 componentDidMount 中调用 this.setState 会导致触发更新
```
import React from 'react'
import { View, Input } from '@/components'

class MyComponent extends React.Component {
  state = {
    myTime: 12
  }
  
  componentDidMount () {
    this.setState({     // ✗ 尽量避免，可以在 componentWillMount 中处理
      name: 1
    })
  }
  
  render () {
    const { isEnable } = this.props
    const { myTime } = this.state
    return (
      <View className='test'>
        {isEnable && <Text className='test_text'>{myTime}</Text>}
      </View>
    )
  }
}
```

##### 不要在 componentWillUpdate/componentDidUpdate/render 中调用 this.setState
```
import React from 'react'
import { View, Input } from '@/components'

class MyComponent extends React.Component {
  state = {
    myTime: 12
  }
  
  componentWillUpdate () {
    this.setState({     // ✗ 错误
      name: 1
    })
  }
  
  componentDidUpdate () {
    this.setState({     // ✗ 错误
      name: 1
    })
  }
  
  render () {
    const { isEnable } = this.props
    const { myTime } = this.state
    this.setState({     // ✗ 错误
      name: 11
    })
    return (
      <View className='test'>
        {isEnable && <Text className='test_text'>{myTime}</Text>}
      </View>
    )
  }
}
```

##### 不要定义没有用到的 state
```
import React from 'react'
import { View, Input } from '@/components'

class MyComponent extends React.Component {
  state = {
    myTime: 12,
    noUsed: true   // ✗ 没有用到
  }
  
  render () {
    const { myTime } = this.state
    return (
      <View className='test'>
        <Text className='test_text'>{myTime}</Text>
      </View>
    )
  }
}
```

##### 组件最好定义 defaultProps
```
import React from 'react'
import { View, Input } from '@/components'

class MyComponent extends React.Component {
  static defaultProps = {
    isEnable: true
  }
  
  state = {
    myTime: 12
  }
  
  render () {
    const { isEnable } = this.props
    const { myTime } = this.state

    return (
      <View className='test'>
        {isEnable && <Text className='test_text'>{myTime}</Text>}
      </View>
    )
  }
}
```

##### render 方法必须有返回值
```
import React from 'react'
import { View, Input } from '@/components'

class MyComponent extends React.Component {
  state = {
    myTime: 12
  }
  
  render () {   // ✗ 没有返回值
    const { isEnable } = this.props
    const { myTime } = this.state

    <View className='test'>
      {isEnable && <Text className="test_text">{myTime}</Text>}
    </View>
  }
}
```

###### 值为 true 的属性可以省略书写值
```
<Hello personal />
<Hello personal={false} />
```

###### 子组件传入函数时属性名需要以 on 开头
```
import React from 'react'
import { View, Input } from '@/components'
import Tab from '../../components/Tab/Tab'

class MyComponent extends React.Component {
  state = {
    myTime: 12
  }

  clickHandler (e) {
    console.log(e)
  }
  
  render () {
    const { myTime } = this.state

    return (
      <View className='test'>
        <Tab onChange={this.clickHandler} />    // ✓ 正确
        <Text className='test_text'>{myTime}</Text>
      </View>
    )
  }
}
```





