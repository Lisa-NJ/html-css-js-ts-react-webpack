### NodeJS=Node

前端 JavaScript + NodeJS = 后端 JavaScript

Node（JavaScript的服务器运行环境）

 = JavaScript虚拟机 && 工具库

Node内部采用Google V8 引擎（对JavaScript进行解释） + libuv（调度系统资源的库）

#### REPL

#### 其他

多行表达式

下划线变量

#### 回调函数

```javascript
var fs = require("fs"); //28/11/2021 有多少模块？每个模块有哪些函数？
fs.readFile('input.txt', function (err, data) {
    if (err) return console.error(err);
    console.log(data.toString());
});

console.log("程序执行结束!");
```

Node.js 异步编程依托于回调来实现，回调函数在完成任务后就会被调用，Node 使用了大量的回调函数，Node 所有 API 都支持回调函数。

例如，我们可以一边读取文件，一边执行其他命令，在文件读取完成后，我们将文件内容作为回调函数的参数返回。

### PHP

为了开始使用 PHP，找一个支持PHP和MySQL的Web主机，安装Web服务器、PHP及MySQL；

如果您的服务器支持 PHP，只要在 web 目录中创建 .php 文件即可，服务器将自动为您解析这些文件。

PHP 脚本在服务器上执行，然后将纯 HTML 结果发送回浏览器。

```php
<?php
$txt="Hello world!";
$x=5;
$y=10.5;
$z=$x+$y;
echo $z;
echo "变量 x 为: $x"; 

function myTest()
{
    //global 关键字：在函数内调用函数外定义的全局变量
    global $x,$y;
    $y=$x+$y;
}
function myTest1()
{
    //所有全局变量存储在一个名为 $GLOBALS[index] 的数组中。 index 保存变量的名称。
    $GLOBALS['y']=$GLOBALS['x']+$GLOBALS['y'];
} 
function myTest2()
{
    //static：希望某个局部变量不要被删除
    static $x1=0;
    echo $x1;
    $x1++;
    echo PHP_EOL;    // 换行符
}
function myTest3($x)
{
    echo $x;
}

MyTest3(6);
//echo - 可以输出一个或多个字符串（字符串可以包含 HTML 标签）,快，没有返回值
echo "<h2>PHP 很有趣!</h2>";
echo "这是一个", "字符串，", "使用了", "多个", "参数。";
$cars=array("Volvo","BMW","Toyota");
echo "<br>";
echo "我车的品牌是 {$cars[0]}";
//print - 只允许输出一个字符串，返回值总为 1；使用方法类似echo
print "<br>";
print "我新车的品牌是 {$cars[1]}";

$a = "Hello";
$b = $a . " world!"; //.可以连接字符串
?>
```

PHP 语句和 PHP 变量区分大小写。

弱类型语言：不必向 PHP 声明该变量的数据类型，PHP 会根据变量的值，自动把变量转换为正确的数据类型；在强类型的编程语言中，我们必须在使用变量前先声明（定义）变量的类型和名称。

PHP 中的 $_GET 和 $_POST 变量用于检索表单中的信息，比如用户输入。

```html
<html>
<head>
<meta charset="utf-8">
<title>菜鸟教程(runoob.com)</title>
</head>
<body>
 
<form action="welcome.php" method="post">
名字: <input type="text" name="fname">
年龄: <input type="text" name="age">
<input type="submit" value="提交">
</form>
 
</body>
</html>
```

当用户填写完上面的表单并点击提交按钮时，表单的数据会被送往名为 "welcome.php" 的 PHP 文件：

```php
欢迎<?php echo $_POST["fname"]; ?>!<br>
你的年龄是 <?php echo $_POST["age"]; ?>  岁。
```

预定义的 **$_GET 变量**用于收集来自 method="get" 的表单中的值，从带有 GET 方法的表单发送的信息，对任何人都是可见的（会显示在浏览器的地址栏）在 HTML 表单中使用 method="get" 时，所有的变量名和值都会显示在 URL 中，所以在发送密码或其他敏感信息时，不应该使用；并且对发送信息的量也有限制，不能超过 2000 个字符。

