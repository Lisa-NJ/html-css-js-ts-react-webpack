Window：requestAnimationFrame() 
	- https://developer.mozilla.org/zh-CN/docs/Web/API/window/requestAnimationFrame
Performance: now() 
	- 

// Object.defineProperty - 给对象添加属性
get set

console.dir(Vue)

### Agile

Lean Startup

### SOLID 原则

**S** - Single Responsibility 单一职责

**O** - Open Close 开闭

L - Liskov Substitution 里氏替换

I - Interface Segregation 接口隔离

 **D** - Dependency Injection 依赖反转

举例：taxTable 计算税额

自我怀疑、自我否定、自我学习

好代码写三遍！

好代码：Readable、Maintainable、Reusable

airbnb / javascript -- gitHub 什么是好代码

**编程语言两大类**

强类型编译语言：Java、C、C++、C#、.net 

	- compiled software: Compile and run
	- C++ 源码 --> 编译 -->010101
	- Java runtime 编译 

弱类型脚本语言：JavaScript、Ruby、php、python

​	- 边写边运行：会尝试解释运行一切能够运行的东西 runtime

Java 8 /  16

Python 3.7

Php 8

CSS 3

HTML 5

JavaScript 社区维护

ECMA 欧洲计算机制造协会 - propose 新功能

**解释 JS**

浏览器（chrome 兼容性好稳定，FF 性能好，Edge 性能更好，IE11，360安全，QQ浏览器， Safari 省电）

解释环境（我在哪里解释，谁来解释）

浏览器里面运行的

JS --> 网页互动服务的 --> 网页环境里面

命令式：JS - 重过程轻结果

声明式：SQL、react - 重结果轻过程

### 需要补充的知识点：

CanIUse.com - 可以查某用法各浏览器的支持情况

W3school 或 MDN - 看文档要看浏览器的兼容性

CSS 与 浏览器 之间也有支持性的问题 

18w 以上 表示成：

```js
min:180000, max: Number.POSITIVE_INFINITY
```

debugger

try ... catch

赛扬、奔腾 处理器

从什么时候开始不再关心性能了？

JS 实现了 读写分离

```js
/* duck test principle (DTP)
JS 做判断时，执行鸭子原则判断标准
当一个东西，长得像、叫声像、走路像鸭子，那么它就是鸭子 => truthy + falsy
{} [] function(){} 不是 falsy，因为包括了对象所有的基本功能
*/
if(x=2){
	console.log('Alice'); //不报错 输出 Alice
}
//先 x=2, 再 if(x)

1=='1' //true
{}==={} //false
{}=={} //false
//==>在普通类型比较中，严格相等可以理解为普通相等+类型相等；
//在比较对象时，严格相等是内存地址相等
```

**Logic Gates 或非门** -- 做短路计算

true && anything --> anything

false && anything --> false

true || anything --> true

false || anythign --> anything

```jsx
//用户已经登陆 && 欢迎消息
var 特殊欢迎消息 = 用户.充值金额>10w && '热烈欢迎，撒花';
var 一般欢迎消息 = '欢迎上线';
var 欢迎消息 = 特殊欢迎消息 || 一般欢迎消息;
var 消息 = 用户 && 欢迎消息

显示Dropdown //true
显示Dropdown && (<div>Dropdown</div>)
```

function 本质上 是 object，所以可以做所有 object 的基本操作

```js
// 匿名函数
var sum = function(a, b){ return a + b; }
```

字典数据 用 对象 key - value 来表示



this 的指向是在调用时根据上下文动态确定的 - 谁调用，指向谁

this 不会被赋值

- 在函数体中，简单调用该函数时，严格模式下 this 绑定到 undefined，否则绑定到全局对象 window（browser）/ global（node）
- 由上下文对象（调用者）调用，绑定在该对象上；
- 

```js
class Person() {
  constructor(name) {
    this.name = name;
  }
  
  getName() {
    return this.name;
  }
}
var alice = new Person('Alice');
var bob = new Person('Bob');

alice.getName(); // Alice
bob.getName(); // Bob

alice.brother = bob;

alice.brother.getName(); // Bob

alice.whatEver = alice.brother.getName;
alice.whatEver(); // Alice
```

字节面试题

```js
var text = 'o0';

var o1 = {
  text: 'o1',
  fn: function(){
    return this.text;
  },
};

var o2 = {
  text: 'o2',
  fn: function(){
    return o1.fn();
  },
};

var o3 = {
  text: 'o3',
  fn: function() {
    o2.fn = function() {
      return this.text;
    }
    return o2.fn();  // o2 是调用者，this 指向 o2
  },
};

var o4 = {
  text: 'o4',
  fn: function() {
    o2.fn = function() {
      return this.text;
    }
    return o2.fn;  
  },
};
console.log(o1.fn()); // o1
console.log(o2.fn()); // o1
console.log(o3.fn()); // o2 *** 
console.log(o4.fn()); // function() { return this.text; }
console.log(o4.fn()()); // o0
```



### JAVASCRIPT

dynamic,   weakly typed  脚本语言，推演运算 

**Statements**

JS 程序的执行单位为行（line），也就是一行一行地执行。一般情况下，每一行就是一个语句；

- Semicolons - 语句以分号结束，一个分号就表示一个语句结束；多个语句可以写在一行内；
- White Space - 语句中的额外空格会被忽略 

**JS 的两次运行**：

​	第一次运行：变量提升 + 分配内存地址；

​	第二次运行：使用内存地址 + 运行结果；



历史：最初是为了在网页中嵌入脚本来对用户输入数据在客户端进行有效性校验

ES4

ES4.6

ES4.9

ES New

ES5 ( ECMA 重组，制定了一系列规范，成立公司 )

ES6 *

ES2018

ES7

ES8

ES2019

ES9



开发工具：VSCode + Live Server

JS引擎 的工作方式：

先解析代码，获取所有被声明的变量，然后再一行一行地运行

==> 所有的变量声明语句，都会被提升到代码的头部，也即 hoisting

错误分两种：

1.低级错误（语法解析错误 - 比如代码中写了中文冒号：）

代码开始执行前会先扫描，如发现低级错误，会报语法错误，一行代码也不会执行；

2.逻辑错误（标准错误，情有可原 - 比如变量没有声明）

js 逻辑错误会引发后续代码终止，但不会影响其它 js 代码块（一组<script>定义的代码块）；

```javascript
const pkg = require('./package.json');

console.log('The dependencies used:');
console.log('  ' + Object.keys(pkg.dependencies).join('\n  '));
console.log();
console.log('The devDependencies used:');
console.log('  ' + Object.keys(pkg.devDependencies).join('\n  '));
```

[JS Array operations]
push    / pop   / lastIndexOf /
unshift / shift / indexOf /  split / splice / length / 
join    / reduce / reduceRight / sort / reverse / 
some    / every  / foreach / 
map     / filter / slice / concat -- pure functions

```javasript
var ary = ['A', 'B', 'C', 'D', 'E']

ary.some(function(item){
 return item==='C'
})

ary.every(function(item){
 return item==='C'
})

ary.foreach(function(val, i){
 console.log(val )
})

ary.map(function(val, i){
 return val + val  
})

ary.filter(function(val, i){
 return val % 2 === 0  
}) 

ary.slice(2, 4)

var ary1 = ['G', 'H']
ar.concat(ary, ary1)

let index = 'abcde'.indexOf('a') //0
index = 'abcde'.indexOf('') //0 ***
```

#### 常见登录鉴权方案

https://cloud.tencent.com/developer/article/1745622
HTTP 是一个无状态协议，所以客户端每次发出请求时，下一次请求无法得知上一次请求所包含的状态数据。
HTTP 提供一个用于权限控制和认证的通用框架。最常用的HTTP认证方案是HTTP Basic Authentication


####  AJAX 编程

Ajax主要的作用：可以部分刷新页面，而不用重新刷新整个网页；

xhr （不常用）， 

jQuery（太大，80%封装DOM），  

axios（对xhr封装，推荐！），

fetch（与xhr平级，不常用，包了两层，兼容性差）

##### XMLHttpReques

需要使用到  JS、xhr-浏览器提供的构造函数、状态码、http等

准备：html文件 空 p 标签，test.txt

JS文件：创建 xhr

用 open() 方法填写请求类型

监听 readyState 的值，用 onreadystatechange() 方法，如果 为 4 表示接收到了 响应，再判断 xhr 状态码，200 表示成功，把 p 标签 内容改为 收到的文本内容 xhr.responseText



```javascript
function print() {
    document.getElementById("demo").innerHTML="RUNOOB!";
}
setTimeout(print, 3000);
//函数 setTimeout 执行之后会产生一个子线程，子线程会等待 3 秒，然后执行回调函数 "print"
```

除了 setTimeout 函数以外，异步回调广泛应用于 AJAX 编程。一个标准的 XMLHttpRequest 对象往往包含多个回调：

```javascript
var xhr = new XMLHttpRequest();
 
//onload 属性是函数，在它请求成功时被调用。
xhr.onload = function () {
  // 输出接收到的文字数据
  document.getElementById("demo").innerHTML=xhr.responseText;
}

//onerror 属性是函数，在它请求失败时被调用。
xhr.onerror = function () {
    document.getElementById("demo").innerHTML="请求出错";
}
 
// 发送异步 GET 请求
xhr.open("GET", "https://www.runoob.com/try/ajax/ajax_info.txt", true); // 配置请求信息
xhr.send();
```

**XMLHttpRequest** 常常用于请求来自远程服务器上的 XML 或 JSON 数据。

开发中不怎么使用，太麻烦！

##### Promise

是 ES6 引入的异步编程的新解决方案，语法上 Promise 是一个构造函数，用来封装异步操作并可以获取其成功或失败的结果；

解决了回调地狱的问题，可进行异步处理并得知任务进度；

Promise、resolve、reject、then、catch、finally

Promise 构造函数：Promise(executor){}

Promise.prototype.then 方法

Promise.prototype.catch 方法

```js
// 实例化 Promise 对象
const p = new Promise(function(resolve, reject){
  setTimeout(function(){
    let data = '数据库中的用户'
    resolve(data) //p 的状态置为成功
    
    //let err = '数据库读取失败'
    //reject(err) //p 的状态置为失败
  }, 1000)
})

// 调用 promise 对象的 then 方法
p.then(function(value){//p 状态为成功时调用
  console.log(value)
}, function(reason){ //p 状态为失败时调用
  console.log(reason)
})
```



Promise 是一个 ECMAScript 6 提供的类，目的是更加优雅地书写复杂的异步任务; 一个 Promise 是一个等待被异步执行的对象，当它执行完成后，其状态会变成 resolved 或者rejected。

Promise 构造函数只有一个参数，是一个函数，这个函数在构造之后会直接被异步运行，所以我们称之为起始函数。起始函数包含两个参数 resolve 和 reject。

当 Promise 被构造时，起始函数会被异步执行；resolve 和 reject 都是函数，其中调用 resolve 代表一切正常，reject 是出现异常时所调用的；

Promise 类有 .then() .catch() 和 .finally() 三个方法，这三个方法的参数都是一个函数，.then() 可以将参数中的函数添加到当前 Promise 的正常执行序列，.catch() 则是设定 Promise 的异常处理序列，.finally() 是在 Promise 执行的最后一定会执行的序列。 .then() 传入的函数会按顺序依次执行，有任何异常都会直接跳到 catch 序列。

**Promise 封装 AJAX 请求**

```js
// 接口地址：https://api.apiopen.top/getJoke

// 原生 AJAX 发请求
//1. 创建对象
const xhr = new XMLHttpRequest();
//2. 初始化
xhr.open('GET', 'https://api.apiopen.top/getJoke')
//3. 发送
xhr.send()
//4. 绑定事件，处理响应结果
xhr.onreadystatechange = function(){
  //判断
  if(xhr.readyState === 4){
    //判断响应状态码 200-299
    if(xhr.status >= 200 && xhr.status < 300){
      //表示 成功
      console.log(xhr.response)
    }else{
      //如果 失败
      console.log(xhr.status)
    }
  }
}

// ----------------------------------------
// 使用Promise 进行封装 - 只需三处修改
// 1⃣️
const p = new Promise((resolve, reject)=>{
  //1. 创建对象
  const xhr = new XMLHttpRequest();
  //2. 初始化
  xhr.open('GET', 'https://api.apiopen.top/getJoke')
  //3. 发送
  xhr.send()
  //4. 绑定事件，处理响应结果
  xhr.onreadystatechange = function(){
    //判断
    if(xhr.readyState === 4){
      //判断响应状态码 200-299
      if(xhr.status >= 200 && xhr.status < 300){
        // 2⃣️
        //表示 成功
        resolve(xhr.response)
      }else{
        //如果 失败
        reject(xhr.status)
      }
    }
  }
})

// 3⃣️
// 指定回调
const result = p.then(function(value){
  console.log(value)
}, function(reason){
  console.error(reason)
})
//-----------------------------------------//Promise.prototype.then 返回结果
const result1 = p.then(function(value){
  console.log(value)
  //1. 非 Promise 类型的属性
  //return 'love'// 不写 return 则为  undefined
  //2. 是 Promise，内部返回的 Promise 的状态决定了 then 方法返回值的 Promise 对象的状态
  return new Promise((resolve,reject)=>{
    resolve('success')
  })
  //3. 抛出错误
  //throw new Error('error!')
  //throw 'error!'
}, function(reason){
  console.warn(reason) //黄色显示
})
console.log(result1) //Promise{}
```

对比上面两者区别：使用 原生 AJAX 发请求，在 回调函数里 处理成功或失败的结果；Promise，在 异步任务的后边 then 方法里面，简洁清晰，也避免了回调地狱

**Promise.prototype.then** - Promise 的 then 方法

如上👆 

then 方法的返回结果是 Promise 对象，对象的状态由回调函数的执行结果来决定

//1. 如果回调函数中返回的结果是 非 Promise 类型的属性，状态为成功，返回值为对象的成功的值

//2. 如果回调函数中返回的结果是是 Promise，内部返回的 Promise 的状态决定了 then 方法返回值的 Promise 对象的状态：

//2-1. 如果内部返回的 Promise 成功，则 then 方法返回的 Promise 对象也成功，值为 内部返回的 Promise 对象成功的值

//2-2. 如果失败，也类似

//3. 抛出错误 - 返回的 Promise 对象状态为失败，失败的值为 抛出的错误值 

==> 因为 then 方法返回 Promise 对象，所以可以链式调用

```js
//链式调用
p.then(value=>{

}, reason=>{

})
.then(value=>{

}, reason=>{

})
```

 另外，then 方法可以只指定一个回调函数作为入参，第二个可省略，变成如下的形式：

