```
Array.prototype.slice = function(fromIndex, toIndex){
  
  if(arguments.length === 0) return this  // 一个参数都不传
  let result = []
  const len = this.length

  fromIndex = (fromIndex + len) % len  // 将负索引转为对应正索引
  if(!toIndex) return [this[fromIndex]]  // 只传第一个参数
  toIndex = (toIndex < len) ? (toIndex + len) % len : len  // 判断toIndex是否超出数组最大索引
  for(let i = fromIndex; i < toIndex; i ++){
    result.push(this[i])
  }
  return result
}
```