预定义的 **$_POST** 变量用于收集来自 method="post" 的表单中的值，从带有 POST 方法的表单发送的信息，对任何人都是不可见的（不会显示在浏览器的地址栏），并且对发送信息的量也没有限制，然而，默认情况下，POST 方法的发送信息的量最大值为 8 MB（可通过设置 php.ini 文件中的 post_max_size 进行更改）。

预定义的 **$_REQUEST** 变量包含了$_GET、$POST和 $_COOKIE的内容，可用来收集通过 GET 和 POST 方法发送的表单数据。

### MySQL

可以运行于多个系统上，支持多种语言：C、C++、Python、Java、Perl、PHP、Eiffel、Ruby 和 Tcl 等；

对PHP有很好的支持，PHP 是目前最流行的 Web 开发语言。

```bash
Rpm -qa | grep mysql //检测系统是否自带安装MySQL
```

如果你系统有安装，那可以选择进行卸载:

```bash
rpm -e mysql　　// 普通删除模式
rpm -e --nodeps mysql　　// 强力删除模式，如果使用上面命令删除时，提示有依赖的其它文件，则用该命令可以对其进行强力删除
```

### Apache服务

```bash
httpd -v  //查看Apache版本

sudo apachectl start //启动Apahe服务

//Web服务根目录：Library/WebServer/Documents

sudo apachectl stop //停止Apache服务

php -v //查看php的版本
```



### JAVASRIPT--网页行为

参考资料：《JS权威指南》 &《 JS高级程序设计》

//...待完成-1 ES6 7 8 9 

//...待完成-2 JS高级视频教程 

#### （资源2） JavaScript核心从入门到精通（李立超 版 视频教程）

https://www.bilibili.com/video/BV1TE411B7KU?p=104&spm_id_from=pageDriver

##### P91～105 DOM



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

##### P83、84 包装类 & 字符串的方法

Number()、String()、Boolean() 可以将基本数据类型的数字、字符串、布尔值转为 Number、String、Boolean对象，但实际开发并不会用，因为执行比较操作会有不可预期的结果。

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

##### P81、82 Date、Math

##### P79、80 call、apply、arguments

##### P70～78 数组



##### P69 垃圾回收 GC

当一个对象没有任何的变量或属性对它进行引用，此时我们将永远无法操作该对象，此时这种对象就是一个垃圾，这种对象过多会占用大量的内存空间，导致程序运行变慢，所以这种垃圾必须进行清理。

程序运行过程中会产生垃圾，垃圾积攒过多以后，会导致程序运行的速度过慢，所以我们需要一个 GC 的机制，来处理程序运行过程中产生的垃圾。

在 JS 中拥有自动的垃圾回收机制：会自动将这些垃圾对象从内存中销毁。

我么不需要也不能进行 GC 的操作；不同浏览器处理的方式不同。

```javascript
var obj = new Object();
//... 使用 obj 来实现功能
obj = null; //这样 浏览器会执行垃圾回收
```



##### P68 toString

当我们直接在页面中打印一个对象时，实际上输出的是：对象的 toString() 方法的返回值，

如果我们希望在输出对象时不输出 [object Object]，可以为对象添加一个 toString() 方法。



##### P61～67 this、工厂方法创建对象-->构造函数、原型对象

解析器在调用函数时，每次都会向函数内部传递进一个隐含的参数 this，this 指向一个对象。

根据函数调用方式的不同，this 会指向不同的对象：

1. 以函数的形式调用，this 永远指向 window

2. 以方法的形式调用，this 就是调用方法的那个对象
3. 当以构造函数的形式调用时，this 指向 新创建的对象
4. 当以 call() & apply() 的形式调用时，this 指向 指定的对象

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



**构造函数** 解决了上述方法无法区分新建对象类别的问题。