```js
//链式调用
p.then(value=>{
	//异步任务 2
})
.then(value=>{
  //异步任务 3
})
```

==>每个回调中可以嵌套一个异步任务，一个一个向前推进，形成链式调用，因此避免了 回调地狱 的现象

**catch 方法**可以理解为 then 方法的语法糖，相当于 then 不指定第一个入参的效果；

如果 return 的是 promise，那么下一个 .then 就会等待 promise 异步；

如果 return 的是 简单的值，那么下一个 .then 会直接执行；

==> return 语句可以把 promise 串起来





##### 参考：

Ajax编程学习视频：Ajax 是什么? 如何创建一个 Ajax？ --技术蛋老师

https://www.bilibili.com/video/BV1jv411P7Hp?from=search&seid=5910765473136513028&spm_id_from=333.337.0.0

《JS权威指南》 &《 JS高级程序设计》

//...待完成-1 ES6 7 8 9 

//...待完成-2 JS高级视频教程 

//参考： [JavaScript 你理解Promise吗](https://www.bilibili.com/video/BV1QV411a7Hu?spm_id_from=333.999.0.0) --技术蛋老师

//参考： [菜鸟教程](https://www.runoob.com/js/js-promise.html)

#### ES6 新特性

JS 解释性语言 源码 --> 解释 --> 解释成 C --> 编译 --> 0010101

浏览器负责解释 JavaScript

##### let、const 块级作用域

{} - 块作用域

const - 常量，必须在声明的同时进行初始化

var、let、const对比

```
ES6 中新增了块级作用域。块作用域由 { } 包括，if语句和for语句里面的{ }也属于块作用域。 

var定义变量，没有块的概念，可以跨块访问，不能跨函数访问，不初始化出现undefined，不会报错。

let定义变量，只能在块作用域里访问，也不能跨函数访问，对函数外部无影响，不存在变量提升，不影响作用域链。

const定义常量，只能在块作用域里访问，也不能跨函数访问，必须在声明的同时进行初始化，而且不能修改；如果是对象或数组，可以修改对象或数组的属性，但不能对整个对象重新赋值；

let a = "hey I am outside";
if(true){
    console.log(a);//Uncaught ReferenceError: a is not defined
    let a = "hey I am inside";
}
变量提升 //...

这里同样抛出了一个错误，认为a没有声明，但是，如果a没有变量提升，执行到console.log时应该是输出全局作用域中的a，而不是出现错误。

这里确实出现了变量提升，而我们不能够访问的原因事实上是因为let的死区（temporal dead zone）设计：当前作用域顶部到该变量声明位置中间的部分，都是该let变量的死区，在死区中，禁止访问该变量。由此，我们给出结论，let声明的变量存在变量提升， 但是由于死区我们无法在声明前访问这个变量.
```

```html
<body>
	<div>
  	<div class='item'></div>
  	<div class='item'> </div>
  </div>
  <script>
		//需求：点击某个按钮，将其颜色改为 pink
		let items = document.getElementByClassName('item')

		for(let i=0; i<items.length; i++){
		  items[i].onclick = function(){
 		    items[i].style.background = 'pink'   
		  }
		}
	</script>
</body>
```

js class 继承

##### 模版字符串 ${...} 

可以 使用 反引号 在字符串里面使用其他变量的值 或者 任意的有返回值的 JS 语句，简化字符串拼接方式；可以在其中使用换行

```javascript
let user = 'Barret'
let age = 15
let a = `${user} who is ${age} is eating`
// `` 既可以包 '' 也可以包 ""

const currency = 'AUD';
const amount = '1000';
const getSymbolByCurrency = (currency)=> ({
  AUD: '$',
  CHY: '¥',
}[currency]);
const pricePerTraveller = `${getSymbolByCurrency(currency)}${amount} Per trav`

// ES6 之前：
"Hello, this is \"Alice\", my name is 'Bob'"
```



##### 解构赋值

使用最多的场景：从对象中 解构出 方法，简化代码

```javascript
let [a, , b] = [1, 2, 3] // a:1 b:3
let { a: c } = { a: 1, b: 2 }// c:1 - 从后面的对象中取出 a 然后 赋给 c

// 数组 也是 对象 
const arr = {0:'Alice', 1:'Bob'};
const arr = ['Alice', 'Bob']; //与上等效 
const {0:name1, 1:name2} = ['Alice', 'Bob'] // name1 = 'Alice'
const [name1, name2] = ['Alice', 'Bob'] 

//与参数默认值结合起来使用 ES6教程 11/68
function connnet({host='127.0.0.1', username, password, port}){
  console.log(host)
  console.log(username)
}
connect({
  host: 'atguigu.com',
  username: 'root',
  password: 'root',
  port: 3306
})

//基本
let [a, b, c] = [1, 2, 3];  //a = 1 b = 2 c = 3
//可嵌套
let [a, [[b], c]] = [1, [[2], 3]]; //a = 1 b = 2 c = 3
//可忽略
let [a, , b] = [1, 2, 3];// a = 1  b = 3
//不完全解构
let [a = 1, b] = []; // a = 1, b = undefined
//剩余运算符
let [a, ...b] = [1, 2, 3];//a = 1  b = [2, 3]
//字符串等
//在数组的解构中，解构的目标若为可遍历对象，皆可进行解构赋值。
//可遍历对象即实现 Iterator 接口的数据。
let [a, b, c, d, e] = 'hello';
// a = 'h' b = 'e' c = 'l' d = 'l' e = 'o'

//解构赋值 中 缺省赋值的使用
const student {
  age: 20,
  courses: [
    { name: 'Learn JS' },
		{ name: 'Giveup JS'}
  ],
}

const { age,
      courses : [
        { name : learnJSName },
        { name : giveupJSName },
        { name : learnPython = 'I love Python' } = {},  //***
      ]
      } = student;

/*
1. {} 解构 对象，[] 解构 数组
2. : 重命名 = 设置默认值
*/
```

##### 对象的简化写法

ES6 允许在大括号里面，直接写入变量和函数，作为对象的属性和方法，写法更简洁；函数可以简写，省略掉 :function；允许在对象属性中进行计算操作：

```js
let name = 'shang'
let change = function(){
   console.log('change')
}
const school = {
  name,
  change,
  improve(){
    console.log('improve')
  },
  // 属性可以使用表达式计算值
  ['change' + name]: true,
}
// 等价于
const school = {
  name: name,
  change: change,
  improve:function(){
    console.log('improve')
  },
  ['changeshang']: true
}
```

##### 箭头函数 Arrow Function ()=>{}

 对比：

一般方法中，this代指全局对象 window
作为对象方法调用，this代指当前对象
作为构造函数调用，this 指代new 出的对象

```js
// 之前的函数声明
let fn = function(){
}

// 箭头函数 语法
let fn1 = (a, b)=>{
  return a+b
}
//调用函数
let result1 = fn1(1, 2)

//1. this 是静态的
function getName(){
  console.log(this.name)
}
let getName2 = ()=>{
  console.log(this.name)
}
// 设置 window 对象的 name 属性
window.name = 'shang'
const school = {
  name: 'guigu'
}

// 直接调用
getName() //shang
getName1() //shang 箭头函数在全局作用域下声明，所以 this 指向window

// call 方法调用
getName.call(school) // guigu, this 发生了改变
getname1.call(school) // shang

//4. 省略写法
let add = (n)=>{
  return n *2
}
// 等价于
let add = n=>{
  return n *2
}
// 等价于
let add = n=>n *2
```

==> 特性：谁定义指向谁

1.没有自己的this，箭头函数的 this 是静态的，始终指向词法作用域，也就是外层调用者obj，也即箭头函数声明时所在作用域下 this 的值

```js
{
  name: 'shang',
  age: 14,
  getName: function(){
    this.name //此时 this 指向 {name,age,...} 对象
  }
  getAge: ()=>{
    this.age //有错：此时 this 指向外层作用域的 this 值
  }
}
```

2.不能作为构造函数实例化对象

3.不能使用 arguments 变量

4.简写：省略 ()，当行参有且仅有一个时；省略 " {} "和 "return"，当代码体只有一条语句时，而且语句的执行结果 就是 函数的返回值

5.箭头函数 Not suitable for call, apply and bind methods

适合的场景：与 this 无关的回调：定时器、数组的方法回调

不适合的场景：与 this 有关的回调：dom 元素的事件回调，对象的方法 



```html
 <script>
    //需求：点击 div 两秒后，改变颜色
    //获取元素
    let ad = document.getElementById('ad')
    //绑定事件
    ad.addEventListener("click", function () {
      console.log(this);  // <div id="ad"></div>
      //定时器
      setTimeout(function () {
        console.log(this); //window
      }, 2000)
    })
  </script>
```



##### 函数默认参数

允许对函数参数设置默认值

设置默认值的参数通常靠后放

##### Spread (扩展运算符)... 

```javascript
// ... 扩展运算符能将[数组]转换为逗号分隔的 参数序列
// 声明一个数组
const tfboys = ['易','源','凯']
//...tfboys => '易','源','凯'

// 声明一个函数
function chunwan(){
  console.log(arguments)
}
chunwan(...tfboys)
// 等价于 chunwan('易','源','凯')
```

- 扩展运算符应用之 数组合并

```js
//ES5 
const kuaizi = ['wang', 'xiao']
const fenghuang = ['zeng', 'ling']
const hebinghou = kuaizi.concat(fenghuang)
console.log(hebinghou)

//ES6 Spread
const hebing = [...kuaizi, ...fenghuang]

let a=[1,2]
let b=[5,6]

b.push(...a)
console.log(b)
//[ 5, 6, 1, 2 ]
```

- 扩展运算符应用之 数组克隆

如果 数组中有引用类型，采用 浅拷贝

```js
const kuaizi = ['wang', 'xiao']
const kelong = [...kuaizi]
```

- 扩展运算符应用之 转换伪数组为真正的数组

```js
const divs = document.querySelectorAll('div') //对象
const divArr = [...divs]
console.log(divArr) //真正的数组 []
```



##### Rest 参数

当被用于函数传参时，是一个 Rest 操作符：

ES6 引入 rest 参数，用于获取函数的实参，用来代替 arguments，rest 参数必须放在参数最后

```javascript
function foo(...args) {
  console.log(args);
}
foo('白','啊','思'); // ['白'，'啊'，'思'] - 是一个数组
// 可以使用数组的 API 方法来处理
```

对比：ES5 获取实参的方法

```js
function date(){
	console.log(arguments)
}
date('白','啊','思')
// Arguments 是一个对象
// Arguments(3)['白'，'啊'，'思']
```




函数中 this 绑定总是指向对象自身

```javascript
//不使用箭头函数，这种写法 有 错，因为下面两个 this 指向不同对象
function Person() {
  this.age = 0;
 
  setInterval(function growUp() {
    // 在非严格模式下，growUp() 函数的 this 指向 window 对象
    this.age++;
  }, 1000);
}
var person = new Person();

//改进之
function Person() {
  var self = this;
  self.age = 0;
 
  setInterval(function growUp() {
    self.age++;
  }, 1000);
}

//使用 箭头函数 完美解决
function Person(){
  this.age = 0;
 
  setInterval(() => {
    // |this| 指向 person 对象
    this.age++;
  }, 1000);
}
 
var person = new Person();
```



##### 支持二进制和八进制的字面量

通过在数字前面添加 0o 或者0O 即可将其转换为八进制值

##### 迭代器（Iterators)

迭代器是一种接口，为各种不同的数据结构提供统一的访问机制。任何数据结构只要部署 [Iterator 接口](对象里面的一个属性 Symbol.iterator)，就可以完成遍历操作。

1）ES6 创造了一种新的遍历命令 for...of 循环，Iterator 接口主要供 for...of 消费

2）原生具备 Iterator 接口的数据(可用 for...of 遍历)

​	a）Array

​	b）Arguments

​	c）Set

​	d）Map

​	e）String

​	f）TypeArray

​	g）NodeList

3）工作原理 //...待理解？？？难！

​	a）创建一个指针对象，指向当前数据结构的起始位置

​	b）第一次使用对象的 next 方法，指针自动指向数据结构的第一个成员

​	c）接下来不断调用 next 方法，指针一直往后移动，直到指向最后一个成员

​	d）每调用 next 方法返回一个包含 value 和 done 属性的对象

注：需要自定义遍历数据的时候，要想到迭代器

###### for...of / for...in

for...of 用于遍历一个迭代器，如数组：

```js
let nicknames = ['di', 'boo', 'punkeye'];

for (let v of nicknames) {
  console.log(v); //v 保存的是 键值
}
// 结果: di, boo, punkeye
```

for...in 用来遍历对象中的属性：

```js
let nicknames = ['di', 'boo', 'punkeye'];

for (let v in nicknames) {
  console.log(v); //v 保存的是 键名
}
Result: 0, 1, 2, size
```

##### Map 和 WeakMap

ES6 提供了 Map 数据结构。它类似于对象，也是键值对的集合。但是“键”的范围不限于字符串，各种类型的值（包括对象）都可以当作键。Map 也实现了 iterator 接口，所以可以使用 扩展运算符 和 for...of... 进行遍历。Map 的属性和方法：

1）size 返回 Map 的元素个数

2）set 增加一个新元素，返回当前 Map

3）get 返回键名对象的键值

4）has 检测 Map 中是否包含某个元素，返回 boolean 值

5）clear 清空集合，返回 undefined

6）delete 删除

```js
//声明 Map
let m = new Map()

//添加元素
m.set('name', 'shang')
m.set('change', function(){ console.log('change')})
let key = {
  school: 'GuiGu'
}
m.set(key, ['bei','shang','shen'])
m.delete('name')
console.log(m.size)

console.log(m)
```

Map 是一个升级版的 对象

##### 集合 Set 和 WeakSet

ES6 提供了新的数据结构 Set。它类似于数组，但成员的值都是唯一的。集合实现了 iterator 接口，所以可以使用 Spread 运算符 和 for...of... 进行遍历，集合的属性和方法：

1）size 放回集合的元素个数

2）add 增加一个新元素，放回当前集合

3）delete 删除元素，返回 boolean 值

4）has 检测集合中是否包含某个元素，返回 boolean 值

5）clear 清空

```js
// 声明一个 Set
let s = new Set()
let s2 = new Set(['大','小','好','坏','小'])
console.log(s2) //Set(4){'大','小','好','坏'} - 去重
console.log(s2.size)
s2.add('喜')
s2.delete('坏')
let ifHas = s2.has('好')
console.log(ifHas) //true

for(let v of s2){
  console.log(v)
}
```



