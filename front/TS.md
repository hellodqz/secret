## FEATURES

##### type 

##### 在不运行代码的情况下检测代码中的错误称为*静态检查* 

> TypeScript 的编译器检查代码 然后删除类型 生成js代码

##### 因此 JS 语法是合法的 TS

##### 编写是校验报错 但不影响代码运行

## type

> typeof 了解变量类型

##### 联合类型 id: number | string

##### 泛型

## tsc 编译器

## 函数参数

##### 可选属性

```ts
function printName(obj: { first: string; last?: string }) {
  // ...
}
```

> 从可选属性中*读取*数据时，您必须`undefined`在使用它之前进行检查 

```
obj.last !== undefined
```

## 类型

##### 类型别名 && 接口声明 （首选）

```
type Point = {
  x: number;
  y: number;
};
type ID = number | string; //联合类型别名
```

##### 接口

> *接口声明*是命名对象类型的另一种方式：

```
interface Point {
  x: number;
  y: number;
}
```

##### 区别

type  只能通过交叉点扩展类型 别名创建后不能添加新属性

```
type Animal = {
  name: string
}
type Bear = Animal & { 
  honey: boolean 
}
const bear = getBear();
bear.name;
bear.honey;
```

interface接口可以

```
interface Animal {
  name: string
}
interface Bear extends Animal {
  honey: boolean
}
const bear = getBear() 
bear.name
bear.honey
```

##### 类型断言 as

```
as
const myCanvas = document.getElementById("main_canvas") as HTMLCanvasElement;
//尖括号  tsx不能用
const myCanvas = <HTMLCanvasElement>document.getElementById("main_canvas");
```

类型断言 强制转换 先转any或unknown 再转类型

```
const a = (expr as any) as T;
```

##### 文字类型  类似枚举字符串 *特定*的字符串和数字

```
function printText(s: string, alignment: "left" | "right" | "center") {
  // ...
}
printText("Hello, world", "left");
printText("G'day, mate", "centre");
Argument of type '"centre"' is not assignable to parameter of type '"left" | "right" | "center"'
```

##### `null`和`undefined`

> JavaScript 有两个原始值用于表示不存在或未初始化的值：`null`和`undefined`.

strictNullChecks on 打开空值检查

##### 非空断言运算符（后缀`!`）

##### 枚举 

##### 兜底 收窄 类型保护 typeof 

##### typeof注意事项 

typeof判断数组 通常用 typeof strs === "object" 强调数组是对象 

```
function printAll(strs: string | string[] | null) {
  if (typeof strs === "object") {
    for (const s of strs) {
Object is possibly 'null'.
      console.log(s);
    }
  } else if (typeof strs === "string") {
    console.log(strs);
  } else {
    // do nothing
  }
}
```

##### 不要使用if(a==0)判断 改用 Boolean(a) 和 ！！a 强制转换为Boolean

##### 利用 in 判断参数中是都含有某属性

```
type Fish = { swim: () => void };
type Bird = { fly: () => void };
function move(animal: Fish | Bird) {
  if ("swim" in animal) {
    return animal.swim();
  }
  return animal.fly();
}
```

##### instanceof 判断类型

##### 类型谓词

```
function isFish(pet: Fish | Bird): pet is Fish { //is 是作为fish类型fan'hui'o
  return (pet as Fish).swim !== undefined;
}
```

## 函数 泛型函数

##### 通用函数

```
function firstElement<Type>(arr: Type[]): Type | undefined {
  return arr[0];
}
// s is of type 'string'
const s = firstElement(["a", "b", "c"]);
// n is of type 'number'
const n = firstElement([1, 2, 3]);
// u is of type undefined
const u = firstElement([]);
```

##### 约束

```
function longest<Type extends { length: number }>(a: Type, b: Type) {
  if (a.length >= b.length) {
    return a;
  } else {
    return b;
  }
}
// longerArray is of type 'number[]'
const longerArray = longest([1, 2], [1, 2, 3]);
// longerString is of type 'alice' | 'bob'
const longerString = longest("alice", "bob");
// Error! Numbers don't have a 'length' property
const notOK = longest(10, 100);
Argument of type 'number' is not assignable to parameter of type '{ length: number; }'.
```

##### 指定类型参数

```
const arr = combine<string | number>([1, 2, 3], ["hello"]);
```

##### 可选参数 ?

```
function f(x?: number) {
}
```

##### 剩余参数 ...args





##### 参数默认值 function f(x = 10) {}

##### 函数重载  尽可能使用联合类型 而不是重载

> 只能调用签名 不能调用实现签名  
>
> 实现签名必须兼容所有重载函数 类似泛型 
>
> 调用签名 必须确定唯一重载

```
function makeDate(timestamp: number): Date;
function makeDate(m: number, d: number, y: number): Date;
function makeDate(mOrTimestamp: number, d?: number, y?: number): Date {
  if (d !== undefined && y !== undefined) {
    return new Date(y, mOrTimestamp, d);
  } else {
    return new Date(mOrTimestamp);
  }
}
const d1 = makeDate(12345678);
const d2 = makeDate(5, 5, 5);
const d3 = makeDate(1, 3);
No overload expects 2 arguments, but overloads do exist that expect either 1 or 3 arguments.
```

## 其他类型

##### viod和undefined

##### object和Object（尽可能不用）

所有的非基础类型都为object

##### unknow（更安全） 和 any

