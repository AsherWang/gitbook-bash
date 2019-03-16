# javascript的编码风格规范
## 关于jsx
jsx是理解支持javascript和html标签混写的一中语言。其中jsx中的标签实际上都是对象。初次之外和javascript没有太大差别(个人理解，未深入了解)。

## 关于typescript
typescript是javascript的超集，typescript代码经过编辑生成javascript代码。理论上可以在开发中从js切换到ts。

## 加载js文件
一般来说框架在导出的时候把加载js文件这一步都做了，如果需要手动写的话，尽量不使用内联js而把js代码放到一个单独的文件。当然也不绝对，如果你有一个好的理由来使用内联js的话。

## 代码风格规范工具 `eslint`
现在的前端项目大都使用eslint来统一代码风格，改工具在写代码的阶段就已经完成了代码风格的检查，对于不符合既定规范的代码一律在控制台警报或者直接报错。所以开发者在处理完报错之后提交的代码已经很大程序上符合规范了。  
这里贴个`saas-h5`的eslint的配置 `.eslintrc.js`， 具体配置可能因框架选取而不一样，建议定义在 __种子项目__ 中。

``` javascript
module.exports = {
  root: true,
  parserOptions: {
    parser: 'babel-eslint'
  },
  env: {
    browser: true,
  },
  // https://github.com/vuejs/eslint-plugin-vue#priority-a-essential-error-prevention
  // consider switching to `plugin:vue/strongly-recommended` or `plugin:vue/recommended` for stricter rules.
  extends: ['plugin:vue/essential', 'airbnb-base'],
  // required to lint *.vue files
  plugins: [
    'vue'
  ],
  // check if imports actually resolve
  settings: {
    'import/resolver': {
      webpack: {
        config: 'build/webpack.base.conf.js'
      }
    }
  },
  // add your custom rules here
  rules: {
    // don't require .vue extension when importing
    'import/extensions': ['error', 'always', {
      js: 'never',
      vue: 'never'
    }],
    // disallow reassignment of function parameters
    // disallow parameter object manipulation except for specific exclusions
    'no-param-reassign': ['error', {
      props: true,
      ignorePropertyModificationsFor: [
        'state', // for vuex state
        'acc', // for reduce accumulators
        'e' // for e.returnvalue
      ]
    }],
    "no-shadow": ["error", { "allow": ["state"] }],
    "linebreak-style": 0,
    "eslint no-unused-expressions": 0,
    // allow optionalDependencies
    'import/no-extraneous-dependencies': ['error', {
      optionalDependencies: ['test/unit/index.js']
    }],
    // allow debugger during development
    'no-debugger': process.env.NODE_ENV === 'production' ? 'error' : 'off',
    'no-console': process.env.NODE_ENV === 'production' ? 'error' : 'off'
  }
}

```

同样的，ts也有类似的代码检查工具 `tsint`

## 规范细节
这里列举的比较细碎，建议不用完整的定义各个细节，使用jslint中预设的代码规范，然后修改其中不符合我们需要的细节即可。
### 句末句号
句末请加句号 (这个有争议，个人做不了主，团队决定)
### 大括号不换行
是的不换行
``` javascript
    if (test === 1) {
        // do your task
    }
```
### 变量声明
- 对所有引用都使用 const，不要使用 var
- 如果引用是可变动的，则使用 let
- 避免无意义的变量名

### 对象
- 使用对象方法的简写方式  
  

``` javascript
// bad
const item = {
  value: 1,
  addValue: function (val) {
    return item.value + val
  }
}

// good
const item = {
  value: 1,
  addValue(val) {
    return item.value + val
  }
}
```
- 使用对象的解构赋值
``` javascript
    // normal
    const data = res.data;
    const ele = arr[0];

    // recommend
    const { data } = res;
```


### 不使用eval方法

### 拒绝with关键词
略生僻，我也是很偶然撞见的，那不如假装它不存在:P 

### 不修改内置对象
比如你给Numer添加了一个方法叫做isEven来判断这个数是不是偶数， 你用得很开心可能会让别人怀疑人生。

### 不要修改函数参数的值
如果有必要，请先clone一个出来再做修改

### 模块
使用标准的 ES6 模块语法 import 和 export
``` javascript
// bad
const util = require('./util');
module.exports = util;

// good
import Util from './util';
export default Util;

// better
import { Util } from './util';
export default Util;
```
### 字符串 
- 推荐使用单引号
- 拼接字符串使用字符串模板，少用加号
- 字符串太长，换行用加号  
  

``` javascript
const mmstr = 'asjdlkjasd';
const testStr2 = `${mmstr}kajsd`;
const testStr3 = '123123123123123123' + 
    'lkashjdkjgasfjgaskjdfas'+
    'lkasdjgjhasgdjhasd';
```
