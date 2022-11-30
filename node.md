### Node.js

(资源一)尚硅谷Node.JS全套完整版教程 李立超

(资源二) Node.js后端开发起手式 Tommy 视频教程

https://www.youtube.com/watch?v=a4AKxvsty9k

#### 环境（包括npm）安装

1. 命令行输入检查是否安装好：

   ```bash
   node -v
   v14.17.5
   ```

//2021-8-24

2. MacOS安装Node.js 

   https://nodejs.org/en/download/ 下载 pkg 安装包，直接点击安装即可

3. 把Creative网站的react项目跑起来：

   npm install 安装package里面配置的包

   npm start 启动项目

   npm build 打包项目成压缩包

   注：参考文件 tutorial-components.html

#### NPM

随同NodeJS一起安装的包管理工具，

```bash
npm -v

npm start
sudo npm install npm -g

npm install express
```

安装好之后，express 包就放在了工程目录下的 node_modules 目录中，因此在代码中只需要通过 **require('express')** 的方式就好，无需指定第三方包路径。

```javascript
var express = require('express');
```

如果全局安装，-g，安装包放在 /usr/local 下或者你 node 的安装目录，可以直接在命令行里使用。

查看全局安装的模块或某模块版本号

```bash
npm list -g
npm list express
```

卸载、更新、搜索模块

```bash
npm uninstall express
npm update express
npm search express
```

创建模块，package.json 文件是必不可少的。我们可以使用 NPM 生成 package.json 文件，生成的文件包含了基本的结果。

```bash
npm init
```

在 npm 资源库中注册用户（使用邮箱注册）

```bash
npm adduser
```

发布模块：

```bash
npm publish
```

##### Minification  为生产环境压缩 JS 代码

In production, it is recommended to minify any JavaScript code that is included with your application. **Minification can help your website load several times faster,** especially as the size of your JavaScript source code grows.

Here's one way to set it up:

1. [Install Node.js](https://nodejs.org/)
2. Run `npm init -y` in your project folder (**don't skip this step!**)
3. Run `npm install terser`

Now, to minify a file called `like_button.js`, run in the terminal:

```
npx terser -c -m -o like_button.min.js -- like_button.js
```

This will produce a file called `like_button.min.js` with the minified code in the same directory. If you're typing this often, you can [create an npm script](https://medium.freecodecamp.org/introduction-to-npm-scripts-1dbb2ae01633) to give this command a name.

**使用 [这个在线转换工具](https://babeljs.io/en/repl#?babili=false&browsers=&build=&builtIns=false&spec=false&loose=false&code_lz=DwIwrgLhD2B2AEcDCAbAlgYwNYF4DeAFAJTw4B88EAFmgM4B0tAphAMoQCGETBe86WJgBMAXJQBOYJvAC-RGWQBQ8FfAAyaQYuAB6cFDhkgA&debug=false&forceAllTransforms=false&shippedProposals=false&circleciRepo=&evaluate=false&fileSize=false&timeTravel=false&sourceType=module&lineWrap=true&presets=es2015%2Creact%2Cstage-2&prettier=false&targets=&version=7.4.3) 将 HTML 标签转换为 JSX 代码**

**针对生产环境的 JSX 设置**

在终端（命令行）中进入你的项目目录，粘贴并执行以下两条命令（**确保你已经安装了 [Node.js](https://nodejs.org/)！**）：

1. `npm init -y` （如果此命令执行失败，[请参考这个修复方法](https://gist.github.com/gaearon/246f6380610e262f8a648e3e51cad40d)）
2. `npm install babel-cli@6 babel-preset-react-app@3`

##### 运行 JSX 预处理器

你可以在每次保存 JSX 文件时执行预处理器，从而将 JSX 文件转换为一份新的、普通的 JavaScript 文件。

1. 创建一个名为 **src** 的目录
2. 在终端（命令行）中，运行以下命令：`npx babel --watch src --out-dir . --presets react-app/prod `（不需等待此命令执行完毕！此命令将为 JSX 文件启动一个自动监听器）。
3. 将 JSX 文件 - **like_button.js** - 移动到新创建的 **src** 目录下（或者创建一个 **like_button.js** 文件并包含此 [JSX 初始代码](https://gist.githubusercontent.com/rachelnabors/ffbc9a0e33665a58d4cfdd1676f05453/raw/652003ff54d2dab8a1a1e5cb3bb1e28ff207c1a6/like_button.js) 的文件）。

监听器将创建一个经过预处理的 **like_button.js** 文件，该文件中包含普通的、浏览器可执行的 JavaScript 代码。

#### package.json 

位于模块的目录下，用于定义包的属性。

main 字段指定了程序的主入口文件，require('moduleName') 就会加载这个文件。这个字段的默认值是模块根目录下面的 index.js。

##### 进程和线程

进程 - 负责为程序的运行提供必备的环境，相当于工厂的车间

线程 - 计算机中最小的计算单位，负责执行进程中的程序，相当于工人

JS代码的执行是单线程的

#### Node.js创建第一个应用 HTTP服务器

```javascript
//请求（require）Node.js 自带的 http 模块，并且把它赋值给 http 变量
var http = require('http'); 

//调用 http 模块提供的函数： createServer 。这个函数会返回 一个对象，这个对象有一个叫做 listen 的方法，这个方法有一个数值参数， 指定这个 HTTP 服务器监听的端口号。
http.createServer(function (request, response) {

    // 发送 HTTP 头部 
    // HTTP 状态值: 200 : OK
    // 内容类型: text/plain
    response.writeHead(200, {'Content-Type': 'text/plain'});

    // 发送响应数据 "Hello World"
    response.end('Hello World\n');
}).listen(8888);

// 终端打印如下信息
console.log('Server running at http://127.0.0.1:8888/');
```



```bash
node server.js
Server running at http://127.0.0.1:8888/
```
[Auth]
鉴权的流程大头在后端

HTTP 是一个无状态协议，所以客户端每次发出请求时，下一次请求无法得知上一次请求所包含的状态数据。

常见的验证方案包括：

Basic ( RFC 7617[2], Base64 编码凭证. 详情请参阅下文.),
Bearer ( RFC 6750[3], bearer 令牌通过OAuth 2.0保护资源),
Digest ( RFC 7616[4], 只有 md5 散列 在Firefox中支持, 查看 bug 472823[5] 用于SHA加密支持),
HOBA ( RFC 7486[6] (草案), HTTP Origin-Bound 认证, 基于数字签名),
Mutual ( draft-ietf-httpauth-mutual[7]),
AWS4-HMAC-SHA256 ( AWS docs[8])

1. HTTP Auth Authentication
2. Cookie + Session
3. JWT
4. OAuth

