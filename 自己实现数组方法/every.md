```
Array.prototype.every = function(fn){
  const len = this.length
  let result = true
  for(let i = 0; i < len; i ++){
    result = fn.call(undefined, this[i], i, this)
    if(!result) return false  // 一旦发现result为false，返回false
  }
  return true  // 全部通过返回true
}
```