可创建一个构造函数，专门用来创建 Person 对象。

构造函数时一个普通函数，创建方式和普通函数没有区别，不同的是，构造函数习惯首字母大写。

调用方式：构造函数 用 new 关键字来调用，而普通函数可以直接调用。

```javascript
function Person(name, age, gender){
  this.name = name;
  this.age = age;
  this.gender = gender;
  this.sayName = function(){...};
}
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

使用同一个构造函数创建的对象，成为一类对象，所以也将一个构造函数称为一个 **类**。

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

解决方法如下，引入 原型对象 的概念

```javascript
Person.Prototype.sayName = function(){
  alert("Hello, I am " + this.name);
}

var per = new Person("sun", 19, "male");
console.log(per.__proto__ == Person.Prototype); //'true'
```

我们所创建的任何一个函数，解析器都会向其添加一个属性： Prototype，指向 原型对象。

如函数作为普通函数调用，Prototype 没有任何作用；

如函数作为构造函数调用时，它所创建的对象中都会有一个隐含的属性 __ proto__，指向该构造函数的原型对象。

原型对象 相当于一个公共的区域，所有同一个类的实例都可以访问到这个原型对象，我们可以将对象中共有的内容，统一设置到原型对象中。

当我们**访问对象的一个属性或方法时**，它会先在对象自身中寻找，如果有直接使用，如果没有，会去 原型对象 中找，如果找到则直接使用，如果没有则去原型对象的原型对象中查找，... 直到找到 Object 对象的原型，如果在 Object 的原型中依然没有找到，则返回 undefined。

Object 的原型 没有 原型对象。

所以，创建构造函数时，可以将这些对象共有的属性和方法，统一添加到构造函数的原型对象中，这样，不用分别为每一个对象添加，也不会影响到全局作用域，就可以使每个对象都具有这些属性和方法。

##### P60 debug

F12 打开调试工具，进入Debug，设断点 Source，逐句执行 F10，观察/监控 值 Watch，AddWatch

##### P58、59 全局作用域、函数作用域

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

##### P51～57 函数 & 方法

函数定义的三种方法：构造函数方式、函数表达式方式、函数声明方式

```javascript
//一：通过构造函数的方式，代码直接写在（）中
var fun = new Function("conslole.log('abc')");

//二：函数表达式方式，将匿名函数赋值给变量
var fun2 = function(...){...};

//三：函数声明的方式
function fun3(...){...};
                   
fun();
fun2();
fun3();
```

函数中可以封装一些代码，在需要时可以执行这些功能（代码）；

函数也是对象，具有对象的特点，如：fun2.hello = 'abc';

封装到函数中的代码不会立即执行，这些代码**会在函数调用时**执行。



**函数参数**

函数（）中可以指定一个或多个形参，形参之间用 "," 隔开，声明形参就相当于在函数内部声明了对应的变量，但是并不赋值；

在调用函数时，可以在（）中指定实参（实际参数），实参将会赋值给函数中对应的形参；

解析器也不会检查实参的类型，所以如果有可能接收到非法的参数，则需要对参数进行类型检查，

解析器也不会检查实参的数量，多余的实参不会被赋值；

如果实参数小于形参数，则没有对应实参的形参将是 undefined;

函数的实参可以是任意的数据类型，包括函数（对象）。



**函数返回值** 的类型 可以 是任意类型，包括函数；

**立即执行函数**

```javascript
(function(){
  alert("立即执行");
})();

(function(a, b){
  return a+b;
})(12, 58);
```

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
                         
//枚举 对象的属性               
for(var n in obj2){ //每循环一次，n 会得到一个 obj2 的属性名
  console.log(obj2[n]); //唯一的写法
}                         
```



##### P46～50 对象

对象是一种复合数据类型，在对象中可以保存多个不同数据类型的属性。

对象的分类：

1.内建对象：由 ES 标准中定义对象，在任何 ES 的实现中都可以使用；

