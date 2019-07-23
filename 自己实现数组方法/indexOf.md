```
Array.prototype.indexOf = function(ele){
  if(!ele) return -1  // 没传直接返回-1
  const len = this.length
  for(let i = 0; i < len; i ++){
    if(this[i] === ele){  // 找到返回索引
      return i
    }
  }
  return -1  // 找不到
}
```