##### Symbol

ES6引入了一种新的原始数据类型 Symbol，表示独一无二的值。是 JS 语言的第七种数据类型，是一种类似于字符串的数据类型；

Symbol 的值是唯一的，用来解决命名冲突的问题；

Symbol 值不能与其他数据进行运算；

Symbol 定义的对象属性不能使用 for...in 循环遍历，但是可以使用 Reflect.ownKeys 来获取对象的所有键名；

```js
// 创建 Symbol -- 第一种方式
let s = Symbol()
console.log(s, typeof(s)) //Symbol() "symbol"
// 创建 -- 第二种方式
let s1 = Symbol('zhang') //入参 类似注释
let s0 = Symbol('zhang') //s1 != s0
// 创建 -- for 方法
let s2 = Symbol.for('ha') //此处是 对象，函数对象
let s3 = Symbol.for('ha') // s2 === s3
```

JS 数据类型：USONB  

U - undefined

S - string symbol

O - object

N - null number

B - boolean

**Symbol 应用**之 - 向对象中添加方法 up down

```js
let game = {}

// 声明一个对象
let methods = {
  up: Symbol(),
  down: Symbol()
}
game[methods.up] = function(){
  console.log("change shape")
}
game[methods.down] = function(){
  console.log("down fast")
}
```

 另一种添加属性的方式

```js
let youxi = {
  name:"langrensha",
  [Symbol('say')]:function(){ //...待消化  
    console.log('发言')
  },
  [Symbol('zibao')]:function(){
    console.log('自爆')
  }
}
console.log(youxi)
```

17/68 //... 待整理

除了定义自己使用的 Symbol 值以外， ES6 还提供了Symbol 的 11 个属性，指向语言内部使用的方法；

[Symbol.内置属性] 整体 可用来做用户自己定义的对象的属性，通过对这些属性值进行设置，可修改用户自定义对象在特定场景下的表现 - 扩展对象功能；

```js
// Symbol.hasInstance
// 加了注释为缺省的使用方式，注释打开后为修改后的
class Person{
  static [Symbol.hasInstance](/*param*/){
    //console.log(param)
    console.log('用来检测类型')
    //return false
  }
}

let o = {}
// o 会被 自动传入上面函数，作为入参
console.log(o instanceof Person)
```

**Symbol.iterator** - 对象进行 for...of 循环时，会调用 Symbol.iterator 方法，返回该对象的默认遍历器

##### Generators

##### 对象超类

ES6 允许在对象中使用 super 方法：

```javascript
var parent = {
  foo() {
    console.log("Hello from the Parent");
  }
}
 
var child = {
  foo() {
    super.foo();
    console.log("Hello from the Child");
  }
}
 
Object.setPrototypeOf(child, parent); //...
child.foo(); // Hello from the Parent
             // Hello from the Child
```



##### 类 class

ES6 提供了更接近传统语言的写法，引入了 class（类）这个概念，作为对象的模板。通过 class 关键字，可以定义类。基本上，ES6 的 class 可以看作只是一个语法糖，它的绝大部分功能，ES5 都可以做到，新的 class 写法只是让对象原型的写法更加清晰、更像面向对象编程的语法而已。

知识点：

1）class 声明类

2）constructor 定义构造函数初始化

3）extends 继承父类

4）super 调用父级构造函数

5）static 定义静态方法和属性

6）父类方法可以重写 

这里的 class 不是新的对象继承模型，它只是原型链的语法糖表现形式。



```javascript
class Task {
  constructor() {
    console.log("task instantiated!");
  }
 
  showId() { //类中定义函数不需要使用 function 关键词
    console.log(23);
  }
 
  //static 关键词定义构造函数的的方法和属性
  static loadAll() {
    console.log("Loading all tasks..");
  }
}
 
console.log(typeof Task); // function
let task = new Task(); // "task instantiated!"
task.showId(); // 23
Task.loadAll(); // "Loading all tasks.."
```

类中的继承和超集：

```javascript
class Car {
  constructor() {
    console.log("Creating a new car");
  }
}
 
class Porsche extends Car {//extends 允许一个子类继承父类
  constructor() {
    super();//必须：执行 super() 函数
    console.log("Creating Porsche");
  }
}
 
let c = new Porsche();
// Creating a new car
// Creating Porsche
```

也可以在子类方法中调用父类的方法，super.parentMethodName()。

类的声明不会提升（hoisting)，如要使用某个 Class，必须先定义，否则会抛出一个 ReferenceError 的错误。









##### 模块化

模块化是指将一个大的程序文件，拆分成许多小的文件，然后将小文件组合起来。

模块化的**好处**：防止命名冲突、代码复用、高维护性

ES6之前的社区**模块化规范**有（ES没有自己的）：

1）CommonJS => NodeJS、Browserify

2）AMD           => requireJS  -- 浏览器端

3）CMD          => seaJS         -- 浏览器端

**ES6模块化语法**：

模块化功能主要由两个命令构成：export 和 import

- export 命令用于规定模块的对外接口
- import命令用于输入其他模块提供的功能

三种暴露的方式

分别 + 统一 + default

导入方式

```js
//1. 通用的导入方式
import * as m1 from './src /js/m1.js'

//2. 解构赋值的形式
import {school, teach} from './src/js/m1.js'
import {school as guigu, findJob} from './src/js/m2.js' //用 as 别名 防止名字冲突
// default - 必须起个别名才可以 
import{default as m3} from './src/js/m3.js'

//3. 简便形式 - 只能针对默认暴露
import m3 from "./src/js/m3.js"
```

**浏览器中使用 ES6 模块化的另一种方式**

在独立 js 文件中而非 html 文件中引入；

```html
<script src='./src/js/app.js' type="module">
```

**实际开发中怎么使用 模块化** -  通过 Babel 做一个转化

原因：兼容性上并非每款浏览器都能支持 src + type='module' 这种导入模块的特性，另外，ES6 还不能对 npm 安装的一些模块做一个导入

步骤：

1.初始化 package.json 并安装工具babel-cli babel-preset-ent browserif(webpack)

```bash
$ npm init --y
$ npm i -D babel-cli babel-preset-ent browserif
```

分别是：babel 命令行工具、预设包，能转换最新的特性为 ES5 的语法、打包工具

2.因为局部安装，通过 npx 运行 babel，进行代码转化

```　bash
$ npx babel src/js -d dist/js --presets=babel-preset-env
```

dist/js 目录下的文件是基于 commonJS 模块规范 (不同于 ES6 的另一种模块规范)

webpack 是基于 NodeJS 的，采用的是 commonJS 模块规范

3.打包

dist/js 目录下的 app.js 直接用页面去引入也是不能直接运行的，require 语法不能够识别；

```bash
$ npx browserify dist/js/app.js -o dist/bundle.js
```



**ES6 模块化规范 与 npm 包 的结合**使用

需求：通过 jquery 包对 home.html 的背景进行修改

步骤：

1.安装 jquery 包



##### 生成器函数 

异步编程用的

//... 待补充

##### async 和 await - ES8

这两种语法结合可以让异步代码像同步代码一样

1-1.async 函数的返回值为 Promise 对象；

1-2.promise 对象的结果由 async 函数执行的返回值决定

```js
// async 函数
async function fn(){
  // 返回一个字符串
  //return 'shang'
  //return
  //1-2-1  返回的结果不是一个 Promise 类型的对象，返回的结果就是成功的 Promise 对象
  //1-2-2 抛出错误，返回的结果是一个失败的 Promise
  //throw new Error('error!!!')
  //1-2-3 返回的结果如果是一个 Promise 对象，那么 该 Promise 对象成功或失败的值就是 fn 函数返回的 Promise 对象成功或失败的值 
  return new Promise((resolve, reject)=>{
    resolve('success')
  })
}
```

2-1.await 必须写在 async 函数中

2-2.await 后侧的表达式一般为 Promise 对象

2-3.await 返回的是 Promise 成功的值

2-4.await 的 Promise 失败了，就会抛出异常，需要通过 try...catch 捕获处理

```js
//创建 Promise 对象
const p = new Promise((resolve, reject)=>{
  //resolve('user info')
  reject('fail!')
})

//await 要放在 async 函数中
async function main(){
  try{
    let result = await p
    console.log(result)
  }catch(e){
    console.log(e)
  }
}
//调用函数
main() 
```



##### **?.**   - ES11（2020）

```javascript
obj?.prop
obj?.[expr]
arr?.[index]
func?.(args)
```

可选链 操作符 ( ?. ) 允许读取位于连接对象链深处的属性的值，而不必明确验证链中的每个引用是否有效。?.  操作符的功能类似于 . 链式操作符，不同之处在于，在引用为空(nullish ) (null 或者 undefined) 的情况下不会引起错误，该表达式短路返回值是 undefined。与函数调用一起使用时，如果给定的函数不存在，则返回 undefined。

#### ES5知识点

