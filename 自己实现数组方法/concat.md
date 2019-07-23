```
Array.prototype.concat = function(){
  const len = arguments.length
  let arr = []
  Object.assign(arr, this)
  for(let i = 0; i < len; i ++){
    if(arguments[i] instanceof Array){
      for(let j = 0, argArrLen = arguments[i].length; j < argArrLen; j ++){
        arr.push(arguments[i][j])
      }
    }else {
      arr.push(arguments[i])
    }
  }
  return arr
}
```
