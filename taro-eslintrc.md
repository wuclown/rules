# taro eslintrc 配置
>内容涞源网络，收集整合。
#### 项目搭建使用taro init myApp选择 eslintrc 检查代码规则
```
{
    "root": true,
    "extends": ["taro"],
    "rules": {
        "no-unused-vars": ["error", { "varsIgnorePattern": "Taro" }],
        "react/jsx-filename-extension": [
            1,
            { "extensions": [".js", ".jsx", ".tsx"] }
        ],
        "indent": "error",
        // 禁止在 componentDidMount 里面使用 setState
        "react/no-did-mount-set-state": "error",
        // 禁止在 componentDidUpdate 里面使用 setState
        "react/no-did-update-set-state": "error",
        // 禁止直接修改 this.state
        "react/no-direct-mutation-state": "error",
        // 禁止在 componentWillUpdate 中使用 setState
        "react/no-will-update-set-state": "error",
        // 禁止拼写错误
        "react/no-typos": "error",
        // 禁止使用字符串 ref
        "react/no-string-refs": "error",
        // @fixable 禁止出现 HTML 中的属性，如 class
        "react/no-unknown-property": "error",
        // 禁止出现未使用的 propTypes
        // @off 不强制要求写 propTypes
        "react/no-unused-prop-types": "off",
        // 必须使用 Class 的形式创建组件
        "react/prefer-es6-class": ["error", "always"],
        // render 方法中必须有返回值
        "react/require-render-return": "error",
        // style 属性的取值必须是 object
        "react/style-prop-object": "error",
        // HTML 中的自闭和标签禁止有 children
        "react/void-dom-elements-no-children": "error",
        // @fixable 自闭和标签的反尖括号必须与尖括号的那一行对齐
        "react/jsx-closing-bracket-location": [
            "error",
            {
                "nonEmpty": false,
                "selfClosing": "line-aligned"
            }
        ],
        // @fixable jsx 的 children 缩进必须为四个空格
        "react/jsx-indent": ["error", 4],
        // 数组中的 jsx 必须有 key
        "react/jsx-key": "error",
        // 禁止在 jsx 中使用像注释的字符串
        "react/jsx-no-comment-textnodes": "error",
        // 禁止出现重复的 props
        "react/jsx-no-duplicate-props": "error",
        // 禁止使用未定义的 jsx elemet
        "react/jsx-no-undef": "error",
        // 禁止使用 pascal 写法的 jsx，比如 <TEST_COMPONENT>
        "react/jsx-pascal-case": "error",
        // @fixable jsx 的开始和闭合处禁止有空格
        "react/jsx-tag-spacing": [
            "error",
            {
                "closingSlash": "never",
                "beforeSelfClosing": "always",
                "afterOpening": "never"
            }
        ],
        // @fixable jsx 中的属性必须用双引号
        "jsx-quotes": ["error", "prefer-single"],
        // jsx 文件必须 import React
        "react/jsx-uses-react": "error",
        // 定义了的 jsx element 必须使用
        "react/jsx-uses-vars": "error",
        // @fixable 多行的 jsx 必须有括号包起来
        "react/jsx-wrap-multilines": "error",
        // 指定数组的元素之间要以空格隔开(,后面)， never参数：[ 之前和 ] 之后不能带空格，always参数：[ 之前和 ] 之后必须带空格
        "array-bracket-spacing": [2, "never"],
        // 最后一个参数不带逗号
        "comma-dangle": [2, "never"],
        // 控制逗号前后的空格
        "comma-spacing": [2, { "before": false, "after": true }],
        // 使用 === 替代 ==
        "eqeqeq": [2, "allow-null"],
        // 禁止对象字面量中出现重复的 key
        "no-dupe-keys": 2,
        // 禁止重复的 case 标签
        "no-duplicate-case": 2,
        // 禁止空语句块
        "no-empty": 2,
        // 禁止对 catch 子句的参数重新赋值
        "no-ex-assign": 2,
        // 禁止不必要的括号 //(a * b) + c;//报错
        "no-extra-parens": 0,
        // 禁止不必要的分号
        "no-extra-semi": 2,
        // 禁止对 function 声明重新赋值
        "no-func-assign": 2,
        // 禁止在嵌套的块中出现 function 或 var 声明
        "no-inner-declarations": [2, "functions"],
        // 禁止 RegExp 构造函数中无效的正则表达式字符串
        "no-invalid-regexp": 2,
        // 禁止在字符串和注释之外不规则的空白
        "no-irregular-whitespace": 2,
        // 禁止把全局对象 (Math 和 JSON) 作为函数调用 错误：var math = Math();
        "no-obj-calls": 2,
        // 禁止直接使用 Object.prototypes 的内置属性
        "no-prototype-builtins": 0,
        // 禁止正则表达式字面量中出现多个空格
        "no-regex-spaces": 2,
        // 禁用稀疏数组
        "no-sparse-arrays": 2,
        // 禁止出现令人困惑的多行表达式
        "no-unexpected-multiline": 2,
        // 禁止在return、throw、continue 和 break语句之后出现不可达代码
        "no-unreachable": 2,
        // 定义对象的set存取器属性时，强制定义get
        "accessor-pairs": 2,
        // 强制数组方法的回调函数中有 return 语句
        "array-callback-return": 0,
        // 强制把变量的使用限制在其定义的作用域范围内
        "block-scoped-var": 0,
        // 限制圈复杂度，也就是类似if else能连续接多少个
        "complexity": [2, 9],
        // 要求 return 语句要么总是指定返回的值，要么不指定
        "consistent-return": 0,
        // 强制所有控制语句使用一致的括号风格
        "curly": [2, "all"],
        // 禁止 if 语句中有 return 之后有 else
        "no-else-return": 0,
        // 禁止出现空函数.如果一个函数包含了一条注释，它将不会被认为有问题。
        "no-empty-function": 2,
        // 禁用不必要的标签
        "no-extra-label:": 0,
        // 禁止 case 语句落空
        "no-fallthrough": 2,
        // 禁止数字字面量中使用前导和末尾小数点
        "no-floating-decimal": 2,
        // 禁止在全局范围内使用 var 和命名的 function 声明
        "no-implicit-globals": 1,
        // 禁止在循环中出现 function 声明和表达式
        "no-loop-func": 1,
        // 禁用魔术数字(3.14什么的用常量代替)
        "no-magic-numbers": [1, { "ignore": [0, -1, 1] }],
        // 禁止在非赋值或条件语句中使用 new 操作符
        "no-new": 2,
        // 禁止对 Function 对象使用 new 操作符
        "no-new-func": 0,
        // 禁止对 String，Number 和 Boolean 使用 new 操作符
        "no-new-wrappers": 2,
        // 禁止自我赋值
        "no-self-assign": 2,
        // 禁止自身比较
        "no-self-compare": 2,
        // 禁用一成不变的循环条件
        "no-unmodified-loop-condition": 2,
        // 禁止出现未使用过的表达式
        "no-unused-expressions": 0,
        // 禁用未使用过的标签
        "no-unused-labels": 2,
        // 禁止不必要的 .call() 和 .apply()
        "no-useless-call": 2,
        // 禁用 with 语句
        "no-with": 2,
        // 禁止将变量初始化为 undefined
        "no-undef-init": 2,
        // 禁止修改 const 声明的变量
        "no-const-assign": 2,
        // 不允许在变量定义之前使用它们
        "no-use-before-define": "error",
        // 禁止类成员中出现重复的名称
        "no-dupe-class-members": 2,
        // 要求使用 let 或 const 而不是 var
        "no-var": "error",
        // 要求使用 const 声明那些声明后不再被修改的变量
        "prefer-const": 0,
        // 禁止在构造函数中，在调用 super() 之前使用 this 或 super
        "no-this-before-super": 2,
        // 禁止不必要的计算性能键对象的文字
        "no-useless-computed-key": 0,
        // 强制在块之前使用一致的空格
        "space-before-blocks": [2, "always"],
        // 强制在注释中 // 或 /* 使用一致的空格
        "spaced-comment": [
            2,
            "always",
            {
                "markers": [
                    "global",
                    "globals",
                    "eslint",
                    "eslint-disable",
                    "*package",
                    "!"
                ]
            }
        ]
    },
    "parser": "babel-eslint"
}
```
