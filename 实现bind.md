## 实现bind
bind会创建一个新的函数返回, 这个函数被调用的时候, this指向bind的第一个参数, 之后的一系列参数都会传入作为函数的参数<br>
1. 返回一个函数
2. 指定这个函数的this
3. 传入参数的实现
### 1. 实现返回函数和指定this
```
Function.prototype.bind = function(context){
  return () => {  // 返回新函数
    return this.apply(context)  // 新函数内部执行原函数, 并指定this, 将执行结果返回
  }
}
```
### 2. 实现传参
bind的传参机制有点奇特, 它支持分两次传参, 也就是所需参数不用一次传完, 可以分两次传
```
var foo = {value: 1};
function bar(name, age) {
    console.log(this.value);
    console.log(name);
    console.log(age);
}
var bindFoo = bar.bind(foo, 'daisy');  // 实现参数固化, 每次调用barFoo时, 原本所需的第一个参数固定了下来, 只用指定第二个
bindFoo('18');
// 1
// daisy
// 18
```
实现思路: 分别用arguments接收, 然后拼接起来
```
Function.prototype.bind = function(context){
  let arg = Array.from(arguments).slice(1)
  return () => {  // 返回新函数
    let arg2 = Array.from(arguments)
    return this.apply(context, arg.concat(arg2))  // 拼接参数数组返回
  }
}
```
以上就基本实现了bind, 但还差点东西: <br>
1. 如果调用bind的是一个**构造函数**, bind指定的this会**失效**
2. 返回函数的prototype应指向原函数的prototype, 使原型链继承下来
### 3. 实现构造函数的判断
因为需要获取到实例的this, 所以这里就不用箭头函数了
```
Function.prototype.bind = function(context){
  let _this = this  // 这里的this指向调用bind的函数
  let arg = Array.from(arguments).slice(1)
  let bindFn = function(){
  let arg2 = Array.from(arguments)
    // 只需判断this的原型是否为返回函数.prototpye即可
    // 如果返回函数被用作构造函数, 内部的this指向实例, this.__proto__ === bindFn.prototype, 下面三元表达式结果为true, 此时不改变this指向
    // 如果返回函数被用作普通函数, 内部this指向window, this.__proto__ === Window.prototype, 下面三元表达式结果为false, 将this绑定为指定的context
    return _this.apply(this instanceof bindFn ? this : context, arg.concat(arg2))
  }
  return bindFn
}
```



参考: https://github.com/mqyqingfeng/Blog/issues/12