​                      比如：Math、String、Number、Boolean、Function、Object 

2.宿主对象：由 JS 的运行环境提供的对象，目前主要是指由浏览器提供的对象；

​                      BOM、DOM

3.自定义对象：由开发人员自建的对象。

```javascript
//JS 对象的属性值，可以是任意的数据类型，包括对象
var obj = new Object();
obj.name = "zhu";
obj.age = 10;
obj["gender"] = "male"; //给属性赋值的另一种方式

delete obj.age; //删除 age 属性

//in 运算可以检查 对象 和 属性 是否相关
var isIn = "name" in obj; //'true' 
```

JS 中的变量都是保存在栈内存中，

基本数据类型的值 直接 在栈内存中存储，值与值之间独立存在，修改一个不会影响其他的变量；

对象 是保存在堆中的，每创建一个新的对象，就会在堆内存中开辟出一个新的空间，而变量保存的是对象的内存地址（对象的引用）；

##### [Relationship between JavaScript, APIs, and other JavaScript tools](https://developer.mozilla.org/en-US/docs/Learn/JavaScript/Client-side_web_APIs/Introduction#relationship_between_javascript_apis_and_other_javascript_tools)

So above, we talked about what client-side JavaScript APIs are, and how they relate to the JavaScript language. Let's recap this to make it clearer, and also mention where other JavaScript tools fit in:

