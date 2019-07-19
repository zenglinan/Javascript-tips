```
Array.prototype.join = function(char){
  const len = this.length  // this为数组
  let result = this[0] || ''  // 取出第一位
  for(var i = 1; i < len; i ++){  // 循环累加，记得做空判断
    result += (char + (this[i] || ''))
  }
  return result
}
```
