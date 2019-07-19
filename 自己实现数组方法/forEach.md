```
Array.prototype.forEach = function(fn){
  const len = this.length
  for(let i = 0; i < len; i ++){
    if(i in this){  // 如果有第i项
      fn.call(undefined, this[i], i, this)  // 跟原生方法一样，this指向window。提供元素，索引，原数组三个参数
    }
  }
}
```
