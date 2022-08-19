#### 待整理 - 新知识点：

ComponentDidMount 函数 中 不使用 async + await；

ComponentDidUpdate 有两个入参：prevProp + prevState；

通读并背诵 axios 文档；

React 项目： axios + styled-component

Every time you get out of focus from the input field, the event blur（onBlur） will trigger.

React `onChange` gets triggered on every keystroke on the keyboard.
Use React `onChange` if you want to give your users a real-time experience or to update React state.

Use React `onBlur` if you want to execute code after they’re out of focus or make API calls.



#### Material UI

漂亮的 React 组件，实现更快、更轻松的 Web 开发体验

基本使用

[官网](https://material-ui.com)

[下一代版本](https://next.material-ui.com)(v5)



```bash
$ npx create-react-app muiweb
$ cd muiweb
$ npm i -D @mui/material @emotion/react @emotion/styled @mui/icons-material
$ npm start
```

依次安装：mui 下一个版本、他的 react 版本、样式表、图标

在 public/index.html 中增加外部第三方(google)字体和图标 //...语法待理解

```html
<Link 
      rel="stylesheet"
      href="https://fonts.googleapis.com/css?family=Roboto:300,400,500,700&display=swap"
     />
<Link 
      rel="stylesheet"
      href="https://fonts.googleapis.com/icon?family=Material+Icons"
     />
```

导入 Material UI [模版组件](https://material-ui.com/getting-started/templates)

【使用 SignIn】

创建文件 SignIn.js，

拷贝 mui 官网上对应模版的 js 版本的代码到 SignIn.js，

修改文件 App.js，删除不用的代码

【知识点 - Theme】

样式可让您为应用程序应用一致的音调；

`ThemeProvider` 依赖于 [React 的上下文（context）功能](https://reactjs.org/docs/context.html)来将主题传递给下级组件，所以你需要确保 `ThemeProvider` 是你试图自定义组件的父级组件；

.palette 调色板
.typography 文字铸排
.spacing 间距
.breakpoints 断点
.zIndex 层级
.transitions 过渡动画
.components 组件

##### 待补充知识点//...

【Grid】

【Card】

【Dialog】/【DialogContent】

#### react-beautiful-dnd

#### react-router-dom

[V6 与 V5 比较](https://www.bilibili.com/read/cv14409269)

[V6](https://reactrouter.com/docs/en/v6/getting-started/tutorial)

[V5](https://v5.reactrouter.com/web/guides/quick-start)

[跟山地人学React Router系列教程](https://www.youtube.com/playlist?list=PLA0YHwTjkRzvwpADLPCJoPCdfTSBshlM3)

Redirect、BrowserRouter、Switch、Link、Route、useParams

```react
//V5 下的导入方式，V6 不再导出 Switch 和 Route
import {
  BrowserRouter as Router,
  Switch,
  Link,
  Route
} from "react-router-dom";

<Link to="/home">to home</Link> //performs route jump

//下面这两种写 Route 的方式都可以
//use colons : to configure dynamic routes
<Switch>
  <Route exact path="/home" component={Home}/>
  <Route path="/about">
    <About />
  <Route path="/:id" children={<Child />} />
  </Route>
  ...
</Switch>

/* A <Route path> matches the beginning of the URL, not the whole thing. So a <Route path="/"> will always match the URL. Because of this, we typically put this <Route> last in our <Switch>. Another possible solution is to use <Route exact path="/"> which does match the entire URL. */

function Child() {
  // We can use the `useParams` hook here to access
  // the dynamic pieces of the URL.
  let { id } = useParams();

  return (
    <div>
      <h3>ID: {id}</h3>
    </div>
  );
```



```react
<div className="list-group">
  {/*
      原生html中，靠<a>标签跳转不同页面
      <a className="list-group-item active" href="./about.html">About</a>
      <a className="list-group-item" href="./home.html">Home</a>
  */}
	{/* 在react中靠路由链接实现切换组件 BrowserRouter 已包裹在App外 */}
   <Link className="list-group-item" to="/about">About</Link>
   <Link className="list-group-item" to="/home">Home</Link>
</div> 

//V5版本中注册路由，无需包裹<Routes>组件。而V6版本中则必须包裹。 
{/* 注册路由 */}
<Routes>
	<Route path="/about" element={<About />} />
	<Route path="/home" element={<Home />} />
</Routes>
```

useRouteMatch

```react
const Topics = () => {
let match = useRouteMatch()
return (
    <div>
      <ul>
        <li>
          <Link to={`${match.url}/components`}>Components</Link>
        </li>
      </ul>
      <Switch>
        <Route path={`${match.path}/:topicId`} component={Topic} />
        <Route path={match.path}>
          <h3>Please select a topic.</h3>
        </Route>
      </Switch>
    </div>
  );
}
export default Topics
```

useParams、Redirect、NavLink

- The `<NavLink>` is a special type of `<Link>` that can style itself as “active” when its `to` prop matches the current location.

```react
// @types/react-router/index.d.ts
export function 
useParams<Params extends { [K in keyof Params]?: string } = {}>(): Params

//The to property is used for redirection, 
//which is usually used in Switch as the processing of matching failure
<Redirect path="/companies/null" to="/firstlogin" />

//the active class name will be added to the matched component
//need to add the exact attribute
<NavLink to="/home">to home</NavLink>
<NavLink exact to="/other">to other</NavLink>
<NavLink to="/other/1">to other/1</NavLink>
```

useHistory、useQuery、useLocation

- `useHistory` gives access to the [`history`](https://v5.reactrouter.com/web/api/history) instance that you may use to navigate.
- `useLocation` returns the [`location`](https://v5.reactrouter.com/web/api/location) object that represents the current URL. You can think about it like a `useState`that returns a new `location` whenever the URL changes.

```react
import { useHistory } from "react-router-dom";

function HomeButton() {
  let history = useHistory();

  function handleClick() {
    history.push("/home");
  }

  return (
    <button type="button" onClick={handleClick}>
      Go home
    </button>
  );
}
//-----------------------------------------------------------
//location.state 里面可以取到
interface LocationState {
    from: {
        pathname: string;
    };
}  
let location = useLocation<LocationState>()
let auth = useAuth()

let { from } = location.state || { from: { pathname: "/" } };
let login = () => {
  auth.signin(() => {
    history.replace(from);
  });
}
```



#### [react前端与node后端交互](https://www.newline.co/fullstack-react/articles/using-create-react-app-with-a-server/)

```bash
$ git clone git@github.com:fullstackreact/food-lookup-demo
$ npm i && cd client && npm i && cd ..
$ npm start
$ git checkout starting-point //Removes the files inside client/
$ rm -r client
```

Install the dependencies for both.

##### What, exactly, is `react-scripts`?

#### `react-scripts`

`react-scripts` is an NPM package specifically for use with `create-react-app`. It's the "black box" which contains the essentials:

- Dependencies
  - Like Babel, ESLint, and Webpack.
- Configuration
  - Config files for Webpack, Babel and ESLint, both for development and production.
- Scripts
  - For instance, the command `react-scripts start` runs a script shipped with this package. It's responsible for ultimately booting the Webpack development server.

##### Why React app need its own server?

But why does our React app need its own server? And how are we going to get these two servers working together?

You can instruct Webpack you would like it to produce this bundle. `create-react-app` inserts a `build` command into `package.json`:

```bash
$ npm run build
```

This command kicks off Webpack and Webpack spits out a bundle. You could then serve the `index.html` from that bundle wherever you'd like.

//...待完成

//-----------------------------------------------------------------------------------------------------------------------------------

##### **useState & useEffect**

 - 最主要的

用Hook赋予元件状态、效果，例如：动态显示码表的时间

简单说：元件有了状态(State hook)后，而有了什么效果(Effect hook)

- 元件：码表的表面
- 状态：变动的秒数
- 效果：因为秒数变动了，所以显示出减少的样子，或者做其他的事情等等...

其他 hooks：useCallback、useMemo、memo、useContext

在这之后：

- 学 React-Router - 换页
- React Context - 管理共用状态
- 理解为什么需要 Redux - 超大型应用才需使用
- 学习Class写法

不管使用什么前端框架，都需要用到 webpack 来帮忙打包；

- 将比较新的语法如箭头函数转为浏览器能认识的语法
- 最终打成三大件：html、css、js

eject：会把隐藏的档案显示出来

index.js： webpack 设定的项目入口

react： 提供API、元件、hook 的写法

react-dom ：如果网页是张白纸，帮我们把写好的元件画在纸上，通过 ReactDOM.render

JSX：用写 html 的方式来写 js 的物件

className：来写组件的css，因为 class 是 js 的关键字

删掉不用的文件

JSX 17 开始有做优化，所以可以不用写 import React from 'react'

如果把component指定在 index.js 中，其他文件引用时只用写到 文件夹即可，不用写成 './pages/Home/index.js'

有很多写css的方式，比如把 css 和 js 写在一起，用物件把样式带入 js 里面；或者 styled components

使用阵列的方式做到：元件最小化，可以在更多的地方重复利用

无论 使用 html 还是 react 来写前端，第一步：切版；

第二步：怎么分状态

props 传入  水管的概念

```
               Home (State) data
             /      \ (props)
    (state) Edit     List 
                      \
                     Item
           
a 0 a 0
b 1 c 1
c 2
```

临时变量 a，点击按钮“加法”触发 plus 后，界面上的值不变；因为 ReactDOM 不认识 a，不知道 a 跟画面有关；

将 a 改成 使用 useState 来声明并初始化；

react 渲染机制：用 useState 来声明变量的话，可以将该变量跟 react 的渲染机制绑定在一起；如果值变化了，会重新渲染；

```react
// 拿到上一次的值，在此基础上 增加
setA(function (prev) {
​            return prev + 11;
​        })
```

如果一连串的setA操作，会被优化合并 

Index 做 key 的方式，不行，因为 index 是用来唯一代表某个 item，但是如果item增删后 index 会变，所以：index 无法代表某个唯一的 item

怎么拿 input 的值？

​	JS 下面：onChange / event.target.value

​                    getElementById.value

​	react：每一个输入的地方 绑定 一个 state，双向绑定                

```react
const [note, setNote] = useState("");

function noteChange(e){
	setNote(e.target.value)
}

<input type="text" value={note} onChange={noteChange}/>
```

推荐 采用 解构的方式来取对象的属性值；

npm i prettier //将代码变漂亮的包

 npm i uuid // 帮忙产生唯一的id 

用 filter 实现删除功能

第三步：useEffect

组件第一次渲染 + 当绑定的状态或变数更新时，会调用 第一个参数 传进来的函数；

如果依赖的变数为空，则 只会执行一次；

假如不加 []，只传一个参数的话，每次渲染都会执行；

```
import {useEffect} from 'react'

useEffect(()=>{
	window.alert("新增成功")
	return ()=>{
		//下一次渲染前会执行，取消绑定
	}
}, [data]) 
```

使用 json-server 来模拟后端API

```
npm i json-server
创建 db.json 文件，代表会从后端拿回的东西

package.json 文件设置 scripts:{...
"server": "json-server --watch db.json"}

//从后端拿数据 
  useEffect(() => {
        fetch("http://localhost:3000/posts/1")
            .then(res => res.json())
            .then(data => {
                console.log(data);
            })
    }, [])
新建文件 constants.js 
也可以将上面的代码改成一个函数，用看似同步的方式处理非同步
async function fetchData(setData) {
    const res = await fetch(API_GET_DATA)
    const { data } = await res.json()
    setData(data)
}
useEffect 本身不支持 sync
```

data 数据改变的时候，发送到后端，useEffect + fetchSetData

使用 useRef 加保护 判断一件事情该不该做，比如：该不该把data提交到远端库

//---------------------------------------------------------------------------------------

缺省空模版

```javascript
import React,{Component} from 'react';

export default class Welcome extends Component{
  constructor(){
    super();
    this.state = {
      username : ""
    }
  }
  render(){
    return(
      <div>
      </div>
      )
  }
}
```

#### React Basic

##### create-react-app

sudo npm uninstall -g create-react-app 可以解决 权限不足的问题

```bash
npm i create-react-app -g //全局安装命令
create-react-app -V //查看版本号

```

使用create-react-app 自动创建的项目基于 Webpack（CommonJS 模块系统）+ ES6 。

```bash
npm install -g create-react-app
create-react-app my-app

//或者上面两行可以用下面来代替，效果相同
npx create-react-app my-app

cd my-app/
npm start
```

React 很重要的一个设计理念：all in js

PWA - progressive web application，理念：通过写网页的形式来写手机 App 应用

registerServiceWorker - 引入了 该模块的 网页，如果上传到一个支持 https 协议的服务器上后，会具有这样的特性：当用户第一次访问该网页时，需要连网才可以看到fn该网页，但是，假如断网了，下次登陆即使没有网络连接，也可以看到之前的页面；因为 registerServiceWorker 会帮助把之前的网页存储在浏览器之内。

**目录结构介绍**：

```
-- public
|		 |----favicon.ico  - 项目左上角的小图标
|    |--*-index.html - html 模版 title - tab显示的名字
|    |----manifest.json - 定义了网页当成 App 时快捷方式
|
-- src 所有源代码
     |--*-index.js - 整个程序运行的入口，引入 App.js，并渲染 
 		 |----logo.svg - 旋转的图片
     |--*-App.js - 负责要显示的内容 
     |----registerServiceWorker.js
     |----App.test.js - 自动化测试

👆最重要的只有三个文件：*
```

```react
import ReactDOM from 'react-dom'
...
ReactDOM.render(<App />, document.getElementById('root'))
```

React-dom：第三方的模块，有个方法 render 可以把一个组件挂载到某一个 dom 节点上；

使用 jsx 语法的地方一定要 import React from 'react'，否则编不过； 

render() 函数中的 <div> 也是 jsx 语法；

##### Elements

元素是构成 React 应用的最小单位，它用于描述屏幕上输出的内容，要将React元素渲染到根DOM节点中，通过把它们都传递给 **ReactDOM.render()** 的方法来将其渲染到页面上：

```react
<div id="example"></div>

const element = <h1>Hello, world!</h1>; //neither a string nor HTML,-->JSX 
ReactDOM.render(
    element,
    document.getElementById('example')
);
```

##### 虚拟 DOM

1. state 数据
2. JSX 模版
3. 数据 + 模版 结合，生成真实的 DOM，来显示
4. state 发生改变
5. 数据 + 模版 结合，生成真实的 DOM，替换原来的 DOM

缺陷：

第一次生成了一个完整的 DOM 片段

第二次生成了一个完整的 DOM 片段

第二次的 DOM 替换第一次的 DOM，非常耗性能

1. state 数据
2. JSX 模版
3. 数据 + 模版 结合，生成真实的 DOM，来显示
4. state 发生改变
5. 数据 + 模版 结合，生成真实的 DOM，并不替换原始的 DOM
6. 新的 DOM（DocumentFragment） 和原始的 DOM 做对比，找差异
7. 指出 input 框发生了变化
8. 只用新的 DOM 中的 input 元素，替换掉老的 DOM 中的 input 元素

缺陷：

性能的提升并不明显

1. state 数据

2. JSX 模版

3. 数据 + 模版 结合，生成真实的 DOM，来显示

   < div id='abc'>< span>hello world</ span></ div>

4. 生成虚拟 DOM（虚拟DOM 就是一个 JS 对象，用它来描述真实 DOM）- 损耗了性能

   ['div', {id: 'abc'}, ['span', {}, 'hello world']]

5. state 发生改变

6. 数据 + 模版 生成新的 虚拟 DOM - 极大地提升了性能

   ['div', {id: 'abc'}, ['span', {}, 'bye']]

7. 直接比较原始虚拟 DOM 和新的虚拟 DOM 的区别，找到区别是 span 中内容 - 极大地提升性能

8. 直接操作 DOM，改变 span 中的内容

##### 生命周期函数

![image-20220511101639037](/Users/lisahuang/Library/Application Support/typora-user-images/image-20220511101639037.png)

##### [Introducing JSX](https://reactjs.org/docs/introducing-jsx.html)

1. JSX produces React “elements”. 

   ```react
   const element = <h1>Hello, world!</h1>; //neither a string nor HTML,-->JSX 
   ```

2. You can put any valid [JavaScript expression](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Guide/Expressions_and_Operators#Expressions) inside the curly braces in JSX.

   在 JSX 的属性中嵌入 JavaScript 代码，使用花括号，*不能*使用引号；

   Curly braces let you bring JavaScript logic and variables into your markup.

   `{{` and `}}` is not special syntax: it’s a JavaScript object tucked inside JSX curly braces.

3. 空标签立即关闭

4. 返回一个顶层标签：组件不能返回多个并列最高层级的 JSX 标签，你必须为所有最高层级的标签添加一个共同的父标签，例如使用 <div>...</div> 或 <>...</> 作为父标签：

   you can write `<>` and `</>`, this empty tag is called a *[React fragment](https://reactjs.bootcss.com/learn/TODO)*.

   <></> 与  <React.Fragment></React.Fragment> 等价

5. JSX attributes inside quotes are passed as strings.

   They work inside the JSX tag content or immediately after `=` in attributes.

6. camelCase most of the things!

**Note:** The `class` is an **HTML Attribute**, while the `className` is a **DOM Property**.

```react
function formatName(user) {
  return user.firstName + ' ' + user.lastName;
}

const user = {
  firstName: 'Harper',
  lastName: 'Perez'
};
const element1 = (//2. example of "{js expression} in JSX"
  <h1>
    Hello, {formatName(user)}!  
  </h1>
);

ReactDOM.render(
  element, 
  document.getElementById('root')
);
```

```react
//3. If a tag is empty, you may close it immediately with />
const element = <img src={user.avatarUrl} />;

//4. JSX tags may contain children，返回一个顶层标签，而且需要加():
const element = (
  <div>
    <h1>Hello!</h1>
    <h2>Good to see you here.</h2>
  </div>
);
```

```react
//5. JSX 嵌入属性
return (
  <img
    className="avatar" //JSX attributes inside quotes are passed as strings
    src={user.imageUrl}
  />
);
```

[SVG](https://developer.mozilla.org/en-US/docs/Web/SVG) is an [XML](https://developer.mozilla.org/en-US/docs/Web/XML) language, similar to [XHTML](https://developer.mozilla.org/en-US/docs/Glossary/XHTML), which can be used to draw vector graphics, such as the ones shown to the right. 

##### [html --> JSX  Converter](https://transform.tools/html-to-jsx)

```react
function Profile(props) {
  return (
    <div className="card">
      <Avatar {...props} />  //This forwards all of Profile’s props to the Avatar
    </div>
  );
}
```

let定义变量，可以改变值；

Num = 0, { **Num** && name}，依旧会渲染，{ **Num>0** && name}，不渲染，因为第一个为false；

Save some JSX to a variable and then include it inside other JSX by using {}.



What do you do when each item needs to <u>render not one, but several DOM nodes</u>?

The short `<> </>` fragment syntax won’t let you pass a key, so you need to either group them into a single `<div>`, or use the slightly longer and more explicit `<Fragment>` syntax:

```react
import { Fragment } from 'react';

// ...

const listItems = people.map(person =>
  <Fragment key={person.id}>  //为了+key
    <h1>{person.name}</h1>
    <p>{person.bio}</p>
  </Fragment>
);
```



##### Babel： JSX-->react

```react
const element = (
  <h1 className="greeting">
    Hello, world!
  </h1>
);

//Babel compiles JSX down to React.createElement() calls.
const element = React.createElement(
  'h1',
  {className: 'greeting'},
  'Hello, world!'
);

//React.createElement() performs a few checks to help you write bug-free code 
//but essentially it creates an object like this:
const element = {
  type: 'h1',
  props: {
    className: 'greeting',
    children: 'Hello, world!'
  }
};
```

##### 组件

```react
function HelloMessage(props) {
    return <h1>Hello {props.name}!</h1>;
}

{/*<>赋值语法：JSX*/}
const element = <HelloMessage name="Magi"/>; //react函数组件 的使用 & 赋值
 
ReactDOM.render(
    element,
    document.getElementById('example')
);
```

使用 ES6 class 来定义一个组件 -- 尽量不用，改用函数代替

```React
class Welcome extends React.Component {
  render() {
    return <h1>Hello World!</h1>;
  }
}
```

新React里， 组件就是 JS函数（function），返回由标签语言编写的用户界面，👆与👇等价：

```react
function Welcome() {
  return (
    <h1>Hello World!</h1>
  );
}
```

//类组件里面 state 的使用方法

```react
class Clock extends React.Component {
  constructor(props) {
    super(props);
    this.state = {date: new Date()}; //键值对 赋值
  }
 
  render() {
    return (
      <div>
        <h1>Hello, world!</h1>
        <h2>现在是 {this.state.date.toLocaleTimeString()}.</h2>
      </div>
    );
  }
}
 
ReactDOM.render(
  <Clock />, 
  document.getElementById('example')
);
```

##### 引入模块

```javascript
// Importing a specific API:
import { render } from 'react-dom';

// Importing all APIs together:
import * as ReactDOM from 'react';
```

```react
ReactDOM.render(
  <React.StrictMode>
    <App />
  </React.StrictMode>, 
  document.getElementById('root')
);
```

```html
<!-- HTML > HTML 没掌握的标签 使用小结 <-->
<!--> time: HTML5新 <-->
<p>我们在每天早上 <time>9:00</time> 开始营业。</p>   //???用处 24/11/2021 LISA
 
<p>我在 <time datetime="2016-02-14">情人节</time> 有个约会。</p>

<!-->nav，main，section<-->
<nav id="navigation"></nav>
<main>
  <p>This paragraph is not rendered by React (open index.html to verify).</p>
  <section id="comments"></section>
</main>

<input placeholder="Type something here" />  //关键字palceholder??? 24/11/2021
<img  src="https://i.imgur.com/MK3eW3As.jpg"  alt="Katherine Johnson" />
```

当 React 元素为用户自定义组件时，它会将 JSX 所接收的属性（attributes）以及子组件（children）转换为单个对象传递给组件，这个对象被称之为 “props”。

##### 函数入参 children

```react
export function Comments() {
  return (
    <> 
      <h2>Comments</h2>
      //自己定义的组件，以下两种调用方式均可
      <Comment text="Hello!" author="Sophie" >jjj</Comment> 
      <Comment text="How are you?" author="Sunil" />
    </>
  );
}

function Comment({ text, author, children }) { //children!!! 必须是，不能改成其他名字
  return (
    <p>{text} — <i>{author}</i>{children}</p>
  );
}
//👆等价于
function Comment(props) { //children!!! 必须是，不能改成其他名字
  return (
    <p>{props.text} — <i>{props.author}</i>{props.children}</p>
  );
}
```

//上面的调用结果如下  注意：children的用法

Hello! — *Sophie*jjj

How are you? — Sunil

##### Render函数

###### When not to use it //。。。不理解，要补

- If your app uses server rendering and generates HTML on the server, use [`hydrate`](https://reactjs.bootcss.com/reference/TODO) instead of `render`.

- If your app is fully built with React, you shouldn’t need to use `render` more than once. If you want to render something in a different part of the DOM tree (for example, a modal or a tooltip), use [`createPortal`](https://reactjs.bootcss.com/reference/TODO) instead.

  

  Calling render repeatedly is similar to calling setState—in both cases, React avoids unnecessary DOM updates.

  #### Import & Export

  Either `'./Gallery.js'` or `'./Gallery'` will work with React, though the former is closer to how [native ES Modules](https://developer.mozilla.org/docs/Web/JavaScript/Guide/Modules) work.

  | Syntax  | Export statement                      | Import statement                        |
  | ------- | ------------------------------------- | --------------------------------------- |
  | Default | `export default function Button() {}` | `import Button from './button.js';`     |
  | Named   | `export function Button() {}`         | `import { Button } from './button.js';` |

  **对象数组的导出**

  ```javascript
  //data.js
  export const people = [{
    id: 0, // Used in JSX as a key
    name: 'Creola Katherine Johnson',
    profession: 'mathematician',
    accomplishment: 'spaceflight calculations',
    imageId: 'MK3eW3A'
  }, {
    id: 1, // Used in JSX as a key
    name: 'Mario José Molina-Pasquel Henríquez',
    profession: 'chemist',
    accomplishment: 'discovery of Arctic ozone hole',
    imageId: 'mynHUSa'
  }]
  ```

  ```javascript
  //App.js
  import { people } from './data.js';
  export default function List() {
    const listItems = people.map(person =>
      <li key={person.id}>
        <img
          src={getImageUrl(person)}
          alt={person.name}
        />
        <p>
          <b>{person.name}</b>
            {' ' + person.profession + ' '}
            known for {person.accomplishment}
        </p>
      </li>
    );
    return <ul>{listItems}</ul>;
  }
  ```

  



//待复习 29/11/2021

- How to move data out of components and into data structures like arrays and objects.



```react
const poem = {
  lines: [
    'I write, erase, rewrite',
    'Erase again, and then',
    'A poppy blooms.'
  ]
};
var c = poem.lines.length; //取array长度
```



 [a pure function](https://wikipedia.org/wiki/Pure_function) is a function with the following characteristics:

- **Minds its own business.** It does not change any objects or variables that existed before it was called.
- **Same inputs, same output.** Given the same inputs, a pure function should always return the same result.

React offers a “**Strict Mode”** in which it calls each component’s function twice during development. **By calling the component functions twice, Strict Mode helps find components that break these rules.**

In React there are three kinds of inputs that you can read while rendering: [props](https://reactjs.bootcss.com/learn/passing-props-to-a-component), [state](https://reactjs.bootcss.com/learn/state-a-components-memory), and [context](https://reactjs.bootcss.com/learn/passing-data-deeply-with-context). You should always treat these inputs as read-only.

When you want to *change* something in response to user input, you should [set state](https://reactjs.bootcss.com/learn/state-a-components-memory) instead of writing to a variable. 

To opt into Strict Mode, wrap your root component into `<React.StrictMode>`.



However, it’s fine because you’ve created them *during the same render*, inside `TeaGathering`. No code outside of `TeaGathering` will ever know that this happened. This is called **“local mutation”**—it’s like your component’s little secret.

```react
function Cup({ guest }) {
  return <h2>Tea cup for guest #{guest}</h2>;
}

//Local mutation
export default function TeaGathering() {
  let cups = [];
  for (let i = 1; i <= 12; i++) {
    cups.push(<Cup key={i} guest={i} />);  //数组的push操作，元素为 JSX 片段
  }
  return cups;
}

```

Event handlers are functions that React runs when you perform some action—for example, when you click a button. Even though event handlers are defined *inside* your component, <u>they don’t run *during* rendering</u>! **So event handlers don’t need to be pure.**

You can still attach it to your returned JSX with a [`useEffect`](https://reactjs.bootcss.com/reference/useeffect) call in your component. This tells React to execute it later, after rendering, when side effects are allowed. 

//怎么理解下面粗体字？ 29/11/2021 LISA

**Express your component’s logic in the JSX you return**. When you need to “change things,” you’ll usually want to do it in an event handler. 

##### 事件响应

Define a function and [pass it as a prop](https://reactjs.bootcss.com/learn/passing-props-to-a-component) to the appropriate JSX tag.

```react
export default function Button() {
  //1. Define
  function handleClick() {   
    alert('You clicked me!');
  }

  return (
    <button onClick={handleClick}>
      Click me
    </button>
  );
}

```

Pass correctly

```react
<button onClick={handleClick}>  //passing a function -1 
<button onClick={() => alert('You clicked me!')}> //passing a function -2 
<button onClick={handleClick()}> //calling a function -1
<button onClick={alert('You clicked me!')}> //calling a function -2
```

All events propagate in React except `onScroll`, which only works on the JSX tag you attach it to.

You can catch all events on child elements by adding `Capture` at the end of the event name:to catch all events on child elements.

```react
<div onClickCapture={() => { /* this runs first */ }}>
  <button onClick={e => e.stopPropagation()} />
  <button onClick={e => e.stopPropagation()} />
</div>
```

Each event propagates in three phases: 

1. It travels down, calling all `onClickCapture` handlers.
2. It runs the clicked element’s `onClick` handler.
3. It travels upwards, calling all `onClick` handlers.

A `<form>` submit event, which happens when a button inside of it is clicked, will reload the whole page by default.

```react
export default function Signup() {
  return (
    <form onSubmit={e => {
      e.preventDefault(); // Preventing default behavior from happening:
      alert('Submitting!');
    }}>
      <input />
      <button>Send</button>
    </form>
  );
}
```

补充知识点：区分 e.stopPropagation() 和 preventDefault() ...08/12/2021 LISA

You can declare an event handler in a parent and pass it as a prop to a child.

```react
//学习：JSX构件里面获取背景信息
export default function LightSwitch() {
  function handleClick() {
    let bodyStyle = document.body.style;  
    if (bodyStyle.backgroundColor === 'black') {
      bodyStyle.backgroundColor = 'white';
    } else {
      bodyStyle.backgroundColor = 'black';
    }
  }

  return (
    <button onClick={handleClick}>
      Toggle the lights
    </button>
  );
}
```



##### State

###### Why State?

1. **Local variables don’t persist between renders.** When React renders this component a second time, it renders it from scratch—it doesn’t consider any changes to the local variables.
2. **Changes to local variables won’t trigger renders.** React doesn’t realize it needs to render the component again with the new data.

To update a component with new data, two things need to happen:

1. **Retain** the data between renders.
2. **Trigger** React to render the component with new data (re-rendering).

步骤：

```react
import { useState } from 'react';        //步骤1:import
import { sculptureList } from './data.js';

export default function Gallery() {
  const [index, setIndex] = useState(0); /*步骤2:The [ and ] syntax here is called array destructuring and it lets you read values from an array.The array returned by useState always has exactly two items.  */

  function handleClick() {
    setIndex(index + 1);                 //步骤3:index & setIndex work together
  }

  let sculpture = sculptureList[index];
  return (
    <>
      <button onClick={handleClick}>
        Next
      </button>
    ...
    )
 }
```

In React, `useState`, as well as any other function starting with ”`use`,” is called a **Hook**.

**Hooks—functions starting with `use`—can only be called at the top level of your components or [your own Hooks](https://reactjs.bootcss.com/learn/reusing-logic-with-custom-hooks).** 

More about hook mechanism in [React Hooks: Not Magic, Just Arrays](https://medium.com/@ryardley/react-hooks-not-magic-just-arrays-cd4f1857236e). //...待完成 30/11/2021

An example **doesn’t use React** but it gives you an idea of how `useState` works internally.//...待完成 30/11/2021

###### State as a Snapshot

State is not tied to a particular function call or a place in the code, but it’s. “local” to the specific place on the screen. 

**Setting state only changes it for the \*next\* render**.

**React keeps the state values “fixed” within one render’s event handlers.** 

Variables and event handlers don’t “survive” re-renders. Every render has its own event handlers.

Event handlers created in the past have the state values from the render in which they were created.

//...React编程思想 1/12

**React waits until \*all\* code in the event handlers has run before processing your state updates.**

```react
  async function handleClick() { //...1/12/2021 语法 LISA
    setPending(pending + 1);
    await delay(3000);           //...1/12/2021 语法 LISA
    setPending(0);
    setCompleted(completed + 1);
  }
```



**Treat any JavaScript object that you put into state as read-only**.



05/12/2021

use the `...` [object spread](https://reactjs.bootcss.com/learn/a-javascript-refresher#object-spread) syntax

```react
setPerson({
  ...person, // Copy the old fields
  firstName: e.target.value // But override this one
});

//Using a single event handler for multiple fields
function handleChange(e) { 
  setPerson({ 
    ...person,
    [e.target.name]: e.target.value //use [] to specify a property with dynamic name. 
});
```

Note that the `...` spread syntax is “shallow”—it only copies things one level deep. This makes it fast, but it also means that if you want to update a nested property, you’ll have to use it more than once. 

###### Write concise update logic with Immer

```react
updatePerson(draft => {
  draft.artwork.city = 'Lagos';
});
```

But unlike a regular mutation, it doesn’t overwrite the past state!

###### Updating arrays without mutation

|           | avoid (mutates the array)           | prefer (returns a new array)                                 |
| --------- | ----------------------------------- | ------------------------------------------------------------ |
| adding    | `push`, `unshift`                   | `concat`, `[...arr]` spread syntax ([example](https://reactjs.bootcss.com/learn/updating-arrays-in-state#adding-to-an-array)) |
| removing  | `pop`, `shift`, `splice`            | `filter`, `slice` ([example](https://reactjs.bootcss.com/learn/updating-arrays-in-state#removing-from-an-array)) |
| replacing | `splice`, `arr[i] = ...` assignment | `map` ([example](https://reactjs.bootcss.com/learn/updating-arrays-in-state#replacing-items-in-an-array)) |
| sorting   | `reverse`, `sort`                   | copy the array first ([example](https://reactjs.bootcss.com/learn/updating-arrays-in-state#making-other-changes-to-an-array)) |

```react
const [artists, setArtists] = useState([]);
setArtists( // Replace the state
  [ // with a new array
    ...artists, // that contains all the old items
    { id: nextId++, name: name } // and one new item at the end
  ]  //[]表示数组
);
```

上面是增加数组元素的例子，如果是删除某元素，用filter， `filter` does not modify the original array.

改变图上形状位置的例子：

```react
  function handleClick() {
    const nextShapes = shapes.map(shape => {
      if (shape.type === 'square') {
        // No change
        return shape;  //没有改变也必须返回值！！！ 06/12/2021 LISA
      } else {
        // Return a new circle 50px below
        return {
          ...shape,
          y: shape.y + 50,
        };
      }
    });
    // Re-render with the new array
    setShapes(nextShapes);
  }
```

学习map使用时的第二个输入参数：i

```react
let initialCounters = [
  0, 0, 0
];
const [counters, setCounters] = useState(
    initialCounters
  );
function handleIncrementClick(index) {
  //*** Inside your map call, you will receive the item index as the second argument. 
    const nextCounters = counters.map((c, i) => { 
      if (i === index) {
        // Increment the clicked counter
        return c + 1;
      } else {
        // The rest haven't changed
        return c;
      }
    });
```

插入的例子

```react
  function handleClick() {
    const insertAt = 1; // Could be any index
    const nextArtists = [
      // Items before the insertion point:
      ...artists.slice(0, insertAt),
      // New item:
      { id: nextId++, name: name },
      // Items after the insertion point:
      ...artists.slice(insertAt)
    ];
    setArtists(nextArtists);
```

**When updating nested state, you need to create copies from the point where you want to update, and all the way up to the top level.**

//...Challenge3: 响应函数参数是怎么传递的？ 06/12/2021 LISA



###### 管理状态

//...学习第一个例子 & 里面的新方法

 To better understand how to think in React, you’ll walk through reimplementing this UI in React below:

1. **Identify** your component’s different visual states
2. **Determine** what triggers those state changes
3. **Represent** the state in memory using `useState`
4. **Remove** any non-essential state variables
5. **Connect** the event handlers to set the state

Human inputs often require [event handlers](https://reactjs.bootcss.com/learn/responding-to-events)!



JS判断 与 JSX输出 的搭配案例，{} <>与()的嵌套使用

```javascript
      <label>
        Last name:{' '}
        {isEditing ? (
          <input
            value={lastName}
            onChange={e => {
              setLastName(e.target.value)
            }}
          />
        ) : (
          <b>{lastName}</b>
        )}
      </label>
```



//...key的使用 待复习 12/12/2021 LISA

```javascript
function PlaceTree({ place }) {  //props里面只接收 place 一个参数
  const childPlaces = place.childPlaces;
  return (
    <>
      <li>{place.title}</li>
      {childPlaces.length > 0 && (
        <ol>
          {childPlaces.map(place => (
            <PlaceTree key={place.id} place={place} />
          ))}
        </ol>
      )}
    </>
  );
}
 			<ol>
        {planets.map(place => (
          <PlaceTree key={place.id} place={place} />  //用到了 key 和 palce
        ))}
      </ol>
```

参数是怎么传过去的？

```javascript
  function handleComplete(parentId, childId) { //需要两个入参？
    const parent = plan[parentId];
    // Create a new version of the parent place
    // that doesn't include this child ID.
    const nextParent = {
      ...parent,
      childIds: parent.childIds
        .filter(id => id !== childId)
    };
    setPlan({
      ...plan,
      // ...so that it has the updated parent.
      [parentId]: nextParent
    });
   }
 const planetIds = root.childIds;
  return (
    <>
      <h2>Places to visit</h2>
      <ol>
        {planetIds.map(id => (
          <PlaceTree
            key={id}
            id={id}
            parentId={0}
            placesById={plan}
            onComplete={handleComplete} //...没有传任何参数？
          />
        ))}
      </ol>
    </>
```



React makes **UI trees** from your JSX. Then <u>React DOM</u> updates the browser DOM elements to match that UI tree. (**React Native** translates these trees into elements specific to mobile platforms.)

![React takes components, turns them into UI tree structures, and ReactDOM turns them into HTML in your browser using the DOM.](https://reactjs.bootcss.com/images/docs/sketches/s_react-dom-tree.png)

React will only keep the state around for as long as you render the same component at the same position. 

When React removes a component, it destroys its state.

**when you render a different component in the same position, it resets the state of its entire subtree**. 

You should not nest component function definitions.

//...??? 13/12/2021 LISA

Every time you click the button, the input state disappears! This is because a *different* `MyTextField` function is created for every render of `MyComponent`. You’re rendering a *different* component in the same position, so React resets all state below. This leads to bugs and performance problems. To avoid this problem, **always declare component functions at the top level, and don’t nest their definitions.**



```javascript
this.state = {      squares: Array(9).fill(null),    }; //长度为 9 的空值数组
```

```html
//相同 UI 位置
 <div>
      {isPlayerA ? (
        <Counter person="Taylor" />
      ) : (
        <Counter person="Sarah" />
      )}
  </div>    
//不同 UI 位置
 <div>
      {isPlayerA &&
        <Counter person="Taylor" />
      }
      {!isPlayerA &&
        <Counter person="Sarah" />
      }
 </div>
```

   There are two ways to reset state when switching between them:

1. Render components in different positions
2. Give each component an explicit identity with `key`



Reducers are a different way to handle state. You can migrate from `useState` to `useReducer` in three steps:

1. **Move** from setting state to dispatching actions.
2. **Write** a reducer function.
3. **Use** the reducer from your component.

useImmerReducer

dispatch 的几个问题：//... 17/12/2021 LISA

1. 可以dispatch state之外的属性吗？如果可以，是否与reducer对应就好了 Yes

确保ruducer函数返回 完整的 更新后的 state！

##### Consumer 消费 Context

//... 与 use Context 比较

多个 context 只能使用 Consumer 层层包的方式来一一传值，后面会用 Redux 代替。

因为 context 会根据引用标识来决定何时进行渲染（本质上是 `value` 属性值的浅比较），所以这里可能存在一些陷阱，当 provider 的父组件进行重渲染时，可能会在 consumers 组件中触发意外的渲染。举个例子，当每一次 Provider 重渲染时，以下的代码会重渲染所有下面的 consumers 组件，因为 `value` 属性总是被赋值为新的对象：

```javascript
class App extends React.Component {
  render() {
    return (
      <MyContext.Provider value={{something: 'something'}}>//每次调用value为一个新（对象的）地址
      <Toolbar />
      </MyContext.Provider>
    );
  }
}
```

为了防止这种情况，将 value 状态提升到父节点的 state 里：

```javascript
class App extends React.Component {
  constructor(props) {
    super(props);
    this.state = {
      value: {something: 'something'},    };
  }

  render() {
    return (
      <MyContext.Provider value={this.state.value}>        
      <Toolbar />
      </MyContext.Provider>
    );
  }
}
```



##### Provide data with Context

![Context provides data to the entire tree](https://reactjs.bootcss.com/images/docs/sketches/s_providing-context.png)

- Context lets a component provide some information to the entire tree below it.
- To pass context:
  1. Create and export it with `export const MyContext = createContext(defaultValue)`.
  2. Pass it to the `useContext(MyContext)` Hook to read it in any child component, no matter how deep.
  3. Wrap children into `<MyContext.Provider value={...}>` to provide it from a parent.



useContext 方法接收一个 context 对象（`React.createContext` 的返回值）并返回该 context 的当前值。当前的 context 值由上层组件中距离当前组件最近的 `<MyContext.Provider>` 的 `value` prop 决定。

当组件上层最近的 `<MyContext.Provider>` 更新时，该 Hook 会触发重渲染，并使用最新传递给 `MyContext` provider 的 context `value` 值。即使组件使用 `React.memo` 或 `shouldComponentUpdate`，也会在组件本身使用 `useContext` 时重新渲染。

`useContext(MyContext)` 只是让你能够读取 context 的值以及订阅 context 的变化。你仍然需要在上层组件树中使用 `<MyContext.Provider>` 来为下层组件提供 context。

##### 高阶组件 HOC 44～49

##### 49讲：高阶组件生命周期劫持

```javascript
//在 componentWillMount() 中定义起始时间
this.beginTime = Date.now();

//在 componentDidMount() 中定义渲染结束时间
this.endTime = Date.now();
const times = this.endTime - this.beginTime;
console.log(“组件” + WrapedComponent.name + "渲染时间：" + times);
```

##### 48讲：高阶组件进行登录认证操作

利用 HOC 不同入参 返回不同的组件

```javascript
//1. LoginPage 组件定义，CartPage 组件定义
//2. HOC 定义：如果 isLogin 为 true，调用返回 WrapedComponent；否则， 调用返回 LoginPage
//3. App 里面：AuthCart = HOC(CartPage),分别传入 true 和 false 来调 AuthCart，根据不同的参数返回不同页面 
```



##### 47讲：高阶组件+Context

//...props的参数传递路径 LISA 2021-12-29

##### 44讲：高阶组件

高阶组件是纯函数，不改变入参组件。

组件：将 props 转化为 UI；

高阶组件：将 组件 转化为 新组件。例如 Redux 的 [`connect`](https://github.com/reduxjs/react-redux/blob/master/docs/api/connect.md#connect) 和 Relay 的 [`createFragmentContainer`](https://relay.dev/docs/v10.1.3/fragment-container/#createfragmentcontainer)。∫



##### Render Props (50~52)

52讲：Render Props 加 HOC

```javascript
//Mouse 作为 数据提供者 接收 不同 的 render，渲染不同的内容
//将 51 里面对 猫组件 的调用改为：
this.props.render(this.state);

//定义新组件 MouseTracker，将 Mouse 用起来，猫组件 作为函数体的一部分
<Mouse render={mouseXY=><Cat mouse={mouseXY}>}/>
```

51讲：render props 封装

```javascript
//Mouse 里面 调用 Cat 组件，实现鼠标移动 猫 跟着动的功能
//渲染图片的方法
import timg from './timg.gif'

<img src={timg} style={{postion:'absolute', left : '100px', top : '50px'}}/>
```

50讲：render props

```javascript
//鼠标移动显示鼠标当前位置

//1. 定义函数 mouseMove()
function mouseMove(e){
  this.setState({x:e.clientX, y:e.clientY});
}

//获取鼠标位置的方式 2. 鼠标移动响应 onMouseMove
//注意：如果 ‘100%’，背景高度 覆盖 到 body
<div style={{height:'100vh', background:'pink'}} onMouseMove={e=>{this.mouseMove(e)}}>
</div>
```

具有 render prop 的组件接受一个返回 React 元素的函数，并在组件内部通过调用此函数来实现自己的渲染逻辑。

```javascript
<DataProvider render={data => (
  <h1>Hello {data.target}</h1>
)}/>
```

**render prop 是一个用于告知组件需要渲染什么内容的函数 prop。**

```react
class Cat extends React.Component {
  render() {
    const mouse = this.props.mouse;
    return (
      <img src="/cat.jpg" style={{ position: 'absolute', left: mouse.x, top: mouse.y }} />
    );
  }
}

class Mouse extends React.Component {
  constructor(props) {
    super(props);
    this.handleMouseMove = this.handleMouseMove.bind(this);
    this.state = { x: 0, y: 0 };
  }

  handleMouseMove(event) {
    this.setState({
      x: event.clientX,
      y: event.clientY
    });
  }

  render() {
    return (
      <div style={{ height: '100vh' }} onMouseMove={this.handleMouseMove}>

        {/*
          使用 `render`prop 动态决定要渲染的内容，
          而不是给出一个 <Mouse> 渲染结果的静态表示
        */}
        {this.props.render(this.state)}
      </div>
    );
  }
}

class MouseTracker extends React.Component {
  render() {
    return (
      <div>
        <h1>移动鼠标!</h1>
        <Mouse render={mouse => (
          <Cat mouse={mouse} />
        )}/>
      </div>
    );
  }
}
```

使用 render prop 的库有 [React Router](https://reacttraining.com/react-router/web/api/Route/render-func)、[Downshift](https://github.com/paypal/downshift) 以及 [Formik](https://github.com/jaredpalmer/formik)。

##### Portals & 事件冒泡（53、54）

```javascript
ReactDOM.createPortal(child, container)
```

将子节点渲染到存在于父组件以外的 DOM 节点。

##### Ant Design 的使用 (55~58)

```bash
npm i antd -S
```

使用 antd

```javascript
import Input from 'antd'
import 'antd/dist/antd.css'

const {TextArea} = Input;//TextAre 是 Input 的一个对象

export default class CommentInput extends Comment{
  render(){
    return (
	   <div style={{width:"300px"}}>
      <TextArea rows={4}>
	   </div> 
    )
  }
}

```

练习：完成一个 评论发表 & 显示 的功能

#### axios (59~62)

其他资源 - [偷米騎巴哥]前端一定要配Axios



用来进行网络请求的，可以 使用 网站：https://httpbin.org(提供了常见的接口) 来练习；

get 方式 有两种写法：写在 url 里面，或者 params 中；

post 方式 只有一种：写在 data 里，method：“post”；





#### redux.reducer.todolist 分析 (63~70~75)

使用场景：复杂项目with a lot of states，状态少的项目不使用

官网：http://redux.org.cn

action：描述 有事情发生了

reducer：依据 action 描述的内容，对状态进行修改的一个个函数

store：仓库，存放 reducer 的地方

action 提交--> 仓库 --> 找到对应的reducer

提交：一般通过 store.dispatch()

推荐：把所有事件类型字符串单独放在一个文件里，并赋值给变量，其他地方如需要使用，则引入该文件，便于编码、减少出错、会有系统提示等好处；

```javascript
//action 定义
{
  type : "addTodo",
  text : "swimming"
}

//--> 👆演化为：三步
//1.action 类型 定义 2.action 创建函数 定义 3. bind dispatch
export const ADD_TODO = "addTodo";
export function addTodo(text){
	return {
    type : "addTodo",
    text : text
  }  
}

const dispatchAddTodo = text => {dispatch(addTodo(text))};

//Redux 提供了 combineReducers()工具类 来 简化代码

//ES6用户使用注意
//combineReducers 接收一个对象，可以把所有顶级的 reducer 放到一个独立的文件中，通过 export 暴露出每个 reducer 函数，然后使用 import * as reducers 得到一个以它们名字作为 key 的 object
import {combineReducers} from 'redux'
import * as reducers from './reducers'

const todoApp = combineReducers(reducers)
```

//...待补充知识点 Array.prototype.reduce()

//...待补充知识点 Object.assigh() 对象合并

**Store** 就是把 action 和 reducer 联系到一起的对象，有以下职责：

1. 维持应用的 state
2. 提供 getState() 方法获取 state
3. 提供 dispatch(action) 方法更新 state
4. 通过 subscribe(listener) 注册监听器
5. 通过 subscribe(listener) 返回的函数注销 监听器

##### 搭配 React

安装 npm install --save react-redux

开发思想：容器组件 & 展示组件 相分离

|       展示组件 | 容器组件                   |                                    |
| -------------: | :------------------------- | ---------------------------------- |
|           作用 | 描述如何展现（骨架、样式） | 描述如何运行（数据获取、状态更新） |
| 直接使用 Redux | 否                         | 是                                 |
|       数据来源 | props                      | 监听 Redux state                   |
|       数据修改 | 从 props 调用回调函数      | 向 Redux 派发 actions              |
|       调用方式 | 手动                       | 通常由 React Redux 生成            |

容器组件不建议直接使用 `store.subscribe()` 来编写，原因是无法使用 React Redux 带来的性能优化；建议使用 React Redux 的 `connect()` 方法来生成。容器组件把展示组件连接到 Redux。

使用 connect() 前，需要先定义 mapStateToProps 这个函数来指定 **如何把当前 Redux store state 映射到 展示组件 的 props** 中。

##### useRef

When you want a component to “remember” some information, but you don’t want that information to [trigger new renders](https://reactjs.bootcss.com/learn/render-and-commit), you can use a **ref**

Here’s how state and refs compare:

| refs                                                         | state                                                        |
| ------------------------------------------------------------ | ------------------------------------------------------------ |
| `useRef(initialValue)` returns `{ current: initialValue }`   | `useState(initialValue)` returns the current value of a state variable and a state setter function ( `[value, setValue]`) |
| Doesn’t trigger re-render when you change it.                | Triggers re-render when you change it.                       |
| Mutable—you can modify and update `current`’s value outside of the rendering process. | “Immutable”—you must use the state setting function to modify state variables to queue a re-render. |
| You shouldn’t read (or write) the `current` value during rendering. | You can read state at any time. However, each render has its own [snapshot](https://reactjs.bootcss.com/learn/state-as-a-snapshot) of state which does not change. |



```javascript
  //The useRef Hook returns an object with a single property called current. Initially, myRef.current will be null. 
  const inputRef = useRef(null);
	const inputRef1 = React.createRef();

  const onHandleClick = ()=> {
    //'current' points to 1st input element
    inputRef.current.focus();
  }
  
  const onHandleClick1 = ()=> {
    //'current' points to 2nd input element
    inputRef1.current.focus();
  }

  return (
    <>
      //When creating a DOM node, React put a reference to this node into inputRef.current. 
      <input ref={inputRef} />
      <button onClick={onHandleClick}>
        Focus the input
      </button>
		  <input ref={inputRef1} />
      <button onClick={onHandleClick1}>
        Focus the input
      </button>
    </>
  );
}
```

**Hooks must only be called at the top-level of your component.** You can’t call `useRef` in a loop, in a condition, or inside a `map()` call.

Sometimes you might need a ref to each item in the list, and you don’t know how many you will have. 

**Pass a function to the `ref` attribute**. This is called a “ref callback”. React will call your ref callback with the DOM node when it’s time to set the ref, and with `null` when it’s time to clear it.

```javascript
import { useRef } from 'react';

export default function CatFriends() {
  //itemsRef holds a Map from item ID to a DOM node. (Refs can hold any values!) 
  const itemsRef = useRef(null);

  function scrollToId(itemId) {
    const map = getMap();
    const node = map.get(itemId);
    node.scrollIntoView({
      behavior: 'smooth',
      block: 'nearest',
      inline: 'center'
    });
  }
  
  //A Ref Callback.
  function getMap() {
    if (!itemsRef.current) {
      // Initialize the Map on first usage.
      itemsRef.current = new Map();
    }
    return itemsRef.current;
  }

  return (
    <>
      <nav>
        <button onClick={() => scrollToId(0)}>
          Tom
        </button>
        <button onClick={() => scrollToId(5)}>
          Maru
        </button>
        <button onClick={() => scrollToId(9)}>
          Jellylorum
        </button>
      </nav>
      <div>
        <ul>
          {catList.map(cat => (
            <li
              key={cat.id}
							//React will call your ref callback with the DOM node when it’s time to set 								//the ref, and with `null` when it’s time to clear it.
              ref={(node) => {   
                const map = getMap();
                if (node) {
                  map.set(cat.id, node);
                } else {
                  map.delete(cat.id);
                }
              }}
            >
              <img
                src={cat.imageUrl}
                alt={'Cat #' + cat.id}
              />
            </li>
          ))}
        </ul>
      </div>
    </>
  );
}

const catList = [];
for (let i = 0; i < 10; i++) {
  catList.push({
    id: i,
    imageUrl: 'https://placekitten.com/250/200?image=' + i
  });
}


```

[useRef 稀土掘金](https://juejin.cn/post/6844904168562360328)

FocusInput.tsx

```typescript
import React, { useEffect, useRef} from 'react'

function FocusInput() {
  //注意：与 TypeScript 结合使用时的方式，需要先声明好泛型
  const inputRef = useRef<HTMLInputElement>(null)
  useEffect(() => {
    //同时使用时需要判空
    inputRef.current && inputRef.current.focus()
  }, [])

  return (
    <div>
      <input ref={inputRef} type="text" />
    </div>
  )
}

export default FocusInput
```

App.tsx

```typescript
import React from 'react'
import './App.css'

import FocusInput from './components/28FocusInput'

const App = () => {
  return (
    <div className="App">
      <FocusInput />
    </div>
  )
}

export default App
```

##### [useRef 与 ts 结合](https://fettblog.eu/typescript-react/hooks/#useref)

##### Refs & DOM 之 回调 Refs

```javascript
function CustomTextInput(props) {
  return (
    <div>
      <input ref={props.inputRef} />
    </div>
  );
}

class Parent extends React.Component {
  render() {
    return (
      <CustomTextInput
        inputRef={el => this.inputElement = el}
      />
    );
  }
}
```

##### 自定义Component 能被Ref：

```javascript
import { forwardRef, useRef } from 'react';

//2. The MyInput component is declared using forwardRef. This opts it into receiving the inputRef from above as the second ref argument
const MyInput = forwardRef((props, ref) => {
  //3. MyInput itself passes the ref it received to the <input> inside of it.
  return <input {...props} ref={ref} />;
});

export default function Form() {
  const inputRef = useRef(null);

  function handleClick() {
    inputRef.current.focus();
  }

  return (
    <>
      //1. Tells React to put the corresponding DOM node into inputRef.current. However, it’s up to the MyInput component to opt into that—by default, it doesn’t.
      <MyInput ref={inputRef} />
      <button onClick={handleClick}>
        Focus the input
      </button>
    </>
  );
}

```

React sets `ref.current` during the commit. Before updating the DOM, React sets the affected `ref.current` values to `null`. After updating the DOM, React immediately sets them to the corresponding DOM nodes.

```javascript
//setTodos does not immediately update the DOM. So the time you scroll the list to its last element, the todo has not yet been added.
setTodos([ ...todos, newTodo]);  
listRef.current.lastChild.scrollIntoView();

import { flushSync } from 'react-dom';
//Fix: Force React to update (“flush”) the DOM synchronously
flushSync(() => {
  setTodos([ ...todos, newTodo]);
});
listRef.current.lastChild.scrollIntoView();
```

1/5 Done! 19/12/2021 加油呀 ⛽️⛽️⛽️ 



[（乐字节）2021前端最新教程-React实战教学]()

#### [Hook (76~80)](https://zh-hans.reactjs.org/docs/hooks-reference.html)

总是在你的 React 函数的最顶层以及任何 return 之前调用他们，并只在函数中使用Hook；

##### useState() 

```javascript
const [person, setPerson] = useState({name:"", age:10}});
```

如果状态属性是一个对象，假如调用 setPerson 只设置某键值对，不会合并成完整对象；但是 类 的 setState 可以把键值对合并成一个完整对象后再 修改 状态 的值。

##### useEffect() 

使用 `useEffect` 完成副作用操作；

会在浏览器绘制后延迟执行，但会保证在任何新的渲染前执行；

 `useEffect` 的第二个参数是个值数组，仅需要在该参数改变时重新执行；

相当于类里面的三个生命周期函数：

```react
//加载 & 更新 时，调用 subscribeToFriendStatus
//卸载时，调用 cleanup() 
useEffect(
  () => {
    ChatAPI.subscribeToFriendStatus(props.friend.id, ()=>{
      setIsOnline(status.isOnline);
    };
    // Specify how to clean up after this effect:
    return ()=> {
      ChatAPI.unsubscribeFromFriendStatus(props.friend.id, handleStatusChange);
    };
);
```

如上所示：如果你的 effect 返回一个函数，React 将会在执行清除操作时调用它。

##### [useMemo](https://zh-hans.reactjs.org/docs/hooks-reference.html#usememo)

```react
const memoizedValue = useMemo(() => computeExpensiveValue(a, b), [a, b]);
```

返回一个 [memoized](https://en.wikipedia.org/wiki/Memoization) 值。

把“创建”函数和依赖项数组作为参数传入 `useMemo`，它仅会在某个依赖项改变时才重新计算 memoized 值；这种优化有助于避免在每次渲染时都进行高开销的计算；

可以把 `useMemo` 作为性能优化的手段，但不要把它当成语义上的保证。

##### 自定义Hook

Hook 可以将 React 中提供的 Hook 组合到定制的 Hook 中，以复用不同组件之间常见的状态逻辑（其他解决方式：高阶组件、render props //待复习...）。



**38讲**：使用 Context 跨组件通信

使用 Context 的方法

```javascript
import React,{Component} from 'react';
import {myContext} from './myContext.js';

export default class ProfileHeader extends Component{
  static contextType = myContext;    //1. 变量名必须为 contextType
  render(){
    return(
      <div>
      	<h2>用户昵称：{this.context.nickname}</h2>  //2. 必须使用 this.context.
				<h2>用户等级：{this.context.level}</h2>
      </div>
      )
  }
}
```



#### 9 表单 受控组件

##### Input输入后能够显示的路径：

界面输入 --> Onchange --> handleChange 修改 state --> 触发 渲染 --> render --> input 中 value有了值



003-state和生命周期函数

Q1: setState()异步调用，必须使用函数作为入参才能够更新成功？

##### 数据自上向下流动

组件里 state 的值改变，UI自动更新；

子组件里通过 props 接收到的值如果更新，UI也会自动更新。

##### 生命周期图谱

https://projects.wojtekmaj.pl/react-lifecycle-methods-diagram/


​        

#### React事件处理

使用 ES6 class 语法来定义一个组件的时候，事件处理器会成为类的一个方法。

必须谨慎对待 JSX 回调函数中的 this，类的方法默认是不会**<u>绑定 this</u>** 的。如果你忘记绑定 this.handleClick 并把它传入 onClick, 当你调用这个函数的时候 this 的值会是 undefined。

这并不是 React 的特殊行为；它是函数如何在 JavaScript 中运行的一部分。通常情况下，如果你没有在方法后面添加 () ，例如 **onClick={this.handleClick}**，你应该为这个方法绑定 this。

```react
class Toggle extends React.Component {
  constructor(props) {
    super(props);
    this.state = {isToggleOn: true};
 
    // 这边绑定是必要的，这样 `this` 才能在回调函数中使用
    // bind 绑定还可以传其它参数，如 bind(this, id)，id 会被传入处理函数
    this.handleClick = this.handleClick.bind(this);
  }
 
  handleClick() {
    this.setState(prevState => ({
      isToggleOn: !prevState.isToggleOn
    }));
  }
 
  render() {
    return (
      <button onClick={this.handleClick}>
        {this.state.isToggleOn ? 'ON' : 'OFF'}
      </button>
    );
  }
}
 
ReactDOM.render(
  <Toggle />,
  document.getElementById('example')
);
```

extends React.Component 不如 React.pureComponent 性能好，因为类里面的状态变化时，子组件会无条件渲染，即使子组件使用的状态没有更新。

##### 补充知识点：\<input type="file" />

#### React哲学

UI组件分层，用React创建静态版本，确定 UI state 的最小且完整表示，确定 state 的位置，添加反向数据流

#### 非受控组件

在 React 渲染生命周期时，表单元素上的 `value` 将会覆盖 DOM 节点中的值.

##### 文件上传的方法

```javascript
 class FileInput extends React.Component {
  constructor(props) {
    super(props);
    this.handleSubmit = this.handleSubmit.bind(this);
    this.fileInput = React.createRef();  //1. 
  }
  handleSubmit(event) {
    event.preventDefault();
    alert(
      `Selected file - ${this.fileInput.current.files[0].name}` //3.
    );
  }

  render() {
    return (
      <form onSubmit={this.handleSubmit}>
        <label>
          Upload file:
          <input type="file" ref={this.fileInput} />  //2.
        </label>
        <br />
        <button type="submit">Submit</button>
      </form>
    );
  }
}

ReactDOM.render(
  <FileInput />,
  document.getElementById('root')
);

```



#### JSX类型详解

支持点语法，但不支持[]，Props默认值为true，

{ foo } 是 { foo : foo } 的简写   //ES6里面对象简写

const {kind, ...other} = props; //ES6 解构语法

React 组件也能够返回存储在数组中的一组元素：

在 js 文件中可以引入 css 文件，使用 className 来定义 css 类名；

input 框输入 <h1>hello world</h1> 呈现 html 效果 - 10/83 Jomy

-- 用 dangerouslySetInnerHTML={{__html: item}} 代替 {item}

注释的两种写法；

使用 label 和 input 配合 完成 鼠标放在 label 上，光标自动聚焦 input

```react
<lable htmlFor='insertArea'>输入内容</lable>
<input id='insertArea'
  {
    //一条注释
  } 
  {/*另一条*/}
  className='input'
  value={this.state.inoutValue}
  onChange={this.handleInputChange.bind(this)}
  />
```



```react
render() {
  // 不需要用额外的元素包裹列表元素！
  return [
    <li key="A">First item</li>, 
    <li key="B">Second item</li>,
    <li key="C">Third item</li>,
  ];
}
```

##### 函数作为子元素 

通常，JSX 中的 JavaScript 表达式将会被计算为字符串、React 元素或者是列表。不过，`props.children` 和其他 prop 一样，它可以传递任意类型的数据，而不仅仅是 React 已知的可渲染类型。例如，如果你有一个自定义组件，你可以把回调函数作为 `props.children` 进行传递：

```javascript
// 调用子元素回调 numTimes 次，来重复生成组件
function Repeat(props) {
  let items = [];
  for (let i = 0; i < props.numTimes; i++) {    items.push(props.children(i));
  }
  return <div>{items}</div>;
}

function ListOfTenThings() {
  return (
    <Repeat numTimes={10}>{/*我是一个注释*/}
      {(index) => <div key={index}>This is item {index} in the list</div>}    </Repeat>
  );
}
```

`false`, `null`, `undefined`, and `true` 是合法的子元素。但它们并不会被渲染。

如果你想渲染 `false`、`true`、`null`、`undefined` 等值，你需要先将它们[转换为字符串](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/String#String_conversion)：

```javascript
<div>
  My JavaScript variable is {String(myVariable)}.</div>
```



#### 复习HTML标签

<span /> 

<tr/> 

<span/>

<>

setState()简写方式//...

复习JS中map的取值用法 [{0:"aaa"}, {1:"bbb"},{2:"ccc"}]

Symbol 独一无二的值

### 拓展知识点

####  [jQuery selectors](https://api.jquery.com/category/selectors/)

MDN Web Docs (previously known as MDN — the Mozilla Developer Network)

### React开发运行环境

//... 06/12/2021 LISA

Hbuilder

##### 扩展运算符 spread ...

```
### 高阶函数中过滤掉不想要的属性
...
render() {
   const { unacceptedProp, byebye, ...acceptedProps } = this.props;
   return <WrappedComponent {...acceptedProps} />
}
```

Arrow functions implicitly return the expression right after `=>`, so you didn’t need a `return` statement:

```
const listItems = chemists.map(person =>
  <li>...</li> // Implicit return!
);
```

However, **you must write `return` explicitly if your `=>` is followed by a `{` curly brace!** If you forget it, nothing gets returned!



### Node.js

执行环境，装在电脑上之后，使电脑能执行 js 代码；

早期 html+js，在浏览器执行；

但是电脑没有执行 js 的环境；

npm、npx 是建立在 Node.js 上的安装包；

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

#### 

### React Native 移动端开发

（资源一）尚硅谷最新 React 开发跨移动端 - 天禹

https://www.bilibili.com/video/BV1z5411g7uu?p=1

概念 -- 公式 -- 适配

2014年 iPhone6发布 前端元年 750*1334

屏幕密度（单位：ppi - pixels per inch）：像素密度，每英寸里面包含的像素点个数。 PPI = (XX + YY) / 屏幕尺寸，用来衡量屏幕；

dpi - dots per inch，用来衡量打印机、投影仪等设备；



### 前端学习路线（李立超）：

第一阶段：HTML + CSS + JS  + Web API / DOM   == 验证标准 ==> 打开任何网页，都能够自己做出来

第二阶段：BootStrap（了解一下）+ 移动端开发  == 验证标准 ==> 任何移动网页，都能够自己做出来

第三阶段：MongoDB (+ MySQL) + Node.js + Moogoose

​                                    服务器：    Koa + Express

第四阶段：[webpack - 打包工具](webpack.js.org)

以上完成了 MPA（多页面应用） 架构，现在主流 SPA（单页应用）应用（前端框架来实现）

第五阶段：（Augular + Vue + ）React

Next 副业：微信小程序 + 微信公众号 

第七阶段：GitHub + Git



建议：java + 算法 + 微前端（实现方式：WebComponents + Qiankun）

#### react-router

[<Switch>](https://www.jianshu.com/p/ed5e56994f13)

渲染第一个被location匹配到的并且作为子元素的**<Route>**或者**<Redirect>**

#### [react-testing-library](https://git.io/react-testing-library)

#### [Eslint](https://eslint.org/docs/user-guide/configuring/#specifying-environments)

可参考：https://segmentfault.com/a/1190000018328740

ESLint是一个用来识别 ECMAScript 并且按照规则给出报告的代码检测工具，使用它可以避免低级错误和统一代码的风格。如果每次在代码提交之前都进行一次eslint代码检查，就不会因为某个字段未定义为undefined或null这样的错误而导致服务崩溃，可以有效的控制项目代码的质量。

运行 eslint --init 之后，.eslintrc 文件会在你的文件夹中自动创建。

```　json
{
    "env": {  //Javascript 脚步将要运行在什么环境中
        "es6": true,
        "node": true
    },
    "extends": "eslint:recommended",
    "parserOptions": {
        "sourceType": "script"
    },
    "rules": { //开启某些规则，也可以设置规则的等级。
        "no-console": 0,
        "no-unused-vars": "error",
        "no-use-before-define": "error",
        "linebreak-style": [
            "error",
            "unix"
        ],
        "quotes": [
            "error",
            "single"
        ],
        "semi": [
            "error",
            "always"
        ],
        "curly": ["error", "all"],
        "default-case": "error",
        "no-else-return": "error",
        "no-empty-function": "error",
        "no-implicit-coercion": "error",
        "no-invalid-this": "error",
        "no-loop-func": "error",
        "no-multi-spaces": "error",
        "no-new-func": "error",
        "no-useless-return": "error",
        "global-require": "error",
        "no-path-concat": "error",
        "no-sync": "error",
        "array-bracket-spacing": [
            "error",
            "never" 
        ],
        "block-spacing": [
            "error",
            "always"
        ],
        "brace-style": [
            "error",
            "1tbs"
        ],
        "camelcase": "error",
        "comma-dangle": [
            "error",
            "always-multiline"
        ],
        "comma-spacing": [
            "error",
            { "before": false, "after": true }
        ],
        "comma-style": [
            "error",
            "last"
        ],
        "key-spacing": [
            "error", 
            { "beforeColon": false, "afterColon": true }
        ],
        "lines-around-comment": [
            "error",
            { "beforeBlockComment": true }
        ],
        "newline-after-var": [
            "error",
            "always"
        ],
        "newline-before-return": "error",
        "no-multi-assign": "error",
        "max-params": [1, 3],
        "new-cap": [
            "error",
            {
                "newIsCap": true,
                "capIsNew": false
            }
        ],
        "no-multiple-empty-lines": [
            "error",
            {
                "max": 2
            }
        ],
        "no-shadow-restricted-names": "error",
        "no-undef-init": "error",
        "keyword-spacing": "error",
        "space-before-blocks": [
            "error",
            "always"
        ]
    }
}

```

