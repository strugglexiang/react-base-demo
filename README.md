# react-base-demo
react基础学习时候的demo


## es6 map方法的使用
- map() 方法返回一个新数组，数组中的元素为原始数组元素调用函数处理后的值。
- map() 方法按照原始数组元素顺序依次处理元素。
- 注意： map() 不会对空数组进行检测。
- 注意： map() 不会改变原始数组。
语法 
```
array.map(function(currentValue,index,arr), thisValue)
currentValue 	必须。当前元素的值
index 可选。当期元素的索引值
arr 可选。当期元素属于的数组对象
thisValue	可选。对象作为该执行回调时使用，传递给函数，用作 "this" 的值。
如果省略了 thisValue ，"this" 的值为 "undefined"
```

## npm i -g live-serve 
- live-server --port=4000


##  label标签的使用
- https://developer.mozilla.org/en-US/docs/Web/HTML/Element/label
点击标签就是点击input框
```
1.
<label>Click me <input type="text"></label>
2.
<label for="username">Click me</label>
<input type="text" id="username">
```

##  bind方法的使用 
https://developer.mozilla.org/zh-CN/docs/Web/JavaScript/Reference/Global_Objects/Function/bind

###创建绑定函数
1.创建绑定函数
```
this.x = 9; 
var module = {
  x: 81,
  getX: function() { return this.x; }
};

module.getX(); // 返回 81

var retrieveX = module.getX;
retrieveX(); // 返回 9, 在这种情况下，"this"指向全局作用域

// 创建一个新函数，将"this"绑定到module对象
// 新手可能会被全局的x变量和module里的属性x所迷惑
var boundGetX = retrieveX.bind(module);
boundGetX(); // 返回 81
```

2.bind()的另一个最简单的用法是使一个函数拥有预设的初始参数。
这些参数（如果有的话）作为bind()的第二个参数跟在this（或其他对象）后面，
之后它们会被插入到目标函数的参数列表的开始位置，传递给绑定函数的参数会跟在它们的后面。
```
unction list() {
  return Array.prototype.slice.call(arguments);
}

var list1 = list(1, 2, 3); // [1, 2, 3]

// Create a function with a preset leading argument
var leadingThirtysevenList = list.bind(undefined, 37);

var list2 = leadingThirtysevenList(); // [37]
var list3 = leadingThirtysevenList(1, 2, 3); // [37, 1, 2, 3]
```
3.bind 是固定某个函数的参数和this，返回另外一个函数。
call 和 apply是指定this和参数调用这个函数，立即执行这个函数。
call apply 的区别是他们指定参数的方式不同。
```
function fn(a,b){
    console.log(this);
    console.log(a);
    console.log(b);
}
// bind(this,args...)
bf = fn.bind("Bind this",10); // 没有任何输出，也就是说没有执行这个函数
bf(); // "Bind this",10,undefined
bf(20);// “Bind this”,10,20
// 原函数不受影响
fn(1,2); //window， 1，2
bf2 = fn.bind("Bind this",1,2);
bf2(); // "Bind this",1,2

// call(this,args...)
fn.call("Call this",1) // "Call this",1,undefined
fn.call("Call this",1,2) // "Call this",1,2

// apply(this,[args])
fn.apply("Apply this",[1]) // "Apply this",1,undefined
fn.apply("Apply this",[1,2]) // "Apply this",1,2
```