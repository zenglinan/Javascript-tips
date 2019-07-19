```
Array.prototype.some = function(fn){
  const len = this.length
  let result = false
  for(let i = 0; i < len; i ++){
    result = fn.call(undefined, this[i], i, this)
    if(result) return true
  }
  return false
}
```
