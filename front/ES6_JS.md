## ES6
### 常用技巧

#### 1. 获取数组最后一个元素

```
arr.slice(-1) 不改变原数组 得到的是数组
arr.pop() 改变原数组
arr[arr.length-1]
```

#### 2. js数组对象 深拷贝

```
[...arr]
let arr1 = arr.slic
```

#### 3. 数组去重

```
1. [...new Set(array)];
2. Array.from(new Set(array))
Array.form:可以把类数组对象(array-like obj)和可迭代对象(iterable objects -- eg:Map or Set)转为常规数组
3. 数组中对象去重
objTrim: function(){
    let obj = {};
    this.test= this.test.reduce((cur,next) => {
         obj[next.imageId] ? "" : obj[next.imageId] = true && cur.push(next);
         return cur;
    },[]);
   return this.test;
},
```

#### 4. 转换成数字

> parseInt()  + "123"  如果转换的内容不是数字 则返回NaN NaN加入任何运算 均为NaN 
>
> isNaN() 判断是否

### 模块化导入导出

>  import Sth from "../../.js" 首字母大写

### class继承 

### 类型

#### 1. symbol 新增类型

#### 2. String 方法

```
"hello".charAt(0); // "h"
"hello, world".replace("world", "mars"); // "hello, mars"
"hello".toUpperCase(); // "HELLO"
```

#### 3.Boolean

> `false`、`0`、空字符串（`""`）、`NaN`、`null` 和 `undefined` 被转换为 `false`

### 循环

#### while 和do while

```
while (true) {
  // 一个无限循环！
}
var input;
do {
  input = get_input();
} while (inputIsNotValid(input))

```

#### for循环

##### 1. for of \for in

```
for (let value of array) {
  // do something with value
}
```

和 [`for`...`in`](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Statements/for...in) ：

```
for (let property in object) {
  // do something with object property
}
```

###  对象 Object 名称-值

> Object，可以简单理解成“名称-值”对（而不是键值对：现在，ES 2015 的映射表（Map），比对象更接近键值对）
>
> “名称”部分是一个 JavaScript 字符串，“值”部分可以是任何 JavaScript 的数据类型——包括对象

##### 1. 对象的属性可以通过链式（chain）表示方法进行访问：

```
obj.details.color; // orange
obj["details"]["size"]; // 12
```

### 数组

##### 1. a.toString() 返回一个包含数组中所有元素的字符串，每个元素通过逗号分隔。

##### 2.a.join(sep) 返回一个包含数组中所有元素的字符串，每个元素通过指定的 `sep` 分隔。

| `a.slice(start, end)`                                | 返回子数组，以 `a[start]` 开头，以 `a[end]` 前一个元素结尾。 |
| ---------------------------------------------------- | ------------------------------------------------------------ |
| `a.sort([cmpfn])`                                    | 依据可选的比较函数 `cmpfn` 进行排序，如果未指定比较函数，则按字符顺序比较（即使被比较元素是数字）。 |
| `a.splice(start, delcount[, item1[, ...[, itemN]]])` | 从 `start` 开始，删除 `delcount` 个元素，然后插入所有的 `item`。 |
| `a.unshift(item1[, item2[, ...[, itemN]]])`          | 将 `item` 插入数组头部，返回数组新长度（考虑 `undefined`）。 |

### 函数

函数实际上是访问了函数体中一个名为 [`arguments`](https://developer.mozilla.org/zh-CN/docs/Web/JavaScript/Reference/Functions_and_function_scope/arguments) 的内部对象，这个对象就如同一个类似于数组的对象一样，包括了所有被传入的参数

```
function add() {
    var sum = 0;
    for (var i = 0, j = arguments.length; i < j; i++) {
        sum += arguments[i];
    }
    return sum;
}

add(2, 3, 4, 5); // 14
```

我们可以使用[剩余参数](https://developer.mozilla.org/zh-CN/docs/Web/JavaScript/Reference/Functions/Rest_parameters)来替换arguments的使用

```
function avg(...args) {
  var sum = 0;
  for (let value of args) {
    sum += value;
  }
  return sum / args.length;
}
avg(2, 3, 4, 5); // 3.5
```

##### 1.★ [apply()](https://developer.mozilla.org/zh-CN/docs/Web/JavaScript/Reference/Global_Objects/Function/apply)

##### 2.★ call()

### 原型链

Person.prototype