[李立超 JS核心从入门到精通](https://www.bilibili.com/video/BV1TE411B7KU?p=104&spm_id_from=pageDriver)

调试环境  Chrome / Inspect / Console 数字类型会用彩色显示出来

##### **变量**

变量是对“值”的具名引用。变量就是为“值”起名，然后引用这个名字，就等同于引用这个值。变量的名字就是变量名。

##### function

函数是一等公民

pure funciton is the one and only first-class citizen

函数 是 普通老百姓，是 Object

函数 和 变量 没有任何区别

函数也可以作为变量的值存储，也可以作为参数传递，也可以作为返回值返回

JS 引擎遇到 return 语句 就直接返回 return 后面的那个表达式的值，后面的语句不再执行

```js
// 计算 0-100 之间能被4整除但不能被5整除的前10个数
function getFirstTen(i, res, limit){
  for(j=0; j<i; j++){
    // break condition
    if(res.length===limit){
      return res;
    }
    if(j%4===0 && j%5!==0){
      res.push(j)
  
  }
}

var res = [];
getFirstTen(101, res, 10);
console.log(res);
```

gy函数声明 function declaration 和 函数表达式 function expression

```js
// function declaration
function add(a, b){
  return a + b;
}
// function expression  -- hoisting
var add = function (a, b){
  return a + b;
}

//重写
var getFirstTen = function (i, res, limit){
  for(j=0; j<i; j++){
    // break condition
    if(res.length===limit){
      return res;
    }
    if(j%4===0 && j%5!==0){
      res.push(j);
  }
}
console.log(getFirstTen); //打印函数内容/browser 或 [Function getFirstTen]/node

var res = getFirstTen(101, [], 10);
console.log(res);
```

functional/local scope/variable && global scope/variable

函数内部声明的变量在函数外面没法访问

函数作用域内部也会产生 变量提升 现象， 与 全局作用域一样

var 命令声明的变量，不管在什么位置，都会被提升到函数体的头部

JS 允许省略函数入参

```js
console.log(add()) //NaN
```

函数参数如果是原始类型的值，传递方式是**传值传递**(pass by value) --> 在函数体内修改参数值，不会影响到函数外部

函数参数如果是 对象、数组、其他函数，传递方式是**传址传递**(pass by reference) --> 在函数体内修改参数，将会影响到原始值

##### 对象 Object

JS 的对象，是一种无序的数据集合，由若干个“键值对”(key-value)构成

分类：内建 + 宿主 + 自定义

1.内建对象：由 ES 标准中定义对象，在任何 ES 的实现中都可以使用；

比如：Math、String、Number、Boolean、Function、Object 

```js
var num = new Number(123) //num: 一个对象
num*2 //参与运算后，num 变为 原始数值 number 类型
// 字符串 和 布尔 类型与之类似 
```

2.宿主对象：

​		由 JS 的运行环境提供的对象，目前主要是指由浏览器提供的对象；

​        BOM、DOM

​		BOM对象举例：

​		<u>window</u>.innerWidth. window.innerHeight .history.back()  , location.href

​		<u>navigator</u>.appVersion navigato.rappVersion, language, platform

3.自定义对象：由开发人员自建的对象，其创建/定义 方法如下：

```javascript
//JS 对象的属性值，可以是任意的数据类型，包括对象

//方法1 -- 字面量
function sum(a, b){ return a + b; }
var obj = {
  age: 10;
  100: 'Bob';
};
console.table(obj); //以表格形式打印
obj.name = 'Lisa';
ob[sum] = '123'; //会以 sum.toString() 作为 key
var v = obj[100]; //'Bob' - 数字也可以作为 key
var dog = {
 //访问对象属性的两种方式 obj.name  obj["name"]
  name: "Doudou",
  "owner": "Mia",  //属性名 也 可以加引号来使用
  greet:function(){
    console.log(this.name + ":" + "Wang Wang!");
  }
};
dog["gender"] = "male"//访问对象属性一种方式
dog.age = 3 //对象添加属性，对象.新属性名 = ...

delete dog.name //删除对象属性
console.log(dog) 
dog.greet();

//in 运算可以检查 对象 和 属性 是否相关
var isIn = "name" in obj; //'true' 

//方法2 -- 系统构造函数
var dog = new Object();
dog.name = "Doudou";

dog.greet = function(){
  console.log(this.name + ":" + "Wang Wang!");
};

dog.greet();

//==>如上定义好的对象没法复用，如果想要复用，需要定义 对象类型，如下： 

//方法3- 创建对象类型/自定义的构造函数 - 注意：名字首字母大写
function Person(first_name,last_name){
  this.first_name = first_name;           //使用 this
  this.last_name = last_name;
  this.greet = greetFunction;
};
//构造函数工作原理：new Person() => Person 定义里 隐式增加 var this = {}, return this
function greetFunction(){
  console.log('Hi, I am ${this.first_name}${this.last_name}.')
}
var person = new Person("David", "Wang"); //使用 new
person.greet(); 
```

console 控制台就相当于在 srcript 标签下面进行处理

document.write() 显示对象时 不能显示属性等，只能[object, Object]

如果一个变量 没有声明，直接 打印 会报错；

一个对象的属性 若没有声明，会 打印出 undefined；

JS 中的变量都是保存在栈内存中，

基本数据类型的值 直接 在栈内存中存储，值与值之间独立存在，修改一个不会影响其他的变量；

对象 是保存在堆中的，每创建一个新的对象，就会在堆内存中开辟出一个新的空间，而变量保存的是对象的内存地址（对象的引用）；不同的变量名指向同一个对象，那么它们都指向同一个内存地址，修改其中一个变量，会影响到其他所有变量；

解析器在调用函数时，每次都会向函数内部传递进一个隐含的参数 this，this 指向一个对象。

##### this 的指向 - dynamic binding

0、函数 预编译过程 this --> window

```js
function test(c){
  var a = 123
  function b(){}
}
AO{
  arguments: [1],//预编译 给 argments 和 this 赋值
  this: window,
  c: 1,
  a: undefined,
  b: function(){}
}
test(1)
```

1、全局作用域里，this --> window

2 、obj.func()，func() 里面 this --> obj

3、在 JavaScript 中函数也是对象，apply / call 就是函数对象的方法，允许切换函数执行的上下文环境（context）为 函数的第一个入参 代表的对象；

```javascript
var person1 = {
  fullName: function() {
    return this.firstName + " " + this.lastName;
  }
}
var person2 = {
  firstName:"John",
  lastName: "Doe",
}
//使用 person2 作为参数来调用 person1.fullName 方法时, this 将指向 person2
person1.fullName.call(person2);  // 返回 "John Doe"
```



**工厂方法**创建对象 用函数加入参来创建不同对象的方式

```javascript
//工厂方法 示例
function createPerson(name, age, gender){
  var obj = new Object();  //使用的 构造函数 都是 Object，无法通过 typeof 区分出新对象的具体类别
  obj.name = name;
  obj.age = age;
  obj.gender = gender;
  
  obj.sayName = function(){
    ...;
  }
}

var obj1 = createPerson("孙",18,"male"); //typeof obj1: "object"
var obj2 = createPerson("猪",28,"male");
var obj3 = createPerson("沙",18,"male");

//代替了之前的笨方法（如下）
 var obj1 = {
  name:"孙",
  age : 18,
  gender : "male",
  sayName : function(){
    ...;
  }
var obj2 = {
  name:"猪",
  age : 28,
  gender : "male",
  sayName : function(){
    ...;
  }
var obj3 = {
  name:"沙",
  age : 18,
  gender : "male",
  sayName : function(){
    ...;
  }
```

##### **构造函数**

**构造函数** 解决了上述方法无法区分新建对象类别的问题。

可创建一个构造函数，专门用来创建 Person 对象。

构造函数是一个普通函数，创建方式和普通函数没有区别，不同的是，构造函数习惯首字母大写。

调用方式：构造函数 用 new 关键字来调用，而普通函数可以直接调用。

```javascript
function Person(name, age, gender){
  this.name = name;
  this.age = age;
  this.gender = gender;
  this.sayName = function(){...};
}
Person.height = 'height' //只属于构造函数对象的属性 - 静态成员
var per = new Person("sun", 18, "male");
console.log(per); //Person{"sun", 18, "male"}
  
//检查 某对象 是否是 某类 的 实例
var isOf = per instanceof Person; //'true'
isOf = per instanceof Object; //'true' <-- 任何对象都是 Object 的后代
```

**构造函数执行流程：**

1.立刻创建一个新的对象

2.将此新的对象设为函数中的 this，所以可以使用 this 来引用新建的对象

3.逐行执行构造函数中的代码

4.将新建的对象作为返回值返回

使用同一个构造函数创建的对象，称为一类对象，所以也将一个构造函数称为一个 **类**。

```javascript
//优化👆构造函数中的方法，<--每执行一次，创建一个新的 sayName 方法，所有实例的 sayName 都唯一
//不同实例间实现 共享方法
//构造函数外面 定义 方法
function fun(){
  .... this.name;
}

function Person(name, age, gender){
  this.name = name;
  this.age = age;
  this.gender = gender; 
  this.sayName = fun; //指向全局 fun 函数
}
//但是，将函数定义在全局作用域，污染了全局作用域的命名空间，而且也不安全，所以有局限
```

##### 原型对象

解决方法如下，引入 **原型对象** 的概念

```javascript
Person.prototype.sayName = function(){
  alert("Hello, I am " + this.name);
}

var per = new Person("sun", 19, "male");
console.log(per.__proto__ === Person.prototype); //'true'
```

我们所创建的任何一个函数，解析器都会向其添加一个属性： prototype，指向 原型对象。

如函数作为普通函数调用，prototype 没有任何作用；

如函数作为构造函数调用时，它所创建的对象中都会有一个隐含的属性 __ proto__，指向该构造函数的原型对象。

原型对象 相当于一个公共的区域，所有同一个类的实例都可以访问到这个原型对象，我们可以将对象中共有的内容，统一设置到原型对象中。

当我们**访问对象的一个属性或方法时**，它会先在对象自身中寻找，如果有直接使用，如果没有，会去 原型对象 中找，如果找到则直接使用，如果没有则去原型对象的原型对象中查找，... 直到找到 Object 对象的原型，如果在 Object 的原型中依然没有找到，则返回 undefined -- 原型链

Object 的原型 没有 原型对象。

==> 创建构造函数时，可以将这些对象共有的属性和方法，统一添加到构造函数的原型对象中，这样，不用分别为每一个对象添加，也不会影响到全局作用域，就可以使每个对象都具有这些属性和方法。

原型是 function 对象的一个属性，它定义了构造函数制造出的对象的公共祖先。通过该构造函数产生的对象，可以继承该原型的属性和 方法；原型也是对象；

利用原型特点和概念，可以提取共用属性；

对象如何查看原型：隐式属性 __ proto__

对象如何查看对象的构造函数：constructor

```js
Car.prototype = {
  height: 1400,
  carName: 'Toyota'
}
function Car(){
  // 执行 new Car() 时，发生的事，第一步：
  //var this = {  
  //  __proto__ : Car.prototype
	//}
}
var car = new Car()
consolo.log(car.carName) //Toyota
```



```
    ｜------<-----------------------<-----------------｜    
    ｜                 缺省属性                        相等
构造函数 function Car() ------ 原型prototype:{}         ｜
    |                          ｜   ｜-- constructor: f Car()
    |                         相等	 |-- __proto__ : Object
    | new       缺省隐式属性     ｜   
实例对象 car    ------------ __proto__
    
```

对象字面量赋值 {} 等价于 new Object()

Object.create(原型 ｜ null) 创建 对象

```js
Person.prototype.name = 'sun'
function Person(){
  
}
var person = Object.create(Person.prototype)
//等价于
var person = new Person()
```

绝大多数对象的最终都会继承自 Object.prototype

null 和 undefined 没有 toString()，undefined 是一个原始值，不是对象，且没有包装类；null 也不是对象；

：可正常计算的范围：小数点前16位，后16位

**继承发展史**

1.传统形式 --> 原型链

​	-- Father.prototype.lastName = 'Deng'

​	   function Father(){}

​       Son.prototype = Father

​	   function Son(){}

​	-- 过多地继承了没用的属性

2.借用构造函数 

​	-- Son 构造函数中：Father.call(this, 参数1，参数2)

​	-- 不能继承借用构造函数的原型

​	-- 每次构造函数都要多走一个函数

3.共享原型

​	-- Son.prototype = Father.prototype

​	-- 不能随便改动自己的原型

​       Son.prototype.sex = 'male' --> Father 的也跟着改了

4.圣杯模式 //...待复习

```js
function inherit(Target, Origin){
  function F(){}
  F.prototype = Origin.prototype
  Target.prototype = new F()
  Target.prototype.constructor = Target
  Target.prototype.uber = Origin.prototype
}

//另一种实现方式 YUI
var inherit = (function(){
  var F = function(){} //被私有化
  return function(Target, Origin){
    F.prototype = Origin.prototype
    Target.prototype = new F()
    Target.prototype.constructor = Target
    Target.prototype.uber = Origin.prototype
  }
}())
```

##### 命名空间

管理变量，防止污染全局，适用于模块化开发；

使用对象 或 闭包；

想要实现方法的连续调用（类似 jquery），方法返回 this 即可；

##### 对象的枚举

for in - for(var prop in obj){ var propName = obj[prop] }，理论上，可以延展到原型及原型链上的属性，但一旦到 Object.prototype，不做处理

1.hasOwnProperty -如果传入参数是 原型属性或方法 false，自己的 true

```js
var obj = {
	name: 'li',
  age: 10,
  country: 'China',
  __proto__: {
    lastName: 'Lee'
  }
}

for(var key in obj){
  if(obj.hasOwnProperty(key)){
    console.log(obj[key])
  }
}
//==> for...in 和 hasOwnProperty 常配套使用 
```

2.in - 判断属性是否可用，包括原型上的属性，不常用

```js
'height' in obj //true
```

3.instanceof - 判断A对象的原型链上有没有B的原型

```js
person instanceof Person //true
person instanceof Object //true

arr instanceof Array //true
obj instanceof Array //false => 可以用来：区分 数组 [] 和 对象 {} 
```

区分 数组 [] 和 对象的另外两种方式：

```js
obj.toString() //[object, Object]
arr.toString() //[object, Array] => 方式二 推荐使用！

constructor // 方式三
```



##### call / apply / bind

改变 this 指向，传参形式不同

```js
// test() 等价于 test.call()
function Person(name, age){
  this.name = name
  this.age = age
}
var obj = {}
Person.call(obj, 'li', '60')//修改 Person 中的 this
Person.apply(obj, ['li', '60'])
Person.bind(obj, 'li', '60')()
==> 后面三种方式 效果等价
```



##### 包装类

Number()、String()、Boolean() 可以将基本数据类型的数字符串、布尔值转为 Number、String、Boolean对象，但实际开发并不会用，因为执行比较操作会有不可预期的结果。

```javascript
var num = new Number(3);
var str = new String("fabgaj");
var bool = new Boolean(true);

//typeof(num) typeof(str) typeof(bool) : "object"
```

对一些基本数据类型的值调用属性和方法时，浏览器会临时使用包装类将其转为对象，然后再调用对象的属性和方法，调用完成后，再转回原来的基本数据类型。

```javascript
var s = 123;
s = s.toString();     //(1)临时转化123 成 Number 对象，然后 销毁对象
s.hello = "nihao";    //(2)临时转化
console.log(s.hello); //(3)临时转化 因为 临时对象（1）！=（2）！=（3），所以：undefined
```

##### arguments

在调用函数时，浏览器每次都会传递进两个隐含的参数：

1.函数的上下文对象 this

2.封装实参的对象 arguments

arguments 保存实参，是个类数组 - 可以通过 arguments.length 可以获取实参个数，通过下标可以获取某个实参；即使不定义行参，也可以通过 arguments 来使用实参，arguments[0] 表示第一个实参；

Arguments.callee 属性指向当前正在执行的函数对象



面向过程 & 面向对象 -- JS 两者的思想都有

1. c、

2. 

##### typeof 类型转化

typeof(123) 与 typeof 123 等价

返回入参的类型；

六种数据类型 number、string、boolean、undefined、object、function

**引用数据类型**：数组(Array)、函数(Function)、对象(Object)

显示类型转换：

```js
var e = Number('123') // 尽量转化成 数字，true->1 'abc'->NaN
var f = parseInt('123abc') //转为 整数 ->123 一直看到非数字位截止
f = parseInt(10, 16)//按16进制来理解10，10->16 'a'->10，第二个参数2~32
parseFloat('100.2.3') // -> 100.2
e.toString() //把 e 转为 字串，null 和 undefined 不能使用
e.toString(8) //把 e 转为 8 进制的数 
String(true) //尽量转化成 字串 -> 'true'
Boolean('12') //尽量转化成 true / false
```

隐式类型转换：

```js
isNaN("abc") //true 会先调用 Number("abc")
==  //引发隐式类型转换
!=  //引发隐式类型转换
```

特例：

undefined 以及 null 与 0 做比较，均返回 false

undefined==null //true

NaN == NaN.       //false

=== !== 不发生类型转换的比较

typeof(a) //在 a 没有定义的情况下返回 undefined，而不是报错

##### ”use strict“ 指令 es5 严格模式

在 JavaScript 1.8.5 (ECMAScript5) 中新增，是对象一个字面量表达式；

不再兼容 es3 的一些不规则语法（例如：不能使用未声明的变量），使用全新的 es5 规范；

浏览器是基于 es3.0 的方法语法 + es5.0 的新增方法 使用的，如果冲突的部分，采用 es3.0；

es3.0 和 es5.0 产生冲突的时候，如果启动 严格模式 的话，使用 es5.0；

启动 严格模式 后，才可以使用 es5.0 的方法； 

为什么使用字符串字面量？- 在没有实现 es5.0 的浏览器上也不会报错，向后兼容（老版本不报错，新版本能识别）；

```js
//用法一：在脚本头部添加 use strict
//启动 es5.0 严格模式
”use strict“
function test(){
  console.log(arguments.callee) //TypeError: es5中不能使用 callee 方法
}

//------------ 推荐使用第二种方式 ---------------
function test1(){
  ”use strict“ //用法二：在函数内部启用 es5.0 严格模式
  console.log(arguments.callee) //TypeError: es5中不能
```

es5.0 禁用的功能：

1. with - 可以改变作用域链，简化代码，但是 运行效率变慢

```js
// with
var obj = {
  name: 'obj'
}
var name = 'window'
function test(){
  var name = 'scope'
  with(obj){ //会把 obj 放在{}内代码体作用域链的最顶端
    console.log(name)
  }
}

//应用场景一：
//定义命名空间
var org = {
  dp1:{
    Lisa: {
      name: 'abc',
      level: 12
    },
    Magi: {
      name: 'def',
      level: 15
    }
  },
  dp2:{
    
  }
}

with(org.dp1.Lisa){
  console.log(name) //可以直接访问自己想要的上下文的属性
}
//场景二：
with(document){
  write('abb')
}
```

2.arguments.callee

3.function.caller

es5 严格模式规定:

1.变量声明后才能使用；

2.局部 this 必须被赋值，而且 赋了什么值就是什么，预编译不再 指向 window；

3.拒绝重复参数和属性

```js
"use strict"
function test(){
  conslole.log(this) 
}
test()  //'undefined'

//如果传入数字
test.call(123) //严格模式下：123；es3：Number{}
```



//...待补充 foreach 循环 二维数组

#####  函数 & 方法 7-8/42 Jomy

简化代码、解偶合、实现一个功能；

函数定义的三种方法：函数声明方式、构造函数方式、函数表达式方式

```javascript
//一：函数声明的方式
function fun3(...){...};

//二：通过构造函数的方式，代码直接写在（）中
var fun = new Function("conslole.log('abc')"); //...???

//三：函数表达式方式，将匿名函数赋值给变量
var fun2 = function(...){...}; //fun2.name = fun2
var fun23 = function test(...){...};//fun23.name - test
//==>表达式会忽略名字，充当了表达式后不能再当函数体，test 不能再使用
            
fun();
fun2();
fun3();
```

函数中可以封装一些代码，在需要时可以执行这些功能（代码）；

函数也是对象，具有对象的特点，如：fun2.hello = 'abc';

封装到函数中的代码不会立即执行，这些代码**会在函数调用时**（函数名() ）执行。

**函数参数**

函数（）中可以指定一个或多个形参，形参之间用 "," 隔开，声明形参就相当于在函数内部声明了对应的变量，但是并不赋值；

在调用函数时，可以在（）中指定实参（实际参数），实参将会赋值给函数中对应的形参；

解析器也不会检查实参的类型，所以如果有可能接收到非法的参数，则需要对参数进行类型检查，

解析器也不会检查实参的数量，多余的实参不会被赋值；

如果实参数小于形参数，则没有对应实参的形参将是 undefined;

函数的实参可以是任意的数据类型，包括函数（对象）。

```js
var test = function(a, b, c){
  var num = test.length //行参 个数
  var num2 = arguments.length //实参 个数
}
```

行参 和 arguments 之间有映射规则，你变我也变，但不是相同的变量；

**return** 

return 语句使函数终止执行，如果没有写，系统自动添加 

return undefined；

return 输出 返回值 到调用的地方；

返回值 的类型 可以 是任意类型，包括函数；

对象的属性如果是一个函数，此时称作对象的方法；调用对象的函数属性，也就是调用函数的方法。

```javascript
var obj = new Object();

obj.sayName = function(){...};

var obj2 = {
  name : "zhu",
  age : 19;
  sayName : function(){...}
}     
                         
obj.sayName();
obj2.sayName();       
                         
//枚举 对象的属性 for...in循环             
for(var n in obj2){ //每循环一次，n 会得到一个 obj2 的属性名
  console.log(obj2[n]); //唯一的写法
}                 

//练习 - 反转字串
function reverse(){
  var str = window.prompt('input')
  var result = ''
  for (var i=str.length-1; i>=0; i--){
    //str.charAt(i)
    result[str.length-1-i] = str[i]
    result += str[i]
  }
  return result
}                         
```

##### 预编译

解决代码执行次序的问题

**函数预编译**发生s在函数执行的前一刻，四个步骤：

1.创建 AO 对象 - Activation Object（执行期上下文 ）

2.找行参和变量声明，变量和行参名作为 AO 属性名，值为 undefined

3.将实参值和行参统一

4.在函数体内找函数声明，将名字挂起来，作为 AO 属性名，并将函数体 赋给 对应 属性

```js
//-----------------------------------
console.log(b)   //undefined - 规则 2
var b = function(){}
//-----------------------------------
//chrome 函数不能声明在 if 语句里面！不可以写成下面的样子
if(a){
  function c(){...}
}
//-----------------------------------
consolo.log(typeof(d))//'undefined'-d没有定义的时候
consolo.log(typeof(null)) //'object'
consolo.log(-true) // -1
consolo.log(+undefined) // NaN  
//-----------------------------------
(window.foo || window.foo = 'bar') //报错！
(window.foo || (window.foo = 'bar')) //先执行 ||右边的 (window.foo = 'bar')，因为()优先级高于 || 
```

**全局预编译** - 预编译也发生在全局 

1.创建 GO 对象（Global Object）GO  === window  

2.变量声明 提升

3.函数声明提升

GO 的创建 早于 AO；

**JS 执行三步**：通篇 语法/语义 分析 + 预编译 + 解释执行

**基本知识点**：

函数声明整体提升

变量 - 声明提升

1.imply global（暗示全局变量）- 任何变量，如果变量 未声明就赋值，此变量就为全局对象 window 所有； 

```js
function test(){
  var a = b = 123
}
test()
console.log(windlow.a)//undefined
console.log(window.b) //123
```

2.一切声明的全局变量，全是 window 的属性 - window 就是全局的域；

```js
var a = 3
console.log(window.a) //3
```



##### 作用域链

**[[scope]]**：每个 js 函数都是一个对象，对象中有些属性我们可以访问，有些不可以，这些属性仅供 js 引擎存取，[[scope]] =**作用域链**就是其中之一；[[scope]] 中存储了执行期上下文的集合，该集合呈链式链接；

**执行期上下文**：当函数执行时，会创建一个称为执行期上下文的内部对象。一个执行期上下文定义了一个函数执行时的环境，函数每次执行时对应的上下文都是独一无二的，所以多次调用一个函数会导致创建多个执行上下文，当函数执行完毕，它所产生的执行上下文被销毁；

**查找变量**：从作用域链的顶端依次向下查找；

```js
function a(){
  function b(){//3.b 函数被创建时，拿 a 现有的作用域
    var b = 234
  }
  var a = 123
  b()
}
var glob = 100
a()
//1.a 被定义后，就有了自己的属性和方法，包括 [[scope]]，指向 scope chain，而 scope chain[0]->GO{}
//2.a 被执行时，创建 AO，scope chain[0]->AO{}
//						        scope chain[1]->GO{}
```

**全局作用域、函数作用域**

直接编写在< script> 标签中的 JS 代码，都在**全局作用域**中，全局作用域在页面打开时创建，在页面关闭时销毁。

全局作用域中有一个全局对象 window，它代表的是一个浏览器的窗口，由浏览器创建，我们可以直接使用。

在全局作用域中，创建的变量都会作为 window 对象的属性保存，创建的函数都会作为其方法保存。

```javascript
//变量的声明提前
//使用 var 关键字声明的变量，会在所有代码执行前被声明（但不会被赋值）；但是若不用 var 声明的变量，则不会被声明提前
console.log("a="+a); //"undefined" 声明了但没赋值
var a = 123;

//上面的代码 等价于 下面三行
var a;
console.log("a="+a); 
a = 123;

//函数的声明提前
fun();
fun2(); //报错！undefined
function fun(){...};  //函数声明，会被提前，在所有代码执行执行被创建
var fun2 = function(){...}; //只有 var fun2 被提前，但赋值并不会
```

调用函数时创建函数作用域，函数执行完毕后，函数作用域销毁。

每调用一次函数就创建一个新的函数作用域，他们之间相互独立。

函数中可以访问到全局作用域的变量。

```javascript
//函数中不使用 var 声明的变量，为全局变量
function fun5(){
  d = 100; //没有使用 var 相当于 window.d
}

fun5();
console.log("d="+d); //"d=100"

//var e=23;
//定义形参 相当于 在函数作用域中声明了变量
function fun6(e){
  alert(e);
}
fun6(); //"undefined"
```

当**在函数作用域中操作一个变量**时，先在自身作用域中寻找，有则用，如果没有，找上一级作用域...如找了全局作用域还没找到，没有定义 undefined.

##### 闭包 

当内部函数被保存到外部时，将会生成闭包。闭包会导致原有作用域链不释放，造成内存泄漏；

//可参考 [蛋老师 闭包 [JS面试题]](https://www.bilibili.com/video/BV1iE411q7Qd/?spm_id_from=333.788.recommend_more_video.0)

**闭包的作用**：

1.实现公有变量

2.可以做缓存（存储结构） 

3.可以实现封装，属性私有化

​	- 参考 inherit 实现的另一种方式

4.模块化开发，防止污染全局变量

```js
//一：公有变量 用途
//待推导 并 复习
function a(){
  function b(){
    var bbb = 234
    document.write(aaa)
  }
  var aaa = 123
  return b //内部的函数被保存到了外部 --> 闭包
}

var glob = 100
var demo = a()
demo()  // 123

//------------ 练习 2 ---------------
function a(){
  var num = 100
  function b(){
    num ++
    console.log(num)
  }
  return b
}
var demo = a()
demo()  //101
demo()  //102

//------------ 练习 3 ---------------
function test(){
  var num = 100
  function a(){
    num ++
    console.log(num)
  }
  function a(){
    num --
    console.log(num)
  }
  return [a, b]
}
var myArr = test()
myArr[0]()  //101
myArr[1]()  //100
```

做存储结构用途

```js
function eater(){
  var food = ''
  var obj = {
    eat: function(){
      console.log('I am eating '+food)
      food = ''
    }
  }
  return obj
}
var eater1 = eater()
eater1.push('banana')
eater1.eat() //I am eating banana
```

##### **立即执行函数**

针对 初始化功能 的函数；

此类函数没有声明，在一次执行结束后马上释放； 

```javascript
// 两种写法
// 第一种 - W3C 建议使用
(function(){
  alert("立即执行");
}())

// 第二种
(function(a, b){
  console.log(a+b)
})(12, 58);

//也可以有返回值并赋值
var v = (function(a, b){
  return a+b 
})(12, 58);
```

只有表达式才能被执行符合执行；

能被 执行符号() 执行的表达式中的函数名会被忽略；

```js
//----------------------------------
var test = function(){
  console.log('a')
}() //a
test() //undefined - test 已经被忽略

//----------------------------------
//语法错误 - 函数声明不能被执行
function f(){ 
  console.log('a')
}()  //如果是 (1,2,3) => 不报错，也不执行


//但是，修改成 下面 的形式后则可以被执行
+ function f(){ 
  console.log('a')
}()
```

##### 运算符

= 赋值运算符 优先级 最低，() 优先级最高

1/0 Infinity 正无穷，Number 类型

0/0 - NaN，非数，Number 类型

6个转成 boolean 后为 false 的值：  

&&：返回左边的值 或者 右边的值

​         -- 可用作短路语句：data && 处理data

||：找真，一个使用场景

```js
div.onclick = function(e){
	//非 IE 浏览器，e 有值
  //IE 浏览器，window.event 存放的是对应的值
  var event = e || window.event //兼容
}
```



```js
var a = 1
document.write(a++) //1 - 先运行语句

//交换 a b 俩数的值 - 技巧！
var a = 123
var b = 4
a = a + b
b = a - b
a = a - b

console.log(NaN==NaN) //false
```

找质数

```js
//判断 100 是不是质数
var vip = Math.sqrt(100)
for(var i=2; i<=vip; i++){ 
  //... 判断 100 是否能被 i 整除
  if(100 % i == 0){
    return true
  }
}
return false
```



##### 克隆 及 三目运算

深度克隆：克隆前后的变量 尽量独立

浅度克隆

```js
//深度克隆：将 origin 里的属性逐个取出，拷贝后 作为 target 的属性
// 遍历对象 for(var prop in obj)
// 1.判断是不是原始值 typeof() object
// 2.如果不是，判断是数组还是对象， instanceof toString-推荐 constructor
//  2.1 从而建立相应的数组或对象
//  2.2 递归，将新数组或对象作为目标对象，origin 的属性 作为源对象 进行拷贝
//... 笔记待完善 - 22/42 Jomy
function deepClone(origin, target){

}
```

待补充：页面跨域

? :

##### 数组 Array

是一种允许你存储多个值在一个引用里的结构

数组的定义

```javascript
//定义方式1 - 数组字面量
var arr = [];
arr[0] = "1st";
arr[24] = "25th"; //可以直接给空数组的某个索引位置的元素赋值
console.log(arr);
==> ['1st', <23 empty items>, '25th']
var cars=["Saab","Volvo","BMW"]; //推荐使用！
var cars1=["Saab",,,,"BMW"] //-- 稀松数组
var cars2=[10] //只有一个元素的 数组  
//定义方式2 - 数组构造方法 new Array(content / length)
var carrs = new Array("Saab","Volvo","BMW");
var carrs = new Array(10) //- 长度是 10 的数组

var cars = new Array();
cars[0]="Saab";
cars[1]="Volvo";
cars[2]="BMW";
```

数组 读写 - 几乎不报错

```js
var arr = []    //空数组
arr[2]          //undefined
arr[10] = 'abc' //数组长度变为11，最后一个元素是 'abc'
```

**常用的方法**

 ECMAScript、DOM-操作html、BOM-操作浏览器

es3.0  很强大 - 其中数组的方法

es5.0 在3.0基础上加了几个方法

es6.0 很强大，加了不少

改变原数组

​	-- push, pop, shift, unshift, sort, reverse, splice

不改变原数组 

​	-- concat, join, split, toString, slice, find

```js
var arr = []
arr.push(10) //+ 尾部添加 返回数组长度
arr.push(1,2,3,4) //5 

//自己重写 push 方法
Array.prototype.push = function(){
  for(var i=0; i<arguments.length; i++){
    this[this.length] = arguments[i]
  }
  return this.length
}

arr.pop()      //- 把数组最后一个元素拿出来
arr.unshift(6) //+ 数组头部插入
arr.shift()    //- 头部拿出  
arr.reverse()  //翻转
arr.splice(1, 2, 56) //从第 1 个位置开始截取 2 个元素，并插入 56 --> 以数组形式返回 截取出的 信息
arr.splice(1, 0, 23) //第二个参数为 0 ： 插入元素
arr.splice(-1, 1)    //将最后一个元素拿出
 
arr = [1,3,4,10,5]
arr.sort() //升序 - [1,10,3,4,5]
//1.必须两个行参
//2.看返回值 1）返回值为负数时，前面的数排前面
arr.sort(function(a,b){
  /*自己定义规则*/
  return a-b //升序
})

//给一个有序的数组，乱序
var arr = [1,2,3,4,5,6]
arr.sort(function(a,b) {
  //乱排
  return Math.random()-0.5
})

Math.random() - 生成 0～1 范围内的随机数，不包含 1

var newArr = arr.slice(1,2)//从第1位开始，到第2位
var newArr1 = arr.slice(2) //从第2位开始截取，到末尾
var newArr2 = arr.slice()  //整个截取

var str = arr.join('-') //1-2-3-4 用'-'连接每个元素成字符串
//split() - 是 string 的方法
var arrResult = str.split('-') //['1','2','3','4']

//字串拼接
// 推荐 数组（散列结构）连接，
// 而不是字串一个个连接 - 栈结构，先进后出
var str = 'ali'
var str1 = 'baidu'
var str2 = 'tencent'
var str3 = 'toutiao'
var arr = [str, str1, str2, str3]
arr.join("")

//The find() method returns the value of the first element that passes a test.
const ages = [3, 10, 18, 20];

function checkAge(age) {
  return age > 18;
}

function myFunction() {
  document.getElementById("demo").innerHTML = ages.find(checkAge);
}

// The find() method executes a function for each array element.
// The find() method returns undefined if no elements are found.
// The find() method does not execute the function for empty elements.
// The find() method does not change the original array.
```

2维数组刷算法题目时常用

数组的存储采用 queue  FIFO，不同于 stack FILO

数组语法上允许存储不同类型的值，但是实际开发中不建议这样使用



##### 类数组

属性要为索引属性，必须有 length 属性，最好加上 push；

虽然是对象，使用方法跟数组 类似；

```js
var obj = {
  '0': 'a',
  '1': 'b',
  '2': 'c',
  'length': 3,
  'push': Array.prototype.push,
  'splice': Array.prototype.splice
}

Array.prototype.push = function(target){
  obj[obj.length] = target
  obj.length ++
}
```

好处：

1.可以利用属性名模拟数组的特性

2.可以动态的增长 length 属性

3.如果强行让类数组调用 push 方法，则会根据 length 属性值的位置进行属性的扩充

DOM 所能生成的所以类似于数组的东西全是类数组

25/42 26/42 待练习//...

##### try...catch

防止报错 

try 代码块中如果如果错误，不抛出，不会执行 try 里面错误后的代码，继续执行 try 后面的代码

```js
try{
	console.log('a')
  console.log(b)   //错误
  console.log('c') //忽略 
}catch(e){ //error <-- err.message, err.name 系统
	console.log(e.message + ” “ + e.name) //执行
}
console.log('d') //执行
//a d
```

try {} catch ( e ) {} finally {}

Error.name  的六种值对应的信息：

1.EvalError：eval() 的使用与定义不一致

2.RangeError：数值越界

3.ReferenceError：非法或不能识别的引用数值 - 多

​	- 一个变量没经声明就使用时会报

4.SyntaxError：发生语法解析错误 - 多

​	-   如果代码里出现中文分号时，Invalid or unexpected token

5.TypeError：操作数类型错误

6.URIError：URI 处理函数使用不当

##### Date 日期对象 

第三方库：Moment.js Day.js

32/42 Jomy - 14'

Javascript W3School - 官方字典

```javascript
var d = new Date();
var d = new Date(milliseconds);
var d = new Date(dateString);
var d = new Date(year, month, day, hours, minutes, seconds, milliseconds);

var date = d.getDate() //1-31
var day = d.getDay() //0-6
var month = d.getMonth() //0~11
var year = d.getFullYear() //2022
//其他 getHours getMinutes getSeconds

//获取 时间戳
var time = d.getTime() //返回 1970 开始的毫秒数 - 最常用
//==> 可以用来计算执行代码花费的时间

d.toString() //转成 字符串

Date() //直接调用返回 当前日期时刻 字符串
```

使用场景 - 闹铃⏰

```js
//setInterval(function(){
// 判断：如超过设定闹铃的时间，触发某操作	
//}, 1000)
```

##### 定时器

推荐书：

高性能 javascript、你不知道的 js

四个重要的 window对象的 方法：

1.setInterval(function(){}, 3000)

​	- 可以计数，定时不精确、基于红黑树

2.clearInterval()

3.setTimeout(fun(){}, n000) - 该函数执行之后会产生一个子线程，子线程会等待 n 秒，然后执行回调函数

4.clearTimeout()

内部函数的 this 指向 window

```js
var i=0
var timer = setInterval(function(){
  log.console(i++)
  if(i>10){
    clearInterval(timer)
  }
}, 3000)

//另一种写法
setInterval(
  'log.console(i++)', 3000)

var timer1 = setTimeout(function(){
  log.console(i++)}, 10000)
clearTimeout(timer1)
```



##### Math 

对象用于执行数学任务，并不像 Date 和 String 那样是对象的类，因此没有构造函数 Math()。

```javascript
//直接调用Math的属性或方法
var area = Math.PI * r * r;
var circumference = 2 * Math.PI * r;

//或使用with关键字
with(Math)
  {
    var myRand = random();
    var biggesr = max(3, 4,  5);
    var height = round(76.35);
  }
```

##### DOM

Document Object Model - 由浏览器厂商定义的一类宿主对象的集合，提供了表示和修改文档所需的方法，是 JS 操作网页的接口，它的作用是 将网页转为一个 JS 对象，从而可以用脚本进行各种操作（比如增删内容）；浏览器会根据 DOM 模型， 将结构化文档（html/xml）解析成一系列的节点，再由这些节点组成一个树状结构（DOM Tree）；所有的节点和最终的树状结构，都有规范的对外接口；所以 DOM 可以理解为网页的编程接口； 

Each time your brower loads and displays a  page, it creates in memory an **internal representation of the page and all its elements**, the **Document Object Model** or DOM.

window.document -- refer to html file

history,loaction.navigator

Document：整个文档树的顶层节点

Root element：< html>

Element：网页的各种 HTML 标签 < body> < a> 

Attribute：网页元素的属性

Text：标签之间或标签包含的文本

Comment：注释

```bash
Common JS methods for DOM Manipulation
1. querySelector - return 1st element found or null
2. querySelectorAll - return all elements as NodeList object or empty object
3. addEventListener - assign function to certain event
4. removeEventListener
5. createElement - create a new HTML element using the name of the tag
6. appendChild
7. removeChild
8. insertBefore - add an element before a child element
9. setAttribute - add a new attribute to an HTML element
```

一个例子：

```js
var btnEl = document.querySelector('#like-button');
var pEl = document.querySelector('#like-counter-dsply');

var count = 0;
btnEl.addEventListener('click', function(){
  count += 1;
  pEl.innerHTML = count;
});
```

id 不用做 css，但可以用在 JS 中 

```javascript
let img = new Image();
img.src = '';
img.onload = function(){...}; //图像装载完毕时调用的事件
img.onerror = function(){...};   //装载图像的过程中发生错误时调用的事件                 
```

补：xml 中可以自定义标签，html 中不可以，xml 已被 json 取代



DOM 不能直接操作 CSS；

 //选项卡的例子

```html
<style type='taxt/css'>
	.content{
		display:none;
		width:200px;
		height:200px;
		border:2px solid red;
	}
	.active{
		background-color: yellow
	}
</style>
<div class='wrapper'>
  <button class = 'active'>111</button>
  <button>222</button>
  <button>333</button>
  <div class='content' style='display:block'>1111</div>
  <div class='content'>deng</div>
  <div class='content'>3333</div>
</div>
<script>
var btn = document.getElementByTagName('button')
var div = document.getElementByClassName('content')
for(var i=0; i< btn.length; i++){
  (function(n){
    btn[n].onclick = function(){
      for(var j=0; j<btn.length; j++){
        btn[j].className = ''
        div[j].style.display = 'none'
      }
      this.className = 'active'
      div[n].style.dislay = 'block'
    }
  }(i))
}
</script>
```

//其他例子：鼠标滑过小格子，显示画笔效果 28/42 Jomy //...待消化 css 部分

// 其他例子：轮播图

**DOM 基本操作**

1.对节点的增删改查

查看元素节点

document - 代表整个文档

document.getElementById() - 元素 id 在 IE8 以下的浏览器，不区分 id 大小写，而且也返回匹配 name 属性的元素

注：实际开发中，id 有别的用途，后端抽取后可能会修改成其他的内容，所以不常用；一般作为顶级框架的名称存在，而不是作为选择器；

淘宝把主体先靠前布局，有原因的；

.getElementsByTagName() - 标签名，返回类数组 使用最广 

.getElementsByName() - 注意：只有部分标签 name 可生效(表单、表单元素、img、iframe)

name：能提交数据的组件的数据名

.getElementsByClassName() - 类名 -> IE8 及以下版本中没有，可以多个 class 一起

.querySelector() - css选择器 在 IE7 及 以下版本中没有

.querySelectorAll() - css 选择器 在 IE7 及 以下版本中没有

```html
<body>
  <div>
    <strong></strong>
  </div>
  <div>
    <span>
    	<strong class = 'demo'>123</strong>
    </span>   
  </div>
  <script type='text/javascript'>
    var strong = document.querySelector('div > span strong.demo')
  </script>
</body>
```

上面 query... 的两个方法 不是实时的，是静态的，取的是调用那一刻的副本 - 所以使用受局限，不常用；

**遍历节点树** - 基于树形结构

利用 dom 元素的属性：

parentNode - 父节点，html 的 parentNode： document

childNodes - 子节点们，包括：元素、文本、属性、注释等

```js
//节点的类型 - nodeType
		元素 - 1
		属性 - 2 
		文本 - 3
		注释 - 8
		document - 9
		DocumentFragment - 11
//节点的四个属性
		nodeName - 元素的标签名，只读
		nodeValue - Text 节点或 Comment 节点的文本内容，可读写
    nodeType - 该节点的类型，只读
		attributes - Element 节点的属性集合，每个属性有 name 和 value，value 可写，name 只读
//节点的一个方法
    Node.hasChildNodes()
//网页经典布局：
		淘宝
    新浪微博
    58同城
```

firstChild - 第一个子节点

lastChild - 最后一个子节点

nextSibling - 后一个兄弟节点

previousSibling - 前一个兄弟节点

**基于元素节点树的遍历** -  dom 元素的属性

parentElement - 返回当前元素的父元素节点（IE 不兼容）

children - 只返回当前元素的元素子节点

node.childElementCount === node.children.length 当前元素节点的子元素节点个数(IE 不兼容)

firstElementChild - 第一个元素节点（IE 不兼容）

lastElementChild - 最后一个元素节点（IE 不兼容）

nextElementSibling / previousElementSibling - 后一个/前一个兄弟元素节点（IE 不兼容）

##### DOM结构树

```
              HTMLDocument.prototype --构造函数-> Document
document --构造函数-> HTMLDocument

                   |- XMLDocument 不用
Node --- Document --- HTMLDocument
			|
      |- CharacterData --- Text
      |                 |- Comment
      |
      |- Element --- HTMLElement --- HTMLHeadElement
      |  													|- HTMLBodyElement
      |  													|- HTMLTitleElement
      |  													|- HTMLParagraphElement
      |  													|- HTMLInputElement
      |  													|- HTMLTabElement
      |  													|- ...
      |- Attr
      
getElementById --定义在-> Document.prototype 上
getElementsByName --定义在-> HTMLDocument.prototype 上
getElementsByTagName --定义在-> Document.prototype 上
                            |- Element..prototype 上
HTMLDocument.prototype 定义了一些常用的属性，body, head 分别指代 HTML 文档的 <body> <head> 标签；
Document.prototype 定义了 documentElement 属性，指代文档的根元素，即 <html> 元素；
getElementsByClassName、querySelectorAll、querySelector 在 Document.prototype，Element.prototype 类中均有定义；
```

##### DOM 基本操作

```
【增】
	document.createElement('div') //创建元素节点
	document.createTextNode()     //创建文本节点
	document.createComment()
	document.createDocumentFragment()
【插】
	parent.appendChild(div)
	parent.insertBefore(a, b) //parent insert a before b 
【删】
	parent.removeChild() //父 删 子
	child.remove()       //子 自删
【替换】
	parent.replaceChild(new, origin) 
【查看滚动条的滚动距离 - 像素】
	window.pageXOffset/pageYOffset - IE 9以上
	document.body.scrollLeft/scrollTop - IE 8 及以下
	document.documentElement.scrollLeft/scrollTop 兼容混乱
	==> 上面两个总有一个为0，相加即可
【查看 可视窗口 的尺寸】
	window.innerWidth / innerHeight - IE 9以上
	document.documentElement.clientWidth /clientHeight - 标准模式下，都兼容
	document.body.clientWidth /clientHeight - 怪异模式 适用
 document.compatMode //'CSS1Compat' - 标准模式, 'BackCompat' - 怪
【查看元素的几何尺寸】 - 任何 dom 元素都可以调用
	domEle.getBoundingClientRect()
	兼容性很好
	该方法返回一个对象，对象里面有 left、top、right、bottom 等属性。left 和 top 代表该元素左上角的 X 和 Y 坐标，right 和 bottom 代表元素右下角的 X 和 Y 坐标
	height 和 width 属性老版本 IE 并未实现
	返回的结果并不是 “实时的”，是此时此刻的静态写照
【查看元素尺寸】
	dom.offsetWidth / offsetHeight
【查看元素位置】
	dom.offsetLeft / offsetTop
	对于无定位父级的元素，返回相对文档的坐标；对于有定位父级，返回相对于最近的有定位的父级的坐标；
	dom.offsetParent
	返回最近的有定位的父级，如无，返回 body, body.offsetParent 返回 null
	eg:求元素相对于文档的坐标 getElementPosition
//body 里面有个默认 8 像素，横向相加 210，纵向塌陷 202 ...待理解
【让滚动条滚动】
	window 上有三个方法
	scroll(x, y) = scrollTo(x, y)
	scrollBy()
	三个方法功能类似，用法都是将 x、y 坐标传入；即实现让滚动轮滚动到当前位置
	区别：scrollBy() 会在之前的数据基础之上做累加；
	eg: 利用 scrollBy() 快速阅读的能力
```

34/42 1:01'40" 以后的待完成//...

< !DOCTYPE html> -- 标准模式，去掉后为 怪异/混杂 模式，这两个都指的是浏览器的渲染模式；

怪异模式 是 为了向后兼容，使得能够使用 IE7 浏览器 来 执行 为了 IE6 而写的代码；

```
空 html 文件中，输入：html:5 会自动生成骨架标签空页面
```



##### JSON - JavaScript Object Notation

~ 是一个特殊格式的字符串，可以被任意的语言识别并且可以转换为任意语言中的对象；

开发中主要用来数据的交互，通常用于服务端向网页传递数据；

～ 和 JS对象 的格式一样，只不过 JSON 字符串中的属性名必须加双引号，其他和JS语法一致；

```javascript
//JS 对象
var obj = {name : "sun", age:18, gender:"male"};

//JSON 字符串 对象，第一种
var objJson = '{"name" : "sun", "age":18, "gender":"male"}'; 

//JSON 字符串 数组，第二种
var arrJson = '[1,2,3,"hello",true]';

//JSON 与 JS对象 互转 
//JSON --> JS
var objRec = JSON.parse(objJson);
//JSON <-- JS
var strJson = JSON.stringify(obj);
```

~ 中允许的值：

字符串、数值、布尔值、null、对象不含函数、数组

```javascript
//JSON实例
//数据为 键/值 对，由逗号分隔；大括号保存对象；方括号保存数组
{"sites":[
    {"name":"Runoob", "url":"www.runoob.com"}, 
    {"name":"Google", "url":"www.google.com"},
    {"name":"Taobao", "url":"www.taobao.com"}
]}

//简单起见，我们网页中直接设置 JSON 字符串
var text = '{ "sites" : [' +
    '{ "name":"Runoob" , "url":"www.runoob.com" },' +
    '{ "name":"Google" , "url":"www.google.com" },' +
    '{ "name":"Taobao" , "url":"www.taobao.com" } ]}';

//使用 JavaScript 内置函数 JSON.parse() 将字符串转换为 JavaScript 对象    
var obj = JSON.parse(text);
document.getElementById("demo").innerHTML = obj.sites[1].name + " " + obj.sites[1].url;
//JSON.stringify()可以将 JavaScript 值转换为 JSON 字符串
```

**JSON数据API**

https://jsonplaceholder.typicode.com/posts

JSON对象在 IE7及以下浏览器中 不支持，所以在这些浏览器中会报错，解决办法：

eval()，该函数可以用来执行一段字符串形式的 JS 代码，并将执行结果返回；如果使用 eval() 执行的字符船中含有{}，会将{}当成是代码块，如果不希望将其当成代码块来解析，则需要在字符串前后各加一个()；

```javascript
var str = '{"name" : "sun", "age":18, "gender":"male"}';
var str2 = "(" + str + ")";
var obj = eval(str2);
```

eval() 函数功能很强大，可以执行一个字符串中的 JS 代码，但是在开发中尽量不要使用，首先性能差，然后它还具有安全隐患。

如果需要兼容 IE7及以下 的 JSON 操作，则可以通过引入一个外部 JS 文件来处理：

```html
<script type="text/javascript" src="js/json2.js"></script>
```

##### 浏览器识别并执行

​                              深度优先原则

1.识别 html 代码 ------------------> domTree

2.对img的处理：先挂节点

==> 生成 domTree ：dom 节点的解析完成，而不是 dom 节点内容的加载完成

3.cssTree 的构建 （深度优先原则）

4.domTree + cssTree = renderTree，渲染引擎开始绘制页面



会引起 renderTree 重建 reflow （低效）的原因：

dom 节点的删除、添加，

dom 节点的宽高变化、位置变化、diaplay none --> block，

offsetWidth、offsetLeft

所以要尽量减少这类操作，如果真的要做，一次性搞定；

repaint 重绘：也会影响效率，但可以接受；



##### 异步加载 js

js 加载的缺点：加载工具方法没必要阻塞文档，过多的 js 加载会影响页面效率，一旦网速不好，那么整个网站将等待 js 加载而不进行后续渲染等工作；

有些工具方法需要按需加载，用到再加载，不用不加载

三种方案：

1.defer 异步加载，但要等到 dom 文档全部解析完（dom 树生成）才会被执行

2.async 异步加载，加载完就执行（异步方式），async 只能加载外部脚本，不能把 js 写在 script 标签里；

==> 1. 2. 执行时不会阻塞页面

3.创建  < script>标签，插入到 DOM 中，加载完毕后 callback -- 最常用

```html
<!-- 异步加载 ts 文件的方式 1: IE 专用 -->
<script src='tools.ts' defer></script>
<script src='tools.ts' defer='defer'></script>
<script defer='defer'> 
	//代码块
</script>

<!-- 异步加载 ts 文件的方式 2: W3C 标准方法 -->
<script src='tools.ts' async='async'></script>

<!-- 异步加载 ts 文件的方式 3:  方法 -->
<script> 
	var script = document.createElement('script')
  script.type = 'text/script'
  
  <!-- 假如 demo.js 中有个函数 test() -->
  test() //不能识别，还没有下载完文件
  setTimeout(()=>{
    test() //此时可以执行，因为 已经下载完
  }, 1000)
  
  //IE 使用 readyState 来判断是否加载完成
  //script.readyState='loading'->'complete'/'loaded'
  if(script.readyState){
      script.onreadystatechange = function(){
      if(script.readyState=='complete'||
         script.readyState=='loaded'){
        test()
      }
    }
  }else{
    //非 IE 浏览器
    script.onload = function(){
      // Safari chrome firefox opera
      test() //文件下载完成后，会触发该函数的执行
    }
  }
	script.src = 'demo.js' //该行代码执行后即开始异 步下载文件
    
  document.head.appendChild(script)//开始执行 demo.js
//也可以把上面的逻辑封装成函数，待整理 //...39/42 后半
</script>
```

正常的 javascript 标签下载完立即执行，执行完才继续加载 html 和 css；

Network 会把所有下载来的东西，所有网络请求展示出来；

##### 浏览器加载 js 时间线

浏览器在运行一个页面的时候，会初始化 js 的功能，从初始化完 js 的功能开始，记载着浏览器要发生的过程；每一步按照时间排序，形成 js 加载时间线；

1.创建 Document 对象，开始解析 web 页面。解析 HTML 元素和他们的文本内容后添加 Element 对象和 Text 节点到文档中，该阶段 document.readyState = 'loading'

2.遇到 link 外部 css，创建线程加载，并继续解析文档

3.遇到 script 外部 js，并且没有设置 async、defer，浏览器加载，并阻塞，等待 js 加载完成并执行该脚本，然后继续解析文档

4.遇到 script 外部 js，并且设置有 async、defer，浏览器创建线程加载，并继续解析文档；对于 async 属性的脚本，脚本加载完成后立即执行该脚本（异步禁止使用 document.write() - 会清空文档流）

5.遇到 img 等，先正常解析 dom 结构，然后浏览器异步加载 src，并继续解析文档；

6.当文档解析完成（domTree 刚创建好），document.readyState = 'interactive'

7.文档解析完成后，所有设置有 defer 的脚本会按照顺序执行。（注意与 async 的不同）

8.document 对象触发 DOMContentLoaded 事件，这也标志着程序执行从同步脚本执行阶段，转化为事件驱动阶段；

9.当所有 async 的脚本加载完成并执行后、img 等加载完成后，document.readyState = 'complete'，window 对象触发 load 事件；

10.从此，以异步响应方式处理用户输入、网络事件等。

1、6、9 - 三个主要点

```html
<body>
	<script>
  	console.log(document.readyState)
    document.onreadystatechange = function(){
      console.log(document.readyState)
    }
    <!-- DOMContentLoaded 必须 这样绑定 -->
    document.addEventListener('DOMContentLoaded', function(){
      console.log('a')
    }, false)
	</script>
</body>
<!-- 可以打印 readyState 的所有状态
loading
interactive
a
complete
-->
```



```html
<body>
	<script>
    <!-- 当 dom 解析完就执行 jquery-->
    $(document).ready(function(){})
    <!-- 当 所有脚本执行完，资源加载完 触发：尽量不用-->
    window.onload = function(){}
  </script>
</body>
<!-- 高效的写法：将 DOMContentLoaded 写在 head /script 里面 -->
```

##### Demo - Object.freeze()

Freezing an object [prevents extensions](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/Object/preventExtensions) and makes existing properties non-writable and non-configurable.

```javascript
const obj = {
  prop: 42
};

Object.freeze(obj);

obj.prop = 33;
// Throws an error in strict mode

console.log(obj.prop);
// expected output: 42
```



##### P137~139 类的操作 & 二级菜单（练习）

##### P134～136 轮播图（练习）

##### P126 Location

##### P125 History

##### P124 Navigator

##### P122～123 键盘事件

onkeydown、onkeyup 一般都会绑定给：能获取焦点的对象 或 document；

altKey、ctrlKey、shiftKey 可用来判断 alt、ctrl、shift 是否被按下；

```javascript
document.onkeydown = function(event){
  event = event || window.event;
  if(event.keyCode==89 && event.ctrlKey){
    console.log("ctrl 和 y 都被按下了");
  }
}
```



##### P118～121 鼠标事件（练习）

##### P111~117 事件

**事件的传播**

关于事件的传播，网景公司和微软有不同的理解：

微软认为事件应由内向外，网景认为相反；W3C综合了两个公司的方案，将事件传播分成了三个阶段，

1 捕获阶段，在该阶段，从最外层的祖先元素向目标元素进行捕获，但是默认此时不会触发事件；

2 目标阶段，事件捕获到目标元素，捕获结束开始在目标元素上触发事件；

3 冒泡阶段，事件从目标元素向祖先元素传递，依次触发祖先元素上的事件。

#####  addEventListener

```javascript
//1
element.addEventListener("click", myFunction);

function myFunction() {
    alert ("Hello World!");
}

//2 
element.addEventListener("click", function(){ alert("Hello World!"); });
```

alert(`Sending "${message}" to ${contact.email}`); 字符串中取变量的方法



##### P85～90 正则表达式 Regular Expression

**基础符号：**

| []  ^ $ {} * + A-z 0-9 / i g

\w  字母、数字、_                             [A-z0-9_]

\W 除了 字母、数字、_                     [ ^A-z0-9_]

\d 任意数字                                        [0-9]

\D除了数字                                        [ ^0-9]

\s 空格

\S 除了空格

\b 单词边界    child & children的例子

\B 除了单词边界

其余网上资源：常见正则表达式

示例：

1 中国手机号码的验证式  /^1[3-9] [0-9]{9}$/

2 电子邮件验证式 \w{3,}  (\ .\ w+)* @ [A-z0-9]+   (\ .[A-z]{2,5}){1,2}

```javascript
//语法
var reg = new RegExp("^1[3-9][0-9]{9}$");
var str = "14510098";
console.log(reg.test(str)); //'false'
str = 13913811289;
console.log(reg.test(str)); //'true'

//或者第二种方法创建正则表达式
reg1 = /^1[3-9][0-9]{9}$/; //效果与上面相同
```

**求正则表达式的步骤：**

逐段分析 -- 文字提取每段规则 --  正则表示每段规则 -- 合并成一个完整规则 -- 测试&修正

##### P69 垃圾回收 GC

当一个对象没有任何的变量或属性对它进行引用，此时我们将永远无法操作该对象，此时这种对象就是一个垃圾，这种对象过多会占用大量的内存空间，导致程序运行变慢，所以这种垃圾必须进行清理。

程序运行过程中会产生垃圾，垃圾积攒过多以后，会导致程序运行的速度过慢，所以我们需要一个 GC 的机制，来处理程序运行过程中产生的垃圾。

在 JS 中拥有自动的垃圾回收机制：会自动将这些垃圾对象从内存中销毁。shijanxi

我么不需要也不能进行 GC 的操作；不同浏览器处理的方式不同。

```javascript
var obj = new Object();
//... 使用 obj 来实现功能
obj = null; //这样 浏览器会执行垃圾回收
```

##### toString

当我们直接在页面中打印一个对象时，实际上输出的是：对象的 toString() 方法的返回值，

如果我们希望在输出对象时不输出 [object Object]，可以为对象添加一个 toString() 方法。



##### P60 debug

F12 打开调试工具，进入Debug，设断点 Source，逐句执行 F10，观察/监控 值 Watch，AddWatch

**eval 作用域**

##### [Relationship between JavaScript, APIs, and other JavaScript tools](https://developer.mozilla.org/en-US/docs/Learn/JavaScript/Client-side_web_APIs/Introduction#relationship_between_javascript_apis_and_other_javascript_tools)

So above, we talked about what client-side JavaScript APIs are, and how they relate to the JavaScript language. Let's recap this to make it clearer, and also mention where other JavaScript tools fit in:

- JavaScript — A high-level scripting language built into browsers that allows you to implement functionality on web pages/apps. Note that JavaScript is also available in other programming environments, such as [Node](https://developer.mozilla.org/en-US/docs/Learn/Server-side/Express_Nodejs/Introduction).
- Browser APIs — constructs built into the browser that sits on top of the JavaScript language and allows you to implement functionality more easily.
- Third-party APIs — constructs built into third-party platforms (e.g. Twitter, Facebook) that allow you to use some of those platform's functionality in your own web pages (for example, display your latest Tweets on your web page).
- JavaScript libraries — Usually one or more JavaScript files containing [custom functions](https://developer.mozilla.org/en-US/docs/Learn/JavaScript/Building_blocks/Functions#custom_functions) that you can attach to your web page to speed up or enable writing common functionality. Examples include jQuery, Mootools and React.
- JavaScript frameworks — The next step up from libraries, JavaScript frameworks (e.g. Angular and Ember) tend to be packages of HTML, CSS, JavaScript, and other technologies that you install and then use to write an entire web application from scratch. The key difference between a library and a framework is “Inversion of Control”. When calling a method from a library, the developer is in control. With a framework, the control is inverted: the framework calls the developer's code.



##### JS数据验证 & 表单验证

大多数情况下，数据验证用于确保用户正确输入数据。

数据验证可以使用不同方法来定义，并通过多种方式来调用。

**服务端数据验证**是在数据提交到服务器上后再验证。

**客户端数据验证 side validation**是在数据发送到服务器前，在浏览器上完成验证。

1. required="required"；//如果必填字段没有填，会提示：Please fill in this field

2. onsubmit=func()，在JS的func()里面取出表单的输入值，判断是否为空或是否满足要求，不满足返回false并提示原因；

   ```javascript
   //示例1：验证email
   function validateForm(){
     var x=document.forms["myForm"]["email"].value;
     var atpos=x.indexOf("@");
     var dotpos=x.lastIndexOf(".");
     //包含 @ 符号和点号(.)，@不可以是首字符，@之后需有至少一个点号，点号后至少两个字符
     if (atpos<1 || dotpos<atpos+2 || dotpos+2>=x.length){
       alert("不是一个有效的 e-mail 地址");
       return false;
     }
   }
   ```

   

###### HTML 约束验证（constraint validation）

～是表单被提交时浏览器用来实现验证的一种算法，它是基于：

- **HTML 输入属性**
- **CSS 伪类选择器**
- **DOM 属性和方法**

##### HTMLCollection 

看起来像但不是数组；可以像数组一样，使用索引来获取元素。

HTMLCollection 无法使用数组的方法： valueOf(), pop(), push(), 或 join() 。

getElementsByTagName() 方法返回 [HTMLCollection](https://www.runoob.com/jsref/dom-htmlcollection.html) 对象。

##### **NodeList** 

对象是一个从文档中获取的节点列表 (集合) 。

```javascript
var myNodelist = document.querySelectorAll("p");
var i;
for (i = 0; i < myNodelist.length; i++) {
    myNodelist[i].style.backgroundColor = "red";
}
```

HTMLCollection 元素可以通过 name，id 或索引来获取。

NodeList 只能通过索引来获取。



##### History: Browser History

History.length

History.forward(), back(), next(), <u>go(-3), go(2), go("example.com")</u>

##### location: the URL of the currently loaded page

location.href=loaction.protocol+host(hostname+port)+pathname+search+hash

示例：

http://www.example.com:8080/tools/display.php?section=435#list

```javascript
location.reload();
```

###### 2 ways to go to a new page:

```javascript
Loacation.href = "www.newpage.com";

Location.replace("www.newpage.com"); //父页面被直接代替
```



###### 查找HTML元素的方法：id、标签、类名

```javascript
var x=document.getElementByID("intro");
document.getElementById("image").src="landscape.jpg"; //直接修改属性
document.getElementById("p2").style.fontFamily="Arial";//修改样式
var y=x.getElementsByTagName("p");
var z=document.getElementsByClassName("introC");
```

###### 分配事件两种方式

```javascript
<! 1.使用事件属性向 button 元素分配 onclick 事件>
<button onclick="displayDate()">点这里</button>
<script>
// 2.使用 JavaScript 来向 HTML 元素分配事件
document.getElementById("myBtn").onclick=function(){displayDate()};
</script>
```



##### 数据类型

**值类型(基本类型)**：字符串（String）、数字(Number)、布尔(Boolean)、空（Null）、未定义（Undefined）、Symbol。

特殊数字：NaN, Infinity

Null 类型 的值只有一个 null，表示一个为空的对象。

Undefined 类型的值只有一个 undefined，只声明没赋值的 变量 值 为 undefined.

```javascript
var x = 5;
var y = "5";
x==y; //true
x===y;//false 既比较值，也比较类型
var x1 = 6;

Math.sqrt(x ** 2 +  x1 ** 2) //平方的写法
console.log(typeof x); //返回 "number"

var z = Number.MAX_VALUE; //JS 中可以表示的数字最大值
var z1 = z * z; //JS 中超过 Number.MAX_VALUE 的数字返回 Infinity，正无穷
var z2 = Number.MIN_VALUE; shi// 5e-324

var a = 'abc' * 'cdf';

console.log(a); //返回 "NaN" not a number
console.log(typeof a); //返回 "number"

//浮点数运算结果可能不精确 precision loss
var x = 0.1 + 0.2; //0.300000000000004

var c = null;
console.log(typeof c); //'object'

//类型转化方式1 --> String, null 和 undefiend 没有 toString 方法
var a = 123;
var b = a.toString();

var c = true;
c = c.toString();

//类型转化方式2：调用 String()
a = String(a);

var e = null;
e = String(e); //e -- > String "null"

//类型转化方式1 --> 调用 Number(),
var a = "123";
a = Number(a);

var bb = "abc"; //或者 undefined
bb = Number(bb); //bb --> Number NaN

bb = ""; //或者 “  ”, false, null
bb = Number(bb); //bb --> Number 0

bb = true;
bb = Number(bb); //bb --> Number 1; false --> 0

//类型转化方式2：调用 parseInt() parseFloat()，把字符串转为整数 浮点
//如果是 null undefined，会先转为 String，再转，所以结果 NaN
var a = "123px";
a = parseInt(a); 
var b = 198.23；
b = parseInt(b); // 198

// 转为 Boolean，Boolean() 
// falsy value (0  NaN  ""  null undefined) --> false

//关系运算符 > >= < <=
//返回 true 或者 false
//对于非数值的情况，会先转为数字再比较；任何值和 NaN 做任何比较，返回 false
var result = 10 > "hello"; //false
result = "11" < "5"; //true 注意：该例子为特例，如果两个String类型比较，不转为 数字，比较 Unicode 
```



##### parseInt(num, base)

base: 0, 2, 4 ... 36

parseInt(3, 0) //返回原值

parseInt(3, 8) //3

parseInt(3, 2) //NaN



#### CDN

您总是希望网页可以尽可能地快。您希望页面的容量尽可能地小，同时您希望浏览器尽可能多地进行缓存。

如果许多不同的网站使用相同的 JavaScript 框架，那么把框架库存放在一个通用的位置供每个网页分享就变得很有意义了。

CDN (Content Delivery Network) 解决了这个问题。CDN 是包含可分享代码库的服务器网络。

国内免费的 CDN 资源有：

- Staticfile CDN：https://staticfile.org/

海外免费的 CDN 资源有：

- cdnjs：https://cdnjs.com/

如需在您的网页中使用 JavaScript 框架库，只需在 <script> 标签中引用该库即可：

引用 jQuery

```javascript
<script src="https://cdn.staticfile.org/jquery/3.4.0/jquery.min.js"> </script>
```

#### Unicode编码 -- 万国码

```html
<script>
	console.log('\u1c00'); //输出 Unicode 编码对应字符
</script>
<!--在网页 body 中输出 &#(十进制的数);-->
<h1> &#1;</h1>
```

中文 按照 康熙字典 的编排方式来。

#### 正则表达式

```javascript
<script>
var patt1=new RegExp("e");
document.write(patt1.test("The best things in life are free"));
</script>
```



```javascript
/*是否带有小数*/
function    isDecimal(strValue )  {  
   var  objRegExp= /^\d+\.\d+$/;
   return  objRegExp.test(strValue);  
}  

/*校验是否中文名称组成 */
function ischina(str) {
    var reg=/^[\u4E00-\u9FA5]{2,4}$/;   /*定义验证表达式*/
    return reg.test(str);     /*进行验证*/
}

/*校验是否全由8位数字组成 */
function isStudentNo(str) {
    var reg=/^[0-9]{8}$/;   /*定义验证表达式*/
    return reg.test(str);     /*进行验证*/
}

/*校验电话码格式 */
function isTelCode(str) {
    var reg= /^((0\d{2,3}-\d{7,8})|(1[3584]\d{9}))$/;
    return reg.test(str);
}

/*校验邮件地址是否合法 */
function IsEmail(str) {
    var reg=/^\w+@[a-zA-Z0-9]{2,10}(?:\.[a-z]{2,4}){1,3}$/;
    return reg.test(str);
}
```



10/42 Jomy JS - 24'31"-30‘30“  //...待补充

##### 定时器

setInterval() 和 setTimeout() 是 HTML DOM Window对象的两个方法。

setInterval() \- 间隔指定的毫秒数不停地执行指定的代码。

setTimeout() - 在指定的毫秒数后执行指定代码。

```javascript
<p id="demo"></p>
<button onclick="myStopFunction()">停止</button>
<script>
var myVar=setInterval(function(){myTimer()},1000);
function myTimer(){
    var d=new Date();
    var t=d.toLocaleTimeString();
    document.getElementById("demo").innerHTML=t;
}
function myStopFunction(){
    clearInterval(myVar);
}
</script>
```

clearInterval() 方法用于停止 setInterval() 方法执行的函数代码。

```javascript
var myVar;
 
function myFunction()
{
    myVar=setTimeout(function(){alert("Hello")},3000);
}
 
function myStopFunction()
{
    clearTimeout(myVar);
}
```

函数还未被执行，你可以使用 clearTimeout() 方法来停止执行函数代码。





#### RESTful API

Representational State Transfer

##### REST架构

1 每一个URL代表一种资源

2 客户端和服务器之间，传递资源的某种表现层（text，HTML，XML，JSON等）

3 客户端通过四个HTTP动词（GET，PUT，POST，DELETE），对服务器资源进行操作，实现“表现层状态转化”



#### JS 面试题

最近写代码遇到的困难或挑战

一个合格的前端开发应该具备哪些特质

你认为好的代码是什么样的

描述一下你最近写的最好的一段代码



-2 Tax Calculation (MYOB)

```js
function calcTax(income) {
  var tacTable = [
    { min:0, max:18200, rate:0, base:0 },
    { min:18200, max:37000, rate:0.19, base:0 },
    { min:37000, max:90000, rate:0.205, base:3572 },
    { min:90000, max:180000, rate:0.37, base:20797 },
    { min:180000, max:Number.POSITIVE_INFINITY, rate:0.45, base:54096 },
  ];
  var taxableRow;
  for(var i=0; i++; i<taxTable.length) {
    if(income>=taxTable[i].min && income<taxTable[i].max) {
      taxableRow = taxTable[i];
    }
  }
  var payableTax = (income - taxableRow.min) * taxableRow.rate + taxableRow.base;
  
  return payableTax;
}
```

-1.  Flight Stops(Qantas) 

given by an array of flights, return stops statement to user

```js
[墨 - 悉]：Direct
[墨 - 悉, 悉 - 新]：1 Stop
[墨 - 悉, 悉 - 新, 新 - 广]：2 Stops
[{},{},{},{}] - flights 的定义
function getStops(flights){
	//经停 Message
  // 第一种解法 - if else 尽量不用
	var stops = [];
	if(flights.length===1){
		return 'Direct';
	}
	var curIndex = 1;
  while(curIndex<flights.length){
    stops.push(flights[curIndex].departure)
  }
  var num = stops.length;
  return num + 'Stop' + num>1 && 's';
  
  // 第二种解法 
  var messageTable = [
    [1, 'Direct'],
    [2, '1Stop'],
    [13, 'Dream Line'],
    [17, 'Around The World'],
    [19, 'The Qantas'],
  ]
  var message; 
  var num = flights.length;
  for(int i=0; i<messageTable.length; i++){
    if(num===messageTable[i][0]){
      message = messageTable[i][1];
      break;
    }
  }
  message==='' && message = num-1 + 'Stops';
  return message;
  
  // 第三种 - ZhaoLong 老师的
  const stops = flight.length - 1;
  return {
    0: 'Direct',
    1: '1 Stop',
    13: 'Dream Line',
    17: 'Around The World',
    19: 'The Qantas',
  }[stops] || stops + 'Stops';
}
```

0.  class 是 以下哪种类型？

1. ```js
   var list = [1,2,3]  // list 的类型  -- b
   function sum(a, b){ // sum 的类型 -- b
   	return a + b;
   }
   ```

   a) Class  **b) Object**  c) No types  d) undefined