- JavaScript — A high-level scripting language built into browsers that allows you to implement functionality on web pages/apps. Note that JavaScript is also available in other programming environments, such as [Node](https://developer.mozilla.org/en-US/docs/Learn/Server-side/Express_Nodejs/Introduction).
- Browser APIs — constructs built into the browser that sits on top of the JavaScript language and allows you to implement functionality more easily.
- Third-party APIs — constructs built into third-party platforms (e.g. Twitter, Facebook) that allow you to use some of those platform's functionality in your own web pages (for example, display your latest Tweets on your web page).
- JavaScript libraries — Usually one or more JavaScript files containing [custom functions](https://developer.mozilla.org/en-US/docs/Learn/JavaScript/Building_blocks/Functions#custom_functions) that you can attach to your web page to speed up or enable writing common functionality. Examples include jQuery, Mootools and React.
- JavaScript frameworks — The next step up from libraries, JavaScript frameworks (e.g. Angular and Ember) tend to be packages of HTML, CSS, JavaScript, and other technologies that you install and then use to write an entire web application from scratch. The key difference between a library and a framework is “Inversion of Control”. When calling a method from a library, the developer is in control. With a framework, the control is inverted: the framework calls the developer's code.



#### （资源1）菜鸟教程 - JS 

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

##### 全局、块级作用域

在 JavaScript 中, 全局作用域是针对 JavaScript 环境； 

在 HTML 中, 全局作用域是针对 window 对象；

使用 **var** 关键字声明的全局作用域变量属于 window 对象。

ES6 可以使用**let**关键字来实现块级作用域，ES6 之前，没有块级作用域的概念;

```javascript
{ 
    //let 声明的变量只在 let 命令所在的代码块 {} 内有效
    let x = 2;
}
// 这里不能使用 x 变量
```

**let** 关键字在不同作用域，或不同块级作用域中是可以重新声明赋值;

```javascript
let x = 2;       // 合法

{
    let x = 3;   // 合法
}

{
    let x = 4;   // 合法
}
```

**const** 用于声明一个或多个常量，声明时必须进行初始化，且初始化后值不可再修改;

```javascript
// 1.正确写法
const PI = 3.14159265359;

// 2.常量数组可以更新属性
// 创建常量数组
const cars = ["Saab", "Volvo", "BMW"];
 
// 修改元素
cars[0] = "Toyota";
 
// 添加元素
cars.push("Audi");

// 3.不能对常量数组重新赋值
cars = ["Toyota", "Volvo", "Audi"];    // 错误
```

##### **this 的多种指向:**

-  1、在对象方法中， this 指向调用它所在方法的对象。

-  2、单独使用 this，它指向全局(Global)对象。

-  3、函数使用中，this 指向函数的所属者。

-  4、严格模式下函数是没有绑定到 this 上，这时候 this 是 undefined。

-  5、在 HTML 事件句柄中，this 指向了接收事件的 HTML 元素。

-  6、在 JavaScript 中函数也是对象，对象则有方法，apply 和 call 就是函数对象的方法，允许切换函数执行的上下文环境（context）；

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

  ##### JSON:  **J**ava**S**cript **O**bject **N**otation

  通常用于服务端向网页传递数据，使用 JavaScript 语法，但是 JSON 格式仅仅是一个文本。

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

#### DOM

Each time your brower loads and displays a  page, it creates in memory an **internal representation of the page and all its elements**, the **Document Object Model** or DOM.

window.document,history,loaction.navigator

Math, Date



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



##### Date 处理日期与时间

```javascript
var d = new Date();
var d = new Date(milliseconds);
var d = new Date(dateString);
var d = new Date(year, month, day, hours, minutes, seconds, milliseconds);
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
    var biggesr = max(3, 4, 5);
    var height = round(76.35);
  }
```



#### 数据类型

**值类型(基本类型)**：字符串（String）、数字(Number)、布尔(Boolean)、空（Null）、未定义（Undefined）、Symbol。

Null 类型 的值只有一个 null，表示一个为空的对象。

Undefined 类型的值只有一个 undefined，只声明没赋值的 变量 值 为 undefined.

```javascript
var x = 5;
var y = "5";
x==y; //true
x===y;//false 既比较值，也比较类型

console.log(typeof x); //返回 "number"

var z = Number.MAX_VALUE; //JS 中可以表示的数字最大值
var z1 = z * z; //JS 中超过 Number.MAX_VALUE 的数字返回 Infinity，正无穷
var z2 = Number.MIN_VALUE; // 5e-324

var a = 'abc' * 'cdf';

console.log(a); //返回 "NaN" not a number
console.log(typeof a); //返回 "number"

//浮点数运算结果可能不精确
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

//转为 Boolean，Boolean()
//1. 数字 --> 除了 0 和 NaN，其他都转为 true
//2. 字符串 --> 除了 "" ，其他都是 true
//3. null undefined --> false

//关系运算符 > >= < <=
//返回 true 或者 false
//对于非数值的情况，会先转为数字再比较；任何值和 NaN 做任何比较，返回 false
var result = 10 > "hello"; //false
result = "11" < "5"; //true 注意：该例子为特例，如果两个String类型比较，不转为 数字，比较 Unicode 
```

**引用数据类型**：对象(Object)、数组(Array)、函数(Function)。

##### 对象由花括号分隔

```javascript
var person={firstname:"John", lastname:"Doe", id:5566};
//空行折行允许，下面与上同
var person={
firstname : "John",
lastname  : "Doe",
id        :  5566
};
//两种寻址方式：
name=person.lastname;
name=person["lastname"];

//for循环遍历
for (x in person){
		txt=txt + person[x] + " ";
	}
```

##### 数组

```javascript
//定义方式1
var cars=new Array();
cars[0]="Saab";
cars[1]="Volvo";
cars[2]="BMW";
//定义方式2
var cars=new Array("Saab","Volvo","BMW");
//定义方式3
var cars=["Saab","Volvo","BMW"];
```

”use strict“ 指令在 JavaScript 1.8.5 (ECMAScript5) 中新增，它不是一条语句，但是是一个字面量表达式，指定代码在严格条件下执行，严格模式下你不能使用未声明的变量。严格模式通过在脚本或函数的头部添加 **use strict**; 表达式来声明。

声明提升，初始化不提升

//...待补充 map() & filter()方法

//...待补充 箭头函数  ()=>语法

Arrow functions implicitly return the expression right after `=>`, so you didn’t need a `return` statement:

```
const listItems = chemists.map(person =>
  <li>...</li> // Implicit return!
);
```

However, **you must write `return` explicitly if your `=>` is followed by a `{` curly brace!** If you forget it, nothing gets returned!

//...待补充 foreach 循环 二维数组

//... ParseInt

##### 面对对象编程

定义对象的两种方式

```javascript
//方法1
var dog = {
  name: "Doudou",
  greet:function(){
    console.log(this.name + ":" + "Wang Wang!");
  }
};
dog.greet();

//方法2
var dog = new Object();
dog.name = "Doudou";
dog.greet = function(){
  console.log(this.name + ":" + "Wang Wang!");
};

dog.greet();
```

如上定义好的对象没法复用，如果想要复用，需要定义 对象类型，如下： 

对象类型的定义及使用方法

```javascript
//创建对象类型
function greetFunction(){
  console.log('Hi, I am ${this.first_name}${this.last_name}.')
}

//注意：名字首字母大写
function Person(first_name,last_name){
  this.first_name = first_name;
  this.last_name = last_name;
  this.greet = greetFunction;
};

var person = new Person("David", "Wang");
person.greet(); 
```

##### 浏览器内置对象

<u>window</u>.innerWidth. window.innerHeight .history.back()  , location.href

<u>navigator</u>.appVersion navigato.rappVersion, language, platform

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



### CSS：渲染HTML元素

内联样式-在HTML元素使用“style”属性

内部样式表-在<head>区域使用<style>元素来包含CSS

外部引用-使用外部CSS文件



### HTML：网页内容

CSS--网页布局

JS--控制网页行为

HTML文档=WEB页面；

###### HTML编辑器：

推荐：VS Code 或者 Sublime Text

缺省：记事本（Windows），TextEdit（OS X），LINUX用户可选：vi、vim、emacs

F12（Mac：Cmd+Opt+I））开启调试模式，Google Chrome浏览器下面；其他浏览器可通过菜单“More Tools/Developer Tools”进入调试；

调试的方法：https://zh.javascript.info/debugging-chrome 

HTML元素=HTML标签（HTML tag）

开始/开放标签(opening tag)，结束/闭合标签(closing tag)

使用“/”关闭空元素更长远，HTML、XHTML和XML都接受这种方式；

##### 常见标签

head, title, meta, style, script, noscript, base, link

body, h1~h7, br, hr, p, div, a, img, 

搜索引擎使用**标题**为网页的结构和内容编索引，用户可以通过标题来快速浏览网页，所以标题应该用来呈现文档结构；

**script**元素既可包含脚本语句，也可通过**source**属性指向外部脚本文件；

###### help：HTML标签参考手册 & HTML标准属性参考手册



##### 表单form

**单选按钮**可以设置以下几个属性：value、name、checked

-  value：提交数据到服务器的值（后台程序PHP使用）
-  name：为控件命名，以备后台程序 ASP、PHP 使用
-  checked：当设置 checked="checked" 时，该选项被默认选中

```
<form>
<p>你生活在哪个国家？</p>
<input type="radio" name="country" value="China" checked="checked">中国<br />
<input type="radio" name="country" value="the USA">美国
</form>
```

**注意：**同一组的单选按钮，name 取值一定要一致，比如上面例子为同一个名称“country”，这样同一组的单选按钮才可以起到单选的作用。

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

#### JSON数据API

https://jsonplaceholder.typicode.com/posts



#### RESTful API

Representational State Transfer

##### REST架构

1 每一个URL代表一种资源

2 客户端和服务器之间，传递资源的某种表现层（text，HTML，XML，JSON等）

3 客户端通过四个HTTP动词（GET，PUT，POST，DELETE），对服务器资源进行操作，实现“表现层状态转化”

#### 快捷键：

1 打开调试 窗 Console，Option+Command+I



#### 好用工具

1 JsonFormatter：可以把JSON格式显示成更易读的方式
