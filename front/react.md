> **dva** 是一个基于 Redux 的 轻量级数据流方案,这个有点像vuex，概念来自 elm，支持 side effects、热替换、动态加载、react-native、SSR 等，已在生产环境广泛应用

## Tips：

- 如无必要 勿增实体 沿用es6
- **所有 React 组件都必须像纯函数一样保护它们的 props 不被更改。**
- jsx 代码 render函数里面 html正常写 js要加{}
- react 和 vue 区别 浅析： react：还是使用js编写 react作为助手 提供工具帮助 直接面对js| vue：直接面对vue 写vue代码   直接面对html
- jsx =js + xml babel 将jsx编译为js代码 最后给浏览器渲染执行
- vsc 插件 快捷方式 生成组件代码 rcc
- 单向数据绑定
- 箭头函数 this指向 指向上一层this
- <React.StrictMode> <App/></> 打开严格模式
- 重点 修正this指向、
- for循环遍历 不可以用index 删除调换位置 一般后端给id
- 大多数 React 应用只会调用一次 `root.render()`
- 阻止组件渲染 可以让 `render` 方法直接返回 `null`，而不进行任何渲染 但不影响组件中的生命周期函数 

## react 编码哲学

> 最好将渲染 UI 和添加交互这两个过程分开 ，编写一个应用的静态版本时，往往要编写大量代码，而不需要考虑太多交互细节；添加交互功能时则要考虑大量细节，而不需要编写太多代码。

> *props* 是父组件向子组件传递数据的方式。即使你已经熟悉了 *state* 的概念，也**完全不应该使用 state** 构建静态版本。state 代表了随时间会产生变化的数据，应当仅在实现交互时使用

## 知识点

#### 1. [FAQ: state 与 props 的区别是什么？](https://zh-hans.reactjs.org/docs/faq-state.html#what-is-the-difference-between-state-and-props)

#### 2. antd: 

## 组件

>  单一功能原则
>
> 组件，从概念上类似于 JavaScript 函数。它接受任意的入参（即 “props”），并返回用于描述页面展示内容的 React 元素
>
> ui的 Photoshop\figma 的图层名称可能最终就是你编写的 React 组件的名称！UI（或者说组件结构）便会与数据模型一一对应

ES6 class Test 类名大写

### 类组件 

```
class extends father{
}
```

### 函数式组件

```
function() {
}
```

hooks 状态管理 无状态组件

## 事件绑定 事件处理

> onClick
>
> 方法不加（）加了会立即执行
>
> React 的事件对象 `e` 会被作为第二个参数传递

```
<div onClick={this.fun1}></div> //不可加（） 且this指向会指向react undefind 
<div onClick={this.fun1.bind(this)}></div>
<div onClick={(param,param1)=>{
	this.fun1(param,param1)
}}></div>
fun1(evt) {
	evt事件对象
}
```

#### 改变this指向方案

### 1. call（） 改变this指向，并且自动执行函数

```
obj.fun1.call(fun2)
```

### 2.apply（）改变this指向，并且自动执行函数

```
obj.fun1.apple(fun2)
```

### 3.bind（）改变this指向，并且手动执行函数

```
obj.fun1.bind(fun2)()
```

## Ref 绑定元素

> ref绑在标签 获取的是真实dom元素
>
> ref绑在组件上面 获取的是组件对象

``` 
let ref1 = React.createRef()
<input ref={ref1}/>
```

## 状态

> 组件内部数据载体
>
> state setState修改状态
>
> vue vuex
>
> 状态就是 UI 中的动态数据
>
> 父子通信较简单，而深层级、远距离组件的通信，则依赖于 "状态提升" + props 层层传递
>
> 不要直接修改state中的值 state监听不到
>
> this.setState() 接受一个对象{}或函数
>
> 单向向下数据流

### 写法：

``` 
state = {
}
constructor() {
super()
this.state = {
}
}
  this.setState({
        posts: response.posts
      });
```

## jsx

## 生命周期

- `componentDidMount()` 方法会在组件已经被渲染到 DOM 中后运行，所以，最好在这里设置计时器
- `componentWillUnmount()` 生命周期方法中清除计时器：
- 使用 `this.setState()` 来时刻更新组件 state：

## 表单 使用受控组件 （动态绑定组件）

## 状态提升

将状态提升至就近父组件 有props传入各子组件 子组件改变值后 由子组件调用父组件传入的函数 返回

## 组合&继承 不用继承

推荐组合 就是vue中slot插槽

## 特性

import动态加载 

# Context

Context 提供了一种在组件之间共享此类值的方式，而不必显式地通过组件树的逐层传递 props。

## 错误边界 try catch 

固定标签包裹组件 发生错误 展示默认组件 并打印错误

## 转发 refs 到 DOM 组件

父组件 创建ref对象并放在自身ref中 将其通过转发向内层传递 并挂在需要的子组件上 这样就可以通过ref直接获取改组件

```
const ref = React.createRef();
<FancyButton ref={ref}>Click me!</FancyButton>;
const FancyButton = React.forwardRef((props, ref) => (
  <button ref={ref} className="FancyButton">
    {props.children}
  </button>
));
```

### Fragments返回一个子元素列表

```
render() {
    return (
      <React.Fragment>        <td>Hello</td>
        <td>World</td>
      </React.Fragment>    );
  }
  //简写
  return (
      <>
        <td>Hello</td>
        <td>World</td>
      </>
    );
```

## 高阶组件

是一种基于 React 的组合特性而形成的设计模式

> **高阶组件是参数为组件，返回值为新组件的函数。**

用于 组件抽象  之前用mixin 现在弃用



## 状态管理

content  redux dva

## 类型检查

使用 PropTypes 进行类型检查

也可以使用 Flow 和TypeScript进行类型检查

## Model 跟随路由动态加载

```javascript
function RouterConfig({ history, app }) {
  const routes = [
    {
      path: '/',
      name: 'IndexPage',
      getComponent(nextState, cb) {
        require.ensure([], (require) => {
          registerModel(app, require('./models/dashboard'));
          cb(null, require('./routes/IndexPage'));
        });
      },
    },
    {
      path: '/users',
      name: 'UsersPage',
      getComponent(nextState, cb) {
        require.ensure([], (require) => {
          registerModel(app, require('./models/users'));
          cb(null, require('./routes/Users'));
        });
      },
    },
  ];
  return <Router history={history} routes={routes} />;
}
```