==> 除了基本类型以外的 都是 Object

##### new 一个对象的过程

```javascript
function Mother(lastName){
  this.lastName = lastName;
}
var son = new Mother("Da");
```

1. 创建一个新对象 son；

2. 新对象会被执行 [[prototype]]连接

   ```javascript
   son.__proto__ = Mother.prototype;
   ```

3. 新对象 和 函数调用 的 this 会绑定起来；

   ```javascript
   Mother.call(son, "Da");
   ```

4. 执行构造函数中的代码；

   ```javascript
   son.lastName;
   ```

5. 如果函数没有返回值，那么就会自动返回这个新对象。

   ```javascript
   return this;
   ```

   

##### Get & Post

get 和 post 的区别有哪些？ -- 蛋老师 //待复习...

https://www.bilibili.com/video/BV1Yb4y1v7tu?spm_id_from=333.999.0.0

Get 是以 **检索和获取** 为主，因此一般在 URL 上直接表明请求的所有内容，而且请求主体一般是不会有内容的；

Post是以 **创建/更新** 为主，内容可能很大，因此一般会直接在请求主体里面带上内容；

浏览器 对 URL 限制了长度，因此也就限制了 请求的内容；

Google 常用浏览器版本 的 URL 限制是 2Mb，即 2048 个字符；

