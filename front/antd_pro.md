## point

- **支持 HMR** 模块热替换(hot module replacement)[查看](https://webpack.js.org/concepts/hot-module-replacement/)

## umi

##### Document.ejs 文件就对应index.html umi 约定如果这个文件存在，会作为默认模板

`.umi` 缓存目录

启用 mfsu production 模式时，建议在本地环境将预编译过程完成，并将产物同步到 git，这样在服务器部署的速度将会得到约 **30 倍** 的提升！

- 预编译：默认情况下，预编译将会将依赖构建到 `~/.umi/.cache/.mfsu` 下。并且使用了 webpack 缓存，减少再次编译依赖的时间。

非编译时比如非常流行的 create-react-app，把源码简单直接地交给 webpack 就完成使命；编译时框架则会自己加很多戏，比如拿到源码后做 ast 分析，拿到依赖图谱，做检查，生成临时文件，等等，最后把编译后的源码交给 webpack，这中间的很多事，本来是需要开发者手动处理或编码的。

## dva 对于绝大多数不是特别复杂的场景来说，**目前可以被 Hooks 取代**

> Elm 专注于Web前端的纯函数式语言

- State 数据，通常为一个 JavaScript 对象，操作的时候每次都要当作不可变数据（immutable data）来对待，保证每次都是全新对象，没有引用关系，这样才能保证 State 的独立性，便于测试和追踪变化。
- Action 行为，一个普通 JavaScript 对象，它是改变 State 的唯一途径。
- dispatch，一个用于触发 action 改变 State 的函数。
- Reducer 描述如何改变数据的纯函数，接受两个参数：已有结果和 action 传入的数据，通过运算得到新的 state。
- Effects（Side Effects） 副作用，常见的表现为异步操作。dva 为了控制副作用的操作，底层引入了**[redux-sagas](https://link.zhihu.com/?target=http%3A//superraytin.github.io/redux-saga-in-chinese)**做异步流程控制，由于采用了**[generator 的相关概念](https://link.zhihu.com/?target=http%3A//www.ruanyifeng.com/blog/2015/04/generator.html)**，所以将异步转成同步写法，从而将 effects 转为纯函数。
- Connect 一个函数，绑定 State 到 View

## 页面代码结构

