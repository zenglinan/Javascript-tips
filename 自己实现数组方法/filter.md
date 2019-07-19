```
Array.prototype.filter = function(fn){
  const len = this.length
  let result = []
  for(let i = 0; i < len; i ++){
    if(i in this){  // 判断是否为空元素的索引
      fn.call(undefined, this[i], i, this) && (result.push(this[i]))
    }
  }
  return result
}
```
