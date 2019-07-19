```
Array.prototype.map = function(fn){
  const len = this.length
  let result = []
  for(let i = 0; i < len; i ++){
    result[i] = fn.call(undefined, this[i], i, this)  // 将回调的返回值存入新数组
  }
  return result
}
```
