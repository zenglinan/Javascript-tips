```
Array.prototype.concat = function(){
  const len = arguments.length
  let arr = []
  Object.assign(arr, this)  // 深拷贝
  for(let i = 0; i < len; i ++){
    if(arguments[i] instanceof Array){  // 是数组就拆解
      for(let j = 0, argArrLen = arguments[i].length; j < argArrLen; j ++){
        arr.push(arguments[i][j])
      }
    }else {  // 其他都直接push
      arr.push(arguments[i])
    }
  }
  return arr
}
```
