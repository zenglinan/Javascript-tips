```
Array.prototype.reduce = function(fn){
  const len = this.length
  let result = this[0]  // 先把第一个元素放进去作为pre
  for(let i = 0; i < len - 1; i ++){  // i<len-1，这样取i+1刚好不会溢出
    result = fn.call(undefined, result, this[i+1])  // this不传，传入累加的结果(result)和下一位元素的值
  }
  return result
}
```
