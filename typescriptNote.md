[用TypeScript编写React的最佳实践](https://blog.csdn.net/weixin_40906515/article/details/106798727) //。。。待完成

[Using ts to write react-router5](https://programming.vip/docs/using-typescript-to-write-react-router-5.html)

[李立超 TS 入门教程](https://www.youtube.com/watch?v=ExTfiyLmJPg&list=PLmOn9nNkQxJGwOhSsQ5H9JTPmiXGmy8Zw)

[bruce前端 TS快速入门](https://www.youtube.com/watch?v=GinkGJZBHIY&t=3529s)

#### React & TS 整合

 布鲁斯 1:59‘30“   2:04’~2:16' 

搜素：[create react app typescript](https://create-react-app.dev/docs/adding-typescript/)

```bash
//npm 或者 yarn 都可以，新建空项目
npx create-react-app my-app --template typescript
yarn create react-app my-app --template typescript
//加 TS 到已有项目
//@types/react: react的扩充包，为user提供react API及参数的类型
npm install --save typescript @types/node @types/react @types/react-dom @types/jest
yarn add typescript @types/node @types/react @types/react-dom @types/jest
```

修改 App 为箭头函数

增加 App 函数组件的类型  React.FC

增加函数组件 Title

修改 css 文件

定义传入Title组件的props类型为 TitleProps

使用 useState hook 时用到范型来定义 state 的类型

#### TS

TypeScript是一种由微软开发的开源、跨平台的编程语言。由于JavaScript语言本身的局限性，难以胜任和维护大型项目开发, 因此微软开发了TypeScript，使其能够胜任开发大型项目。TypeScript是JavaScript的一个超集，支持ES6标准，可以编译成纯JavaScript运行在任何浏览器上。

涵盖了环境搭建、TypeScript中的各种类型（基本类型、数组、对象、元组、枚举、unknown、any、void、never等）、TypeScript的编译选项，以及TypeScript中面向对象的相关知识（类、抽象类和接口），教程最后通过一个实战项目“贪食蛇”对知识进行了系统的串联。

**JS弊端**：

变量是动态类型，不固定；

写代码时不会报错，增加bug难度；

函数的入参没有类型，不易于维护 ；

##### **TS是什么？**

以 JS 为基础构建的是一种面向对象的强类型的编程语言，一个 JS 的超集；

可以在任何支持 JS 的平台中运行，但不能被 JS 解析器直接执行，需要先编译成 JS；

适合开发大型项目；

+变量类型，enum、interface

+支持 ES 的新特性

+新特性：抽象类、装饰器

+丰富的配置选项，可以设置编译后的 JS 版本

+强大的开发工具，如写代码时的提示

##### **语言特性**

+ 类型批注和编译时类型检查

- 类型推断
- 类型擦除
- 接口
- 枚举
- Mixin
- 泛型编程
- 名字空间/命名空间
- 元组
- Await

以下功能是从 ECMA 2015 反向移植而来：

- 类
- 模块化 / 模块
- lambda 函数的箭头语法
- 可选参数以及默认参数

##### **环境搭建**

因为 TS 解析器是用 Node 来写的，所以需要：

1. 下载安装 Node.js

2. 使用 npm 全局安装 TS

**基本语法：**

```typescript
//定义变量
const hello : string = "Hello World!"


//类、方法、对象
class Site { 
   name():void { 
      console.log("Runoob", 'abc'); //可以带两个参数 
   } 
} 
var obj = new Site(); 
obj.name();
```

##### 基础类型：

any、number、string、boolean、enum、void、null、undefined、never、symbol

```typescript
let binaryLiteral: number = 0b1010; // 二进制
let octalLiteral: number = 0o744;    // 八进制
let decLiteral: number = 6;    // 十进制
let hexLiteral: number = 0xf00d;    // 十六进制

let name: string = "Runoob";
let name1 = "Runoob"; //不用写 string，因为可以自动推导出类型
let flag: boolean = true;

// 在元素类型后面加上[]
let arr: number[] = [1, 2];

// 或者使用数组泛型
let arr: Array<number> = [1, 2];

// 元祖 表示已知元素数量和类型的数组，各元素的类型不必相同，对应位置的类型需要相同。
let x: [string, number];
x = ['Runoob', 1];    // 运行正常
x = [1, 'Runoob'];    // 报错
console.log(x[0]);    // 输出 Runoob

enum Color {Red, Green, Blue};
let c: Color = Color.Blue;

// --------------- function -----------------
// void 用于标识方法返回值的类型，表示该方法没有返回值。
function hello(): void {
    alert("Hello Runoob");
}

function hello1(a: string, b: string) {
    return a + b
}

// undefined
function hello2(name: string, age?: number) {
  let a: number
  if(number === undefined) return -1; // 排错机制
  a = number 
  return 2 * a;
}

// 箭头函数
const func = ()=>{  
}

//--------------- 断言  unknown  -----------------
// API 或者 Fetch 从后端来的资料，没有办法推导出类型 时 使用
// jsonplaceholder
type Data = {
  userId: number,
  id: number,
  title: string,
  completed: boolean
}

type Person = string //类型别名可以指代一个基础数据类型，interface没法

async function getData(){
  const res = await    fetch('https://jsonplaceholder.typicode.com/todos/1')
  const data = await res.json() as Data
}

const data1: Data = {
  userId: 1,
  id: 1,
  title: "delete something",
  completed: false
}

type Beta = {
  name: string
}

// 假设 data1 是动态的
const beta = data1 as unknown as Beta

// null 表示对象值缺失。
// undefined 用于初始化变量为一个未定义的值
// never 是其它类型（包括 null 和 undefined）的子类型，代表从不会出现的值。
```

##### 对象类型：

{}、Class、function、[]

变量命名规则：

不能使用 name 否则会与 DOM 中的全局 window 对象下的 name 属性出现了重名；

不能包含其他特殊字符， **_**  **$** 除外；

变量使用前必须先声明；

```typescript
//四种声明方式
var uname1:string = "Runoob";
var uname2:string; //初值为 undefined
var uname3 = "Runoob";//该变量可以是任意类型
var uname;//任意类型，默认初值 undefined
```

##### **联合类型**

联合类型（Union Types）可以通过管道(|)将变量设置多种类型，赋值时可以根据设置的类型来赋值。

```typescript
var val:string|number 
val = 12 
val = "Runoob" 
```

##### **可用运算符**

```
算术运算符 + - * / % ++ --
关系运算符 == != > < >= <=
逻辑运算符 && !! !
短路运算符 && !!
位运算符 & ! ~ ^ << >> >>>
赋值运算符 = += -= *= /=
三元运算符 ?:
负号运算符 -
字符串连接运算符 +
instance of
typeof
```

##### **数组声明**

```typescript
//一：先声明再初始化
var sites:string[]; 
sites = ["Google","Runoob","Taobao"] 
console.log(sites[0]); 
console.log(sites[1]);

//二：在声明时直接初始化
var nums:number[] = [1,2,3,4] 
```

使用**Array**初始化数组

```typescript
//一：指定数组初始化大小
var arr_names:number[] = new Array(4)  
for(var i = 0; i<arr_names.length; i++) { 
        arr_names[i] = i * 2 
        console.log(arr_names[i]) 
}

//二：直接初始化数组元素
var sites:string[] = new Array("Google","Runoob","Taobao","Facebook") 
```

##### 数组解构

```typescript
var arr:number[] = [12,13] 
var[x,y] = arr // 将数组的两个元素赋值给变量 x 和 y
```

```typescript
//数组迭代 - 遍历
var j:any; 
var nums:number[] = [1001,1002,1003,1004] 
 
for(j in nums) { 
    console.log(nums[j]) 
}
```

##### **可选参数**

在参数名旁使用`?`实现可选参数的功能，需要针对 undefined 情形进行处理；

```typescript
function buildName(firstName: string, lastName?: string) {
    if (lastName)
        return firstName + " " + lastName;  
	  return firstName;
}
 
let result1 = buildName("Bob");  // 正确
let result2 = buildName("Bob", "Adams", "Sr.");  // 错误，参数太多了
let result3 = buildName("Bob", "Adams");  // 正确
```

##### **剩余参数**

在TypeScript里，你可以把所有参数收集到一个变量里：

```
function buildName(firstName: string, ...restOfName: string[]) {
  return firstName + " " + restOfName.join(" ");
}

let employeeName = buildName("Joseph", "Samuel", "Lucas", "MacKinzie");
```

剩余参数会被当做个数不限的可选参数。 

##### **循环**

ES6 中引入 for...of 循环，以替代 for...in 和 forEach() ，并支持新的迭代协议。for...of 允许你遍历 Arrays（数组）, Strings（字符串）, Maps（映射）, Sets（集合）等可迭代的数据结构等。

```typescript
//-3. for 循环
//-2. ,while 循环
//-1. do...while 循环
//1. for...of 循环 
//允许遍历可迭代的数据结构 Arrays（数组）, Strings（字符串）, Maps（映射）, Sets（集合）等
let someArray = [1, "string", false];
for (let entry of someArray) {
    console.log(entry); // 1, "string", false
}
//2. for...in 循环
var j:any; 
var n:any = "a b c" 
for(j in n) {
    console.log(n[j])  
}
//3. forEach
// forEach、every 和 some 是 JavaScript 的循环语法
let list = [4, 5, 6];
list.forEach((val, idx, array) => {
    // val: 当前值
    // idx：当前index
    // array: Array
});
```

**编译选项** 6-9/30. 24-25/65 Jomy

tsc file.ts -w  //只编译指定文件，不使用  tsconfig.json，而是会使用默认自带的配置项

tsc //按照 tsconfig.json 中的配置进行编译，ts-node 也会使用

tsconfig.json -- [官网](https://www.typescriptlang.org/docs/handbook/tsconfig-json.html) 

include、exclude、extends、files、

**compilerOptions** 包含编译子选项

​	target //用来指定 ts 被编译为的 ES 的版本 "es 6"="es2015"

​	module //指定模块化的规范 “commonjs ”、"es2015"

​	lib //用来指定项目中使用的库，一般不用改，在node运行时要改

​	outDir//指定编译后文件所在的目录

​	rootDir //指定要编译的文件根目录

​	outFile//所有全局作用域中的代码编译输出到一 个文件 “outFile” = “./dist/app.js” - 用的不多，不够灵活，所以交给打包工具去做

​	allowJs //是否对js文件进行打包编译，默认false

​	checkJs //检查js代码是否符合ts语法规范

​	removeComments //编译时是否在js文件中移除注释

​	noEmit //不生成编译后的文件

​	noEmitOnError //当有错误时不生成编译后的文件	

​	alwaysStrict //设置编译后的文件是否使用严格模式

​	noImplicityAny //不允许隐式的any类型

​	noImplicityThis //不允许不明确类型的this

​	strictNullChecks //严格检查空值

​	strict //所有严格检查的总开关，包括👆四个 -- 建议打开

```json
{
  "compilerOptions": {
    "module": "esnext",
    "target": "es5",
    "lib": [
      "dom",
      "dom.iterable",
      "esnext"
    ],
    "baseUrl": "./",
    "allowJs": true,
    "skipLibCheck": true,
    "esModuleInterop": true,
    "allowSyntheticDefaultImports": true,
    "strict": true,
    "forceConsistentCasingInFileNames": true,
    "noFallthroughCasesInSwitch": true,
    "moduleResolution": "node",
    "resolveJsonModule": true,
    "isolatedModules": true,
    "noEmit": true,
    "jsx": "react-jsx"
  },
  "include": [
    "src"
  ]
}
```

##### 类型保护机制

Jomy 26/65

1. 类型断言的方式 ，利用自己对逻辑的了解

   ```ts
   interface Bird{
     fly:boolean,
     sing:()=>{}
   }
   interface Dog{
     fly:boolean,
     bark:()=>{}
   }
   function trainAnimal(animal: Bird | Dog){
     if(animal.fly){
       (animal as Bird).sing() //断言
     }else{
       (animal as Dog).bark()
     }
   }
   ```

2. in 语法做类型保护

   ```ts
   function trainAnimal1(animal: Bird | Dog){
     if('sing' in animal){//判断某个实例中是否有某方法
       animal.sing() 
     }else{
       animal.bark() //JS 类型推断
     }
   }
   ```

3. typeof 语法来做类型保护

   ```ts
   function add(first:string|number, second:string|number){
     if(typeof first==='string' || typeof second === 'string'){
       return `${first}${second}`
     }
     return first+second
   }
   ```

4. Instanceof 语法来做类型保护，必须使用类 class

   ```ts
   class NumberObj{ //必须是类 才能使用 instance
     count: number
   }
   
   function addSecond(first: object|NumberObj, second: object|NumberObj){
     if(first instanceof NumberObj &&
       second instanceof NumberObj){
       return first.count+second.count
     }
     return 0
   }
   ```

   

##### **声明文件**

 - 引用后，可以借用 TS 的各种特性来使用库文件了

以 **.d.ts** 为后缀；

```typescript
//使用 declare 定义类型，帮助 TS 判断传入的参数类型对不对
declare var jQuery: (selector: string) => any;

jQuery('#foo');
```

##### **使用 webpack 打包 ts 代码**  

10-12/30 part3

```bash
//1. 对项目进行初始化,生成 package.json,用来管理项目
$ npm init -y
//2. 装使用 webpack 需要的依赖，-D：开发
// 命令执行后，会去网上下指定的包，并写依赖到 package.json 文件
//webpack：打包工具核心代码
//webpack-cli：打包工具命令行工具
//typescript：ts 核心包
//ts-loader：webpack 的加载器，把 webpack 和 ts 进行整合，让 ts 编译器可以在 webpack 中使用
$ npm i -D webpack webpack-cli typescript ts-loader
```

//3. 手动新建并编写 webpack 的配置文件 webpack.config.js，如下：

```javascript
//引入 node.js 下面的 path 模块，用来拼接路径
const path = require('path');

//webpack 中 所有配置信息 写在 module.exports 中
module.exports = {

    //指定入口文件
    entry: './src/index.ts',

    //指定打包文件所在的目录
    output: {
        //指定打包文件的路径
        path: path.resolve(__dirname, 'dist'),
        //打包后生成的文件
        filename: "bundle.js"
    },

    //指定 webpack 打包时要使用的模块
    module: {
        //指定load的规则
        rules: [
            {
                //指定规则生效的文件
                test: /\.ts$/,
                //要使用的 loader
                use: 'ts-loader',
                //要排除的
                exclude: /node-modules/
            }
        ]
    }
}
```

//4. 创建 ts 编译配置文件

```json
 {
   "compilerOptions": {
    "module": "ES2015",
    "target": "ES2015",
    "strict": true
   }
 }
```

//5. Package.json 中 增加一行，使得可以通过 build 命令执行 webpack

```json
　"build":"webpack"
```

//6. 命令行执行打包

```
$ npm run build
```

//7. 安装 插件 使得可自动生成 html 文件

```bash
$ npm i -D html-webpack-plugin
```

新建文件 ./src/index.html；

配置 webpack.config.js，补充：

```js
const HTMLWebpackPlugin = require('html-webpack-plugin')

plugins: [
        new HTMLWebpackPlugin({
            //title: "自定义 title"
            template: "./src/index.html"
        }) //自动生成 html 文件，并引入资源
    ]
```

//8. 安装插件，相当于在项目中装上内置的开发服务器，该服务器与 webpack 有关联， 使得构建或代码修改完后 浏览器自动刷新

```bash
$ npm i -D webpack-dev-server
```

配置 package.json，补充：

```json
"build" : "webpack",
"start": "webpack serveƒ --open chrome.exe"
```

//9. 安装插件，每次重新编译前清理 dist 目录的旧文件

```bash
$ npm i -D clean-dev-server
```

配置 webpack.config.js，补充：

```js
//引入插件
const {CleanWebpackPlugin} = require('clean-webpack-plugin')

plugins: [
  			new CleanWebpackPlugin(),
        new HTMLWebpackPlugin({
            //title: "自定义 title"
            template: "./src/index.html"
        }) //自动生成 html 文件，并引入资源
    ]

//用来设置引用模块
resolve:{
  extensions: ['.ts', '.js']
}
```

//10. 装 Babel - 转新的 js 语法为 旧的，可以在不支持新语法的浏览器上运行，实现与不同浏览器的兼容



```bash
$ npm i -D @babel/core @babel/preset-env babel-loader core-js
```

babel-loader：帮助 webpack 打包，且只是webpack和babel做通信的一个桥梁，用了之后，webpack和babel做了打通，但 babel-loader并不会帮助我们把es6语法翻译成es5语法；

@babel/core：babel 的核心库；

@babel/preset-env：翻译es6成es5的规则；但有些新的语法，在低版本的浏览器里，实际上还是不存在的。虽然了语法翻译，但只翻译了一部分；

@babel/polyfill：将缺失的语法补充到浏览器里；

core-js 提供新的浏览器环境

```json
//指定 webpack 打包时要使用的模块
module: {
  //指定load的规则
  rules: [
    {
      //指定规则生效的文件
      test: /\.ts$/,
      use: [
        //配置 babel 新版 js --> 旧版 js
        {
          //要使用的 loader
          loader: 'babel-loader',
          options: {
            presets: [['@babel/preset-env', {
              useBuiltIns: 'usage',//使用corejs的方式:按需加载
              corejs: 3,//指定corejs版本
              targets: {//要兼容的目标浏览器版本
                "chrome": "88"
              }
            }]]
          }
        },
        'ts-loader',   //先执行：ts --> js
      ],
      //要排除的
      exclude: /node_modules/
    }
  ]
},
```



##### **面向对象**

抽象类和接口 -- Jomy 16/65

 - 程序中所有的操作都需要通过对象来完成

类：对象的模型

ts 的类 和 js 的类

```typescript
class Live {
  roomName: string
  private id: string //TS开发阶段防止外面引用，不影响JS
  protected name: string //子类可以读取
  
  constructor(roomName1: string, id1: string, name1: string) {
   	console.log("建立直播中...");
    this.roomName = roomName1
    this.id = id1
    this.name = name1
  }
}

const live = new Live('1号', '00001', 'bruce');
console.log(live.roomName); //其他两个属性不能这样用

class CarLive extends Live{
   constructor(roomName1: string, id1: string, name1: string) {
     super(roomName1, id1, name1)
   }
  start() {
    super.name //此处可以访问 父类 的 protected 属性
  	super.id
  }
}

const carLive = new CarLive('car room', '00002', 'bruce2')

// JS 私有属性的定义
class Live2 {
  #name   //私有属性定义,外面不能访问，调试窗打印不出来 
  constructor(name1: string) {
    this.#name = name1;
  }
}
//-----------------------------------------------------
//类属性 static
static age = 10;
//只读 readonly
readonly name = 'swk';

/** 抽象类
* 关键字 abstract，不能用来创建对象，专门用来被继承；
* 抽象类中可以添加抽象方法
*/
abstract class Animal{
  age:number;
	name:string;
  constructor(age:number, name:string){
    this.age = age;
    this.name = name;
  };
  
  // 抽象方法：abstract 开头，没有方法体
  // 抽象方法只能定义在抽象类中，必须被子类重写
  abstract sayHello(): void;
}
//继承
class Cat extends Animal{
  run(){
    console.log('${this.name}在跑');
  }
  //重写：子类覆盖掉父类的方法
  sayHello(){
    console.log("喵喵");
  }
}
```

##### **接口 Interface **

//... 接口 可索引的类型 & 既是函数又是对象 & 类静态部分与实例部分 [待完成](https://typescript.bootcss.com/interfaces.html)

- TS 中有，JS 中没有

一系列抽象方法的声明，是一些方法特征的集合，这些方法都应该是抽象的；

接口在TS编译成JS后会被剔除掉，只是编写代码时做提示用。 它只是 TypeScript 的一部分；

类型检查器只会去关注值的外形：只要传入的对象满足提到的必要条件，那么它就是被允许的；

类型检查器不会去检查属性的顺序，只要相应的属性存在并且类型也是对的就可以。

```typescript
// interface 和 type 相类似，但并不完全一致  -- 12/65 Jomy
// ?. readonly [propName:string] 可以继承 可定义方法 字符串索引签名
// readonly 只能在对象刚刚创建的时候修改其值
// [propName:string]字符串索引签名 - 前提是你能够确定这个对象可能具有某些做为特殊用途使用的额外属性
interface IPerson { 
    readonly firstName:string, 
    lastName:string, 
    [propName: string]: any; //字符串索引签名 -- 2.11/Jomy
    sayHi: ()=>string //定义方法特征，没有实现
} 
var customer:IPerson = { 
    firstName:"Tom",
    lastName:"Hanks", 
    sayHi: ():string =>{return "Hi there"} //实现
} 

// 接口定义函数类型
// 对于函数类型的类型检查来说，函数的参数名不需要与接口里定义的名字相匹配
// 函数的参数会逐个进行检查，要求对应位置上的参数类型是兼容的
interface SayHi{
  (word: string): string //调用签名
}

const say: SayHi = (wd: string) => {
  return wd
}

//接口还可以定义索引 //...待查
```

最简单判断该用`readonly`还是`const`的方法是看要把它做为变量使用还是做为一个属性。 做为变量使用的话用`const`，若做为属性则使用`readonly`。

```typescript
//自定义类型
type MyType = {
  name: string,
  age: number
}

/** 接口用来定义一个类结构，用来定义一个类中应该包含哪些属性和方法
* 同时接口也可以被当成类型声明去使用，下面两处声明合起来才是完整的定义；
*/
interface MyInterface{
  readonly name: string 
  age: number
}

interface MyInterface{
  gender: string
  school?: string //表可选，string | undefined
}

const obj : MyType = {
  name: 'sss',
  age: 111
}

const obj1 : MyInterface = {
  name: 'sss',
  age: 111,
  gender: 'male'
}

const obj2 = {
  name: 'sss',
  age: 111,
  gender: 'male',
  height: 142
}

const setObject = (obj:MyInterface, name:string):void=>{
  obj.name = name
}


setObject(obj2) //ok: 此时 TS编译器 不会特别严格，只会检查那些必需的属性是否存在，并且其类型是否匹配 MyInterface 的要求

setObject({
  name: 'sss',
  age: 111,
  gender: 'male',
  height: 142
}) //报错！因为当把一个字面量传给一个对象时，TS 会进行强校验
//==> TS 的类型校验特性
// 对象字面量会被特殊对待而且会经过额外属性检查，当将它们赋值给变量或作为参数传递的时候。 如果一个对象字面量存在任何“目标类型”不包含的属性时，你会得到一个错误。

//接口 - 只定义对象的结构，所有属性都不能有实际的值
interface MyInterface1{
  name: string //不能有实际的值
  sayHello(): void //抽象方法
}

/**
* 定义类时，可以使类去实现一个接口
* 实现接口就是使类满足接口的需求
*/
class MyClass implements myInterface1{
  name: string  //缺省 public，不能写成 private，因为接口中定义了该属性
  constructor(name: string){
    this.name = name
  }
  sayHello(){
    console.log('abc')
  }
}
```

当一个类实现了一个接口时，只对其实例部分进行类型检查，constructor存在于类的静态部分，所以不在检查的范围内 ；

当接口继承了一个类类型时，它会继承类的成员但不包括其实现。

##### **类的属性封装**

```typescript
// Getter/Setter方法：属性的存取器 -- 15/65
// 常用于 私有加密保护
class MyClass{
  private _name: string;
  private _age: number;
  
  constructor(n: string, a: number){
    this._name = n;
    this._age = a;
  }
  
  getName(): string {
    return this._name;
  }
  getAge(): number {
    return this._age;
  }
  setName(value: string){
    this._name = value;
  }
  setAge(value: number){
    this._age = value;
  }
}

const person = new MyClass('xiaohong', 15);
person.setName('xiaoming');

//TS 中，存取器的另一种写法 get name
//👆类中方法 getName() 可以换成下面的写法
get name(){
  return this._name;
}
set name(n: string){
  this._name = n;
}
//调用的地方（好像在直接使用属性）：
per.name; //相当于执行了 per.get name();

//其他几个(set name、get age、set age)类似
```

##### **在构造函数中定义类属性** 

构造函数在 new Person() 实例化一个对象的瞬间被自动调用；

 - ts语法糖

```typescript
class C{
  //可以直接将属性定义在构造函数中 - TS 简化写法
  cosntructor(public name: string, public age: number){
  }
}

//这种写法与👇传统写法等价
class C{
  name: string;
  age: number;
  
  constructor(n: string, a: number){
    this.name = n;
    this.age = a;
  }
}
//------------- parent / children ------------14/65
class Person{
  constructor(public name: string){}
}

class Teacher extends Person{
  constructor(public age: number){
    super('dell')//子类构造器必须通过 super 调用父类构造器
  }
}
```

##### 枚举类型

```ts
enum Status{
  OFFLINE,
  ONLINE=3,
  DELETED
}
console.log(Status.OFFLINE) //0 - 默认从 0 开始
console.log(Status.DELETED) //4
console.log(Status[0])  //OFFLINE 反向 查名称
```

**范型** **generic** - 为了能够重用不同类型参数但逻辑相同的代码

泛指的类型

在相同的函数或类定义里，通过使用不同的类型，该类型只有在使用的时候才决定；

在定义函数或类时，如果遇到类型不明确就可以使用范型；

可以直接调用具有范型的函数；

可以指定多个范型；

可以指定范型可以定义的范围；

```typescript
function print<T> (data: T) {
  console.log('data', data)
}
print<number>(999)
print<string>('yyy')
print<boolean>(true)

//-----------------------------------------------------
//普通函数
function fnOrigin(a: number): number{
  return a;
}

//使用范型 <T>写在()的前面
function fn<T>(a: T): T{
  return a;
}
//可以直接调用具有范型的函数
let result = fn(10); //不指定范型，TS 可以自动对类型进行推断
let result2 = fn<string>('hello'); //指定范型，适用于 TS 不好推断的情况

//下面两种写法等价
function map<ABC>(params: ABC[]){ 
  return params
}
function map<ABC>(params: Array<ABC>){ 
  return params
}
//------------------------------------------------------
//多个范型指定
function fn2<T, K>(a: T, b: K): T{
  console.log(b);
  return a;
}
fn2<number, string>(123, 'hello');
//也可以不写，TS 类型推断机制 会自动推断出 此时的 T 和 K
fn2(123, 'hello');

interface Inter{
  length: number;
}
//T extends Inter：表示范型 T 必须实现接口 Inter，也即：具有number类型的 length 属性
function fn3<T extends Inter>(a: T): number{
  return a.length;
}

fn3('abc');         //有效
fn3({length: 10});  //有效
fn3(123);           //编译错误，number 类型没有 length 属性

//------------------ 使用范型定义类 -----------------
class MyClass<T>{
  constructor(public name: T){}
}

const mc = new MyClass<string>('swk');
const mc1 = new MyClass(123); 

interface Item{
  name: string
}
class DataManager<T extends Item>{
  constructor(private data: T[]){}
  getItem(index: number):string{
    return this.data[index].name
  }
}
cosnt data= new Datamanager([
  {
    name: 'dell'
  }
])

// 约束传入的 T：只能是 number 或 string
class DataManager1<T extends number|string>{
  constructor(private data: T[]){}
  getItem(index: number):T{
    return this.data[index]
  }
}
```

利用范型声明类型 - 29/65 Jomy

```ts
// 如何使用范型作为一个具体的类型注解
function hello<T>(params: T){
  return params
}
const func: <T>(param: T) => T = hello
```

##### 命名空间 namespace

模块化的思想 - 30-31/65

page.ts

```ts
namespace Home {
  class Header {
    constructor() {
      const elem = document.createElement('div')
      elem.innerHTML = 'This is Header'
      document.body.appendChild(elem)
    }

  }

  class Content {
    constructor() {
      const elem = document.createElement('div')
      elem.innerHTML = 'This is Content'
      document.body.appendChild(elem)
    }
  }

  class Footer {
    constructor() {
      const elem = document.createElement('div')
      elem.innerHTML = 'This is Footer'
      document.body.appendChild(elem)
    }
  }

  export class Page {
    constructor() {
      new Header()
      new Content()
      new Footer()
    }
  }
}

```

index.html

```html
<script>
    new Home.Page()
  </script>
```

优化后：

tsconfig.json 使用 "outFile": "./dist/page.js"

page.ts 修改为：

```ts
///<reference path='./components.ts'/>

namespace Home {
  export class Page {
    constructor() {
      new Components.Header()
      new Components.Content()
      new Components.Footer()
    }
  }
}
```

其他 class 的定义放在 components.ts 中

命名空间 还可以导出 interface & namespace

32/65 

需要使用 require.js，来 配合解读 amd 生成的语法

采用 import 的方式 引入模块 //... 没明白，待复习

##### **parcel 打包** - 33/65

类似于 webpack 的工具，但是不需要额外配置

在 html 文件中直接引入 .ts 文件 

```bash
$ npm i -D parcel@next
```

 修改 package.json 文件

```json
"test": "parcel ./src/index.html"
```

##### **描述文件** .d.ts - 34-35/65

```ts
// 定义全局变量
declare var $: (param: () => void) => void

// 定义全局函数
declare function $(param: () => void): void

declare function $(param: string): {
  html: (html: string) => {}
}
```

```ts
$(function () {
   alert(123)
})

$(function () {
  $('body').html('<div>123</div>')
})
```

也可以使用接口来定义

```ts
// 使用 interface 的语法实现 函数重载
interface JQuery {
  (readyFunc: () => void): void
  (selector: string): JqueryInstance
}

declare var $: Jquery
```

对类进行类型定义

```ts
// 如何对对象进行类型定义，以及如何对类进行类型定义
// 使得 new $.fn.init() 有效
declare namespace $ {
  namespace fn {
    class init { }
  }
}
```

##### 模块化 - 36/65

以 ES6 为例讲解，也可以用类似的方法去学习 commonJS、umd 等

```bash
$ npm i -D jquery
```

##### keyof - 37/65

```ts
// 通过 keyof 实现将入参控制在 Person 现有的属性里面，且对返回值类型有正确的提示
interface Person {
  name: string
  age: number
  gender: string
}

class Teacher {
  constructor(private info: Person) { }

  getInfo<T extends keyof Person>(key: T): Person[T] {
    return this.info[key]
  }
}

const teacher = new Teacher({
  name: 'dell',
  age: 30,
  gender: 'male'
})

const test = teacher.getInfo['name']
```



##### **[Utility](typescriptlang.org/docs/handbook/utility-types.html)** 

TS 已经写好可以直接拿来用

Record<Keys, Type>

Pick<Type, Keys>

Omit<Type, Keys>

```typescript
const cats: Record<CatName, CatInfo> = {
  miffy: {age: 10, breed: "Persian"}
  boris: {age: 5, breed: "Maine Coon"} 
	mordred: {age: 14, breed: "British Shorthair"}
} 

interface Todo {
  title: string,
  description: string;
  completed: boolean;
  createdAt: number; 
}
type TodoPreview = Pick<Todo, "title" | "completed">
const todo: TodoPreview = {
  title: "Clean room",
  completed: false
}

type TodoPreview1 = Omit<Todo, "description">

```

##### 类型推断type inference

推断发生在初始化变量和成员，设置默认参数值和决定函数返回值时；

候选类型、最佳通用类型

如果没有找到最佳通用类型的话，类型推断的结果为**联合数组类型**，

“按上下文归类”：会发生在表达式的类型与所处的位置相关时

上下文类型表达式包含了明确的类型信息，上下文的类型被忽略；

使用场景通常包含： 函数的参数，赋值表达式的右边，类型断言，对象成员和数组字面量和返回值语句； 上下文类型也会做为最佳通用类型的候选类型。

##### 类型注解

```ts
// 函数 参数解构 的 类型注解 方式
// 第一种写法
function add2({ first, second }: { first: number, second: number }
): number {
    return first + second
}
const total11 = add2({ first: 1, second: 2 })

// 第二种，箭头函数 形式的
const add21 =
    ({ first, second }: { first: number, second: number }): number => {
        return first + second
    }
```

**Q&A:**

1 ts & tsx 

Use `.ts` for pure TypeScript files.

Use `.tsx` for files which contain JSX.

For example, a React component would be `.tsx`, but a file containing helper functions would be `.ts`.

add 包需要安装ts的type转译文件

2 怎么学 TS？

通读官网 Documentation 各个模块

TypeScript AST Viewer - 复杂语法 可以 给出抽象语法树

TS 如何 与第三方库配套使用

​	- 以 Redux 为例， Redux 官网搜索 TypeScript，可以找到 Usage with TS

#### 项目实战 - 前端 TS + react

5/65 TS 环境 配置 ‼️

工具 ts-node：可以把ts文件编译生成js文件并执行该js文件 = tsc + node

11/65 数组和元组 tuple

元组：长度固定，且每项类型固定的数组

```ts
class Teacher {
  name: string,
  age: number
}

// TS 不会强制要求每项必须得是new出的Teacher类，只要对象中也包含相同的类型匹配的字段也可，TS 也接受这样的赋值
const arr:Teacher[] = [
  new Teacher(),
  {
    name: 'Lisa',
    name: '40'
  }
]

// 元组的一个使用场景，处理 csv 文件
const teacherList:[string,string,number][]=[
  ['dell', 'male', 19],
  ['dun', 'male', 42],
  ['jenny', 'female', 40]
]
```

1 react cli 创建空项目

2 第三方库 antd，找到官网范例，直接copy想要的TS版本的代码到自己的项目，删掉不用的组件

3 通过Props范型通知组件可以接受的参数有哪些

4 前端请求api代理：

package.json 文件增加

"proxy":"http://localhost:7001"

作用：如果发现前端请求里面有 api 开头的，

比如：http://localhost:3000/api/isLogin 代理到：

http://localhost:7001/api/isLogin 这样的接口上

```ts
//'/api/...':前端请求的接口都用 api 作为前缀，前后端通信的常用方式
axios.get('/api/isLogin').then(res =>
            console.log(res))
```

4-1 到后端，补充接口 /api/isLogin

4-2 前端 Login 表单中增加 axios 请求，安装 qs，使得能过在 axios 请求中使用 表单 数据

```
$ npm i -D qs @types/qs
```

使用qs

```　ts
import qs from 'qs'

const onFinish = (values: any) => {
        axios.post('/api/post', qs.stringify({
            password: values.password
        }), {
            headers: {
                "Content-Type": "application/x-www-form-urlencoded"
            }
        })
    };

```

4-3 前端登陆 发送 axios 请求 60/65

4-4 前端 爬取 发送 axios 请求，如果成功，提醒 成功

4-5 使用 echarts（百度）来展示爬取到的信息在页面下半部分； 

GitHub 资料 [echarts-for-react]([echarts-for-react](https://github.com/hustcc/echarts-for-react))，到Echarts官网范例处拷贝 Option 信息；找到 EchartOption 作为 getOption 的返回类型

```bash
$ npm i -D echarts @types/echarts echarts-for-react
```

```ts
import ReactECharts from 'echarts-for-react'
<ReactECharts option={getOption()} />
```

```bash
$ npm i -D moment //转化时间        
```

```ts
import moment from 'moment'
times.push(moment(Number(i)).format('MM-DD HH:mm'))
```

4-6 爬取的数据展示在页面上

4-7 res.data.data --> res.data 使用 axios 拦截中间件实现

给从后端回来的数据加类型注解

4-8 解决前后端都需要的数据两边都需要定义的冗余问题

backend新增文件：responseResult.d.ts 定义后端需要返回的所有类型，修改使用的地方；

将该文件拷贝一份到 frontend，修改使用到的地方

可以引入同步，使得后端的 .d.ts 修改以后，可以自动同步到前端；

5 Node 爬虫 项目 - Jomy

对象：http://www.dell-lee.com/typescript/demo.html?secret=secretKey

里面每个课程的学习人数

5-1 新建文件夹 backend-ts-project

5-2 

```
cd backend-ts-project
$ npm init -y
$ tsc --init
$ npm i -D ts-node
$ npm i -D typescript
```

5-3 新增 src / crawler.ts

​      package.json + "dev": "ts-node ./src/crawller.ts"

```ts
console.log('hello')
```

定义类 Crawller

5-4 使用 superagent，使得在 node 里面也可以发送 Ajax 请求

```bash
$ npm i -D superagent @types/superagent
```

```ts
    private rawHtml = ''

    async getRawHteml() {
        const result = await superagent.get(this.url)
        this.rawHtml = result.text
    }

    constructor() {
        this.getRawHteml();
    }
```

5-5 把 html 文件中有用的内容提取出来，用到 cheerio - GitHub 官网看使用

```bash
$ npm i -D cheerio @types/cheerio
```

 使用类似于 JQuery 的语法

```ts
getCouseInfo = (html: string) => {
  const $ = cheerio.load(html)
  const courseItems = $('.course-item')
  console.log(courseItems.length); //4
}
```

5-6 优化代码，解藕函数 getRawHtml 和 getCourseInfo

5-7 打印结果到 json 文件

```ts
  async initSpiderProcess() {
        const html = await this.getRawHtml()
        const courseInfo = this.getCouseInfo(html)
        const fileContent = this.generateJsonContent(courseInfo)
        this.writeFile(JSON.stringify(fileContent))
    }
```

5-8 优化代码：21/65

将公用的爬虫部分和业务的处理解析分开，+dellAnalyzer

将 要爬取的链接 也 抽出来

+interface Analyzer 定义，让 DellAnalyser 实现 该接口

==> 如果需要换一种方式解析，定义一个新的类来实现 该 接口，并修改 定义分析实例 的类即可

5-9 单例模式复习 22/65

- 类不能被外部实例化 - 构造函数声明为 private
- 增加私有static实例
- 增加接口返回该实例

5-10 编译 23/65

提供给别人使用的应该是编译后的 build 目录中的，而不是 src 目录里的

- tsconfig 打开 "outDir": "./build"

- tsconfig 打开 "inlineSourceMap": true, 可以追踪到 ts 文件

- package.json +"build": "tsc -w"//自动监控ts文件的变化，并自动编译

- 安装 nodemon，配置 package.json - 使用方式参考 nodemon 官网

  ```json
    "scripts": {
      "build": "tsc -w",
      "start": "nodemon node ./build/crowller.js"
    },
    "nodemonConfig": {
      "ignore": [
        "data/*"
      ]
    },
  ```

  ts 文件变化 --build--> 自动编译成 .js --nodemon--> 运行 .js 文件 --> data/... 

- 安装 concurrently，使之可以并行执行 上面两条命令

  ```json
    "scripts": {
      "dev:build": "tsc -w",
      "dev:start": "nodemon node ./build/crowller.js",
      "dev": "concurrently npm:dev:*"
    },
  ```

  然后执行命令 npm run dev 即可

6 使用 Express 开启一个服务，让用户可以在浏览器上访问接口  38/65

6-1 新增 / src / index.ts 

6-2 package.json

	 + "rootDir": "./src"
	 + 修改："dev:start": "nodemon node ./build/index.js"
	 + 修改： "dev": "tsc && concurrently npm:dev:*"

6-3 安装

```bash
$ npm i -D express @types/express
```

6-4 index.ts 代码实现

```ts
import express, { Request, Response } from 'express'

const app = express()

app.get('/', (req: Request, res: Response) => {
    res.send('hello, I am express')
})
app.listen(7001, () => {
    console.log('server is running on 7001')
})
```

6-5 增加 router.ts

```ts
import { Router, Request, Response } from 'express'

const router = Router()

router.get('/', (req: Request, res: Response) => {
    res.send('hello, I am express')
})

router.get('/getData', (req: Request, res: Response) => {
    res.send('bye')
})

export default router
```

并修改 index.ts 文件如下

```ts
import router from './router'

const app = express()
app.use(router)
```

===> 最简版 Express 服务器 + 2 个 路由 ✅

6-6 在 router.ts 中使用 Crawller 39/65

使得在浏览器中，输入一次 localhost:7001/getData，data / course.json 中就多出一条记录

6-7 给 getData 接口 + 权限的校验，修改 router.ts 

```ts
router.get('/', (req: Request, res: Response) => {
    res.send(`
    <html>
        <body>
            <form method='post' action='/getData'>
            <input type='password' name='password'>
            <button>submit</button>
        </body>
    </html>
    `)
})

router.post('/getData', (req: Request, res: Response) => {
    const { password } = req.body
    if (password === '123') {
        const secret = 'secretKey'
        const url = `http://www.dell-lee.com/typescript/demo.html?secret=${secret}`

        const analyzer = DellAnalyzer.getInstance()
        new Crawller(url, analyzer)

        res.send('getDate success!')
    } else {
        res.send('password Error!')
    }
})
```

新问题：代码运行时报错，req.body 是 any 类型，但 TS 并没有提示语法错误 - 使用一些老的库 如 express 时，会有这样的问题，.d.ts 文件翻译的有问题；

-- 使用中间件来解决，使得 req.body 有内容，GitHub 找 body-parser

待补充：express 中间件的知识，使用次序等

在 index.ts 中 +

```ts
import bodyParser from 'body-parser' // ts 支持的 import

app.use(bodyParser.urlencoded({ extended: false }))
```

==> 浏览器 重新 输入 123 或者 456，运行正常  

发现问题：

1. express 库的 .d.ts 文件类型描述不准确
2. 当使用中间件的时候，对 req 或者 res 做了修改（比如 给 req 增加了字段）以后，实际上类型 Request 并不能修改，这样 新增的字段 无法在 TS 中 使用，因为与类型不匹配

6-8 + RequestWithBody 来解决上述问题 40/65

router.ts + 

```ts
interface BodyRequest extends Request {
    body: {
        [key: string]: string | undefined
    }
}
```

然后使用 Request 类型的地方 换成 BodyRequest

==> 解决上面第一个问题

+custom.d.ts 文件 && TS 类型融合

```ts
declare namespace Express {
    interface Request {
        teacherName: string
    }
} 
```

index.ts 中 增加

```ts
app.use((req: Request, res: Response, next: NextFunction) => {
    req.teacherName = 'dell'
    next()
})
```

router.ts 中使用

```ts
res.send(`${req.teacherName} password Error!`)
```

==>解决第二个问题

6-9 登陆功能开发 - 使用 cookie-session / GitHub 状态持久存储

```
$ npm i -D cookie-session @types/cookie-session
```

index.ts +

```ts
app.use(cookieSession({
    name: 'session',
    keys: ['teacher dell'],

    // Cookie Options
    maxAge: 24 * 60 * 60 * 1000 // 24 hours
}))
```

router.ts

```ts
const isLogin = req.session ? req.session.login : undefined
if (isLogin) {...}else{
  res.send('Please log in first!')
}
```

6-10 优化 +Utils文件夹

将业务相关的 ts 文件移入Utils 文件夹

+checkLogin 中间件，并在两个路由上使用

```ts
const checkLogin = (req: BodyRequest, res: Response, next: NextFunction) => {
    const isLogin = req.session ? req.session.login : undefined
    if (isLogin) {
        next()
    } else {
        res.send('please login in first!')
    }
}

router.get('/getData', checkLogin, (req: Request, res: Response) => {...
 })
```

 修改 读取文件的路径 crawller.ts 修改： 

```ts
 private filePath = path.resolve(__dirname, '../../data/course.json')
```

**类的装饰器** 44/65 难理解！

装饰器本身是一个函数，通过 @ 来使用，接收类构造函数为参数

使用多个装饰器时，先执行下面的

运行时机：被装饰的类创建好之后立即执行

 打开 tsconfig.json 中的 “experimentalDecrators” & "emitDecoratorMetadata"

```ts
function testDecorator(constructor: any){
costructor.prototype.getName = ()=>{
	console.log('dell')
}
}	
@testDecorator
class Test{} //执行装饰器

const test = new Test()
(test as any).getName() // dell:使用到装饰器添加的函数 
```

对装饰器 增加 是否执行的判断标识，使用工厂方法

```ts
function testDecorator(flag: boolean){
  if(flag){
   return (constructor: any){
		costructor.prototype.getName = ()=>{
		console.log('dell')
		}
	}	else{}
}

@testDecorator(true)
class Test{} //执行装饰器
const test = new Test() 
```

这样创建的装饰器 test.getName 时不会有提示信息，另一种方式来写装饰器

```ts
function testDecoratorFactory() {
    return function <T extends new (...args: any[]) => {}>(constructor: T) {
        // extend the original construactor
        return class extends constructor {
            name = 'lee'
            getName() {
                return this.name
            }
        }
    }
}

//1 run Factory to generate a  decorator
//2 use the decorator to decorate a class  without a name
//3 assign the decorated class to Test
const Test = testDecoratorFactory()(class {
    name: string
    constructor(name: string) {
        this.name = name
    }
})
```

**方法的装饰器**

key对应的是方法名字

普通方法，target对应的是类的 prototype

静态方法，target对应的是类的构造函数

```ts
// 与 Object.defineProperty() 的 参数很像 - developer.mozilla.org
function getNameDecorator(target:any, key:string, descriptor:PropertyDescriptor) {
    console.log(target)
}
//Test { getName: [Function] } 'getName'
//{ [Function:Test] getName: [Function] } 'getName'
class Test {
    name: string
    constructor(name: string) {
        this.name = name
    }
    @getNameDecorator
    getName() {
        return this.name
    }
}
```

访问器的 装饰器 只能 加在一个上面，原因可以查 TS 官网

属性装饰器 47/65 - error 待查...

TS  官网 / playground，左边显示 TS 代码，右边是生成的 JS 代码

**函数参数的装饰器** 48/65

Try-catch 反复编写的解决办法 -- 使用方法装饰器+工厂方法传参

50/65 - 没有声音

```bash
$ npm i -D reflect-metadata 
```

tsconfig.json 打开 两项：

```json
"target": "es5" // for (let key in target.prototype)) 才能进循环
"experimentalDecorators": true, /* Enable experimental support for TC39 stage 2 draft decorators. */
"emitDecoratorMetadata": true, 
```

Reflect.defineMetadata 语法 待补充//...

LoginController.ts + 

```ts
import 'reflect-metadata'

@controller
class LoginController {
    @get('/login')
    login() { }

    @get('/')
    home(req: BodyRequest, res: Response) {
        const isLogin = req.session ? req.session.login : undefined

        if (isLogin) {
            ...
        } else {
            ...
        }
    }
}
```

新增文件 decorator.ts +

```ts
export function controller(target: any) {
    for (let key in target.prototype) {
        const path = Reflect.getMetadata('path', target.prototype, key)
        const handler = target.prototype[key]
    }
}

export function get(path: string) {
    return function (target: any, key: string) {
        Reflect.defineMetadata('path', path, target, key)
    }
}
```

6-11 自动生成路由 get，利用装饰器 51/65

执行一遍 LoginController.ts 利用装饰器（先get再controller）生成路由；

方法：在 index.ts 中 import './controller/LoginController'；

将 logout 也迁移到 LoginController 中去

6-12 迁移 post 到新的代码结构中

增加：getRequestDecorator

6-13 迁移 getData & showData 到新的文件 CrawllerController.ts 中

checkLogin 中间件的使用，使用 装饰器 来解决

```ts
// factory
export function use(middleware: RequestHandler) {
    // return a real decorator
    return function (target: any, key: string) {
        Reflect.defineMetadata('middleware', middleware, target, key)
    }
}

export function controller(target: any) {
    for (let key in target.prototype) {
        const path = Reflect.getMetadata('path', target.prototype, key)
        const method: Method = Reflect.getMetadata('method', target.prototype, key)
        const middleware = Reflect.getMetadata('middleware', target, key)
        console.log(path, method, middleware);

        const handler = target.prototype[key]
        if (path && method && handler) {
            if (middleware) {
                router[method](path, middleware, handler)
            } else {
                router[method](path, handler)
            }

        }
    }
}

```

6-14 代码优化 

+文件夹 decorator 并且 添加文件，把装饰器逐个拆开保存到不同文件里：

controller.ts / index.ts / request.ts / 

给 any 类型的变量添加类型；

根目录下新建router.ts，只定义 router；

middleware 改成 middlewares，允许一个函数使用多个中间件，修改 controller.ts 对中间件的使用

#### TS官网都有啥

[JSDoc Reference](https://www.typescriptlang.org/docs/handbook/jsdoc-supported-types.html)

// @ts-check.  -- To enable errors in JavaScript files

// @ts-nocheck -- skip checking some files in jsconfig.json

// @ts-expect-err  or  // @ts-ignore or  --  ignore errors on specific lines

##### TS中

通过*类型断言*这种方式可以告诉编译器，“相信我，我知道自己在干什么”。

它没有运行时的影响，只是在编译阶段起作用。

类型断言有两种形式。 其一是“尖括号”语法：

```ts
let someValue: any = "this is a string";

let strLength: number = (<string>someValue).length;
```

另一个为`as`语法：

```ts
let someValue: any = "this is a string";

let strLength: number = (someValue as string).length;
```

两种形式是等价的。 至于使用哪个大多数情况下是凭个人喜好；然而，当你在TypeScript里使用JSX时，只有`as`语法断言是被允许的。

##### MDN

[Symbol](https://developer.mozilla.org/zh-CN/docs/Web/JavaScript/Reference/Global_Objects/Symbol)