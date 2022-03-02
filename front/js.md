### ES6
1. 数组去重
```
1. [...newSet(array)];
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
