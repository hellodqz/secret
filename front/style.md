## css

### 1. common

1. div > span 选择div直接下一级中的span
   div span 选择div下所有span
2. 垂直居中
   父元素display：flex 子节点 align-self:center; 

### 2. 引入方式

#### 1.写在<style></style>标签里，一般放在head <title></title>标签下面

#### 2.link 

### 3.选择器

#### 1. [通配选择器](https://developer.mozilla.org/zh-CN/docs/Web/CSS/Universal_selectors) \* { }

#### 2. [选择器列表](https://developer.mozilla.org/zh-CN/docs/Learn/CSS/Building_blocks/Selectors#选择器列表) 

​		h1, .class1 {} AT: 选择器列表中 任何一个语法有错 均无效

#### 3. 类型（标签）选择器、类选择器class、id选择器#id1

#### 4. [标签属性选择器](https://developer.mozilla.org/zh-CN/docs/Learn/CSS/Building_blocks/Selectors#标签属性选择器) 

a[title] { } a[href="https://example.com"] { }

#### 5. [伪类与伪元素](https://developer.mozilla.org/zh-CN/docs/Learn/CSS/Building_blocks/Selectors#伪类与伪元素) 

用来样式化一个元素的特定状态 a:hover { } ，`::first-line`是会选择一个元素（下面的情况中是`<p>`）中的第一行 p::first-line { }

#### 6. [运算符](https://developer.mozilla.org/zh-CN/docs/Learn/CSS/Building_blocks/Selectors#运算符)

```
article > p { } 初代子元素
```



#### 7. 一览表

| 器                                                           | 示例                | 学习CSS的教程                                                |
| :----------------------------------------------------------- | :------------------ | :----------------------------------------------------------- |
| [类型选择器](https://developer.mozilla.org/zh-CN/docs/Web/CSS/Type_selectors) | `h1 { }`            | [类型选择器](https://developer.mozilla.org/zh-CN/docs/user:chrisdavidmills/CSS_Learn/CSS_Selectors/Type_Class_and_ID_Selectors#Type_selectors) |
| [通配选择器](https://developer.mozilla.org/zh-CN/docs/Web/CSS/Universal_selectors) | `* { }`             | [通配选择器](https://developer.mozilla.org/zh-CN/docs/user:chrisdavidmills/CSS_Learn/CSS_Selectors/Type_Class_and_ID_Selectors#The_universal_selector) |
| [类选择器](https://developer.mozilla.org/zh-CN/docs/Web/CSS/Class_selectors) | `.box { }`          | [类选择器](https://developer.mozilla.org/zh-CN/docs/user:chrisdavidmills/CSS_Learn/CSS_Selectors/Type_Class_and_ID_Selectors#Class_selectors) |
| [ID选择器](https://developer.mozilla.org/zh-CN/docs/Web/CSS/ID_selectors) | `#unique { }`       | [ID选择器](https://developer.mozilla.org/zh-CN/docs/user:chrisdavidmills/CSS_Learn/CSS_Selectors/Type_Class_and_ID_Selectors#ID_Selectors) |
| [标签属性选择器](https://developer.mozilla.org/zh-CN/docs/Web/CSS/Attribute_selectors) | `a[title] { }`      | [标签属性选择器](https://developer.mozilla.org/zh-CN/docs/User:chrisdavidmills/CSS_Learn/CSS_Selectors/Attribute_selectors) |
| [伪类选择器](https://developer.mozilla.org/zh-CN/docs/Web/CSS/Pseudo-classes) ：指定要选择的元素的特殊状态 | `p:first-child { }` | [伪类](https://developer.mozilla.org/zh-CN/docs/User:chrisdavidmills/CSS_Learn/CSS_Selectors/Pseuso-classes_and_Pseudo-elements#What_is_a_pseudo-class) |
| [伪元素选择器](https://developer.mozilla.org/zh-CN/docs/Web/CSS/Pseudo-elements) | `p::first-line { }` | [伪元素](https://developer.mozilla.org/zh-CN/docs/User:chrisdavidmills/CSS_Learn/CSS_Selectors/Pseuso-classes_and_Pseudo-elements#What_is_a_pseudo-element) |
| [后代选择器](https://developer.mozilla.org/zh-CN/docs/Web/CSS/Descendant_combinator) | `article p`         | [后代运算符](https://developer.mozilla.org/zh-CN/docs/User:chrisdavidmills/CSS_Learn/CSS_Selectors/Combinators#Descendant_Selector) |
| [子代选择器](https://developer.mozilla.org/zh-CN/docs/Web/CSS/Child_combinator) | `article > p`       | [子代选择器](https://developer.mozilla.org/zh-CN/docs/User:chrisdavidmills/CSS_Learn/CSS_Selectors/Combinators#Child_combinator) |
| [相邻兄弟选择器](https://developer.mozilla.org/zh-CN/docs/Web/CSS/Adjacent_sibling_combinator) 当第二个元素*紧跟在*第一个元素之后，并且两个元素都是属于同一个父`元素`的子元素，则第二个元素将被选中 | `h1 + p`            | [相邻兄弟](https://developer.mozilla.org/zh-CN/docs/User:chrisdavidmills/CSS_Learn/CSS_Selectors/Combinators#Adjacent_sibling) |
| [通用兄弟选择器](https://developer.mozilla.org/zh-CN/docs/Web/CSS/General_sibling_combinator) | `h1 ~ p`            | [通用兄弟](https://developer.mozilla.org/zh-CN/docs/User:chrisdavidmills/CSS_Learn/CSS_Selectors/Combinators#General_sibling) |

### 继承

#### CSS 为控制继承提供了四个特殊的通用属性值。每个css属性都接收这些值。

1. [`inherit`](https://developer.mozilla.org/zh-CN/docs/Web/CSS/inherit) 设置该属性会使子元素属性和父元素相同。实际上，就是 "开启继承".
2. [`initial`](https://developer.mozilla.org/zh-CN/docs/Web/CSS/initial) 设置属性值和浏览器默认样式相同。如果浏览器默认样式中未设置且该属性是自然继承的，那么会设置为 `inherit` 。
3. [`unset`](https://developer.mozilla.org/zh-CN/docs/Web/CSS/unset) 将属性重置为自然值，也就是如果属性是自然继承那么就是 `inherit`，否则和 `initial`一样

### 4. 常用技巧 

#### 1.display

#### 2. 清除浮动



#### 3.flex布局

#### 4.grid格栅布局

#### 5. table布局

#### 6. 背景图片 自适应

```
1. 小图重复 background-repeat
2. 大图平铺 background-size 设置长度或百分比值
3. background-size: contain盒子包含图片 、cover图片包含盒子 
4. background-position: top center 定位图片到盒子位置 （0.0）左上角
```

#### 7.溢出 overflow

#### 8. 尺寸单位

| 单位   | 相对于                                                       |
| :----- | :----------------------------------------------------------- |
| `em`   | 在 font-size 中使用是相对于父元素的字体大小，在其他属性中使用是相对于自身的字体大小，如 width |
| `ex`   | 字符“x”的高度                                                |
| `ch`   | 数字“0”的宽度                                                |
| `rem`  | 根元素的字体大小                                             |
| `lh`   | 元素的line-height                                            |
| `vw`   | 视窗宽度的1%                                                 |
| `vh`   | 视窗高度的1%                                                 |
| `vmin` | 视窗较小尺寸的1%                                             |
| `vmax` | 视图大尺寸的1%                                               |

#### 9.继承与不继承



## sass

## less 

## gulp css打包工具

## web标准

1. html
2. css
3. js