加入浏览器收藏夹的过程分析。

get使用**<u>MIME类型application/x-www-form-urlencoded的URL编码（也叫百分号编码）文本的格式</u>**传递参数，保证被传送的参数由遵循规范的文本组成，例如一个空格的编码是"%20"。（文章转载自乐字节）



（资源）web编程原理、写的最详细的文章 -- 乐字节

https://www.bilibili.com/read/cv11615943?spm_id_from=333.999.0.0

##### 如何设置请求的编码以及响应内容的类型？

通过请求对象（ServletRequest）的setCharacterEncoding(String)方法可以设置请求的编码，其实要彻底解决乱码问题就应该让页面、服务器、请求和响应、Java程序都使用统一的编码，最好的选择当然是UTF-8；通过响应对象（ServletResponse）的setContentType(String)方法可以设置响应内容的类型，当然也可以通过HttpServletResponsed对象的setHeader(String, String)方法来设置。

##### 什么是Web Service？

从表面上看，Web Service就是一个应用程序，它向外界暴露出一个能够通过Web进行调用的API。这就是说，你能够用编程的方法透明的调用这个应用程序，不需要了解它的任何细节，跟你使用的编程语言也没有关系。例如可以创建一个提供天气预报的Web Service，那么无论你用哪种编程语言开发的应用都可以通过调用它的API并传入城市信息来获得该城市的天气预报。之所以称之为Web Service，是因为它基于HTTP协议传输数据，这使得运行在不同机器上的不同应用无须借助附加的、专门的第三方软件或硬件，就可相互交换数据或集成。
SOA（Service-Oriented Architecture，面向服务的架构），SOA是一种思想，它将应用程序的不同功能单元通过中立的契约联系起来，独立于硬件平台、操作系统和编程语言，使得各种形式的功能单元能够更好的集成。显然，Web Service是SOA的一种较好的解决方案，它更多的是一种标准，而不是一种具体的技术。

##### 转发和重定向 之间的区别？

forward是容器中控制权的转向，是服务器请求资源，服务器直接访问目标地址的URL，把那个URL 的响应内容读取过来，然后把这些内容再发给浏览器，浏览器根本不知道服务器发送的内容是从哪儿来的，所以它的地址栏中还是原来的地址。

redirect就是服务器端根据逻辑，发送一个状态码，告诉浏览器重新去请求那个地址，因此从浏览器的地址栏中可以看到跳转后的链接地址，很明显redirect无法访问到服务器保护起来资源，但是可以从一个网站redirect到其他网站。forward更加高效，所以在满足需要时尽量使用forward（通过调用RequestDispatcher对象的forward()方法，该对象可以通过ServletRequest对象的getRequestDispatcher()方法获得）。

并且这样也有助于隐藏实际的链接；在有些情况下，比如需要访问一个其它服务器上的资源，则必须使用重定向（通过HttpServletResponse对象调用其sendRedirect()方法实现）。

##### 浏览器组成：

1 shell 部分

2 内核部分 {

 - 渲染引擎（语法规则 和 渲染）
 - js 引擎 - V8 2008年Google发布，能把js代码直接转化为机械码=>速度快
 - 其他模块 }

3 主流浏览器机器内核 {

	- IE - trident
	- Chrome - webkit / blink
	- Firefox - Gecko
	- Opera - presto
	-  Safari - webkit }

**html 文件引入 js 的方式**

- 页面级JS - html 文件内引入 < script>...</ script>
- 外部JS文件 - 通过src引入 < script src="./path/abc.js"></ script>>

为符合web标准（w3c标准中的一项）结构、样式、行为相分离，通常会采用外部引入；外部JS文件优先级更高，同时使用，内部失效；

//参考代码 - 打印 package.json 依赖文件：

```js
const pkg = require('./package.json');

console.log('These are the dependencies that we use:');
console.log(Object.keys(pkg.dependencies).join('\n'));
console.log();
console.log('These are the devDependencies that we use:');
console.log('  ' + Object.keys(pkg.devDependencies).join('\n  '));

```



### 工具

1 JsonFormatter：可以把JSON格式显示成更易读的方式

2 IDE 中可以加 代码规范 的 文件 / 工具

3 Atom 编辑器

### 快捷键：

1 打开调试 窗 Console，Option+Command+I

