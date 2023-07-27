transform: skewX(20deg) // 沿着X轴的2D倾斜变换
transform: translateX(x) // Defines a translation, using only the value for the X-axis
transform: translateX(-30%) // 

隐藏的几种实现:
 1. display:none
 2. visibility: hidden
 3. transparent: 0

```css
<link href="style.css" rel="stylesheet"/>  //html 文件引入 css 的方式，等价于
<link href="style.css" rel="stylesheet" type="text/css"/>
<p class="related first-li"></p>  //可以设置同时属于多个 class 
<p class="related" class="first-li"></p>  //只有第一个样式被应用

/* 内联样式 */
<p style="color:red; font-size:20px">少小离家</p>

padding:  ⬆️ ➡️ ⬇️ ⬅️
padding: 10px 20px /* 上下 左右 */
/* 元素选择器：
	li - 选中所有 li 元素 
	.post-img - 选中 class 为 "post-img" 的元素
	#container - 选中 id 为 "container" 的元素
	* - 所有    
*/
li{
  margin-bottom: 10px;
  margin-left: 10px; /* 与左边的内容分开 */
}

div[class|=col]{ /* 选中 class 以 col 开始的 div  */
  border:1px solid; 
}

a:href { /* 只有 a 标签中设置了 href 属性的会被选中 a:visited a:hover */
  color: red;
  text-decoration: none;/* 去掉 超链接 下面的下划线 */
}
.post-img {
  width: 800px;
  height: auto; /* 与原图宽高等比例 设置 */
}
#container {
  width: 800px;
  // set the margin property to auto to horizontally center the element within its container.
  margin: auto; /* 会将左右自动调成相同 */
}
/* 交集选择器
	作用：选中同时符合多个条件的元素
	语法：选择器1选择器2选择器3{}
	注意：交集选择器中如果有元素选择器，必须使用元素选择器开头 */
div.static {
  position: static; /* 关闭 top bottom left right 等 */
}
/* , 分隔 - 同时选择多个选择器对应的元素，或 */
h1, h2, h4, p, #web {
  font-family:sans-serif;
}
h1 {
  font-size: 35px;
  text-transform: uppercase;
  font-style: italic;
}
h4 {
  color: green !important; /* 优先级最高 */
  font-size: 21px;
  text-align: center;
}

/* 关系选择器：空格、>、+、～
	div p：父与子关系
	div > p > span ：祖先后代关系 子元素的子元素
	p + span：选择 p 后边紧挨的那个 span
	p ~ span：选择 p 后边的所有兄弟 span
*/
footer p { /* 选择 footer 下面的 p */
  font-size: 16px;
}
.related-author {
  /* Defines from thin to thick characters. 100-900
  400 is the same as normal, and 700 is the same as bold */
  font-weight: bold; /* 加粗 */
}
.related-list {
  list-style: none; /* 去掉 list 前面缺省的 . */
}
/* 属性选择器：[]
	p[title]： 选择含有指定属性的元素
	[title="abc"] ：选择含有 title 属性 且值为 "abc" 的元素
	[title^"abc"] ：选择含有 title 属性 且值以"abc" 开头的元素	
	[title$"abc"] ：选择含有 title 属性 且值以"abc" 结尾的元素	
	[title*"abc"] ：选择含有 title 属性 且值包含"abc" 的元素
*/
p[title] {
  font-size: 20px;
  line-height: 1.5; //font-size 的 1.5 倍
}
/* 伪类（不存在的类） 伪元素 选择器：:、::
	- 伪类 用来描述一个原色的特殊状态，比如：第一个元素、被点击的元素、鼠标移入的元素...
	- 伪类 一般情况下以 : 开头
	:first-child 第一个子元素
	:last-child  最后一个子元素
	:nth-child(3) 第三个子元素，
		- n 为特殊值 表示所有，
		- 2n 或 even 表示第偶数个子元素，
		- 2n+1 或 odd：基数位 
	以上这些伪类都是根据所有的子元素进行排序
	:first-of-type
	:last-of-type
	:nth-of-type()
		- 这几个伪类的功能和上述的类似，不同点是他们是在同类型元素中进行排序
	:not() 否定伪类
		- 将符合条件的元素从选择器中去除 
*/
li:last-child {  //sudo 选择法 li:first-child
	margin-bottom: 0; //与下面的内容分开
}
li:nth-child(3){
  //设置第三个子的样式
  font-style: italic;
}
li:nth-child(n){
  //设置所有子的样式
  font-style: italic;
}
ul>li:not(:nth-child(3)){
  color:yellowgreen;
}

```

margin collapse 的现象：margin 不叠加

width 缺省，使用父元素的 100%

Block-level elements vs. Inline elements

positioning：top 和 margin 概念不同 absolute relative static sticky 

css 尽可能 精简

BEM css //...待补充

sass 官网 documentation 重要！ 

【实操】

css 文件 --copy--> sass 文件 会报很多错误 --rename--> scss 文件：很多错误就没有了

```scss
@import "_variables.scss"
@import "typography.scss";
html {
  font-size: 94.75%;
}
  
body {
  font-family: Arial, sans-serif;
  margin: 0;
}

// 修改 css 的平级结构 为 nesting 的，把子选择器的样式放入父样式下面
.container {
  display: -webkit-box;
  display: -ms-flexbox;
  display: -webkit-flex;
  display: flex;
  
  // flex-direction: column;
  // flex-wrap: nowrap;
  flex: {
    direction: column;
    wrap: nowrap;
  }
  aligh-items: center;
  padding: $size-default * 3;
  box-sizing: border-box;
}

.sass-introduction {
  border: $border-default;
  background: map-get($colors, main);
  padding: 2rem;
  text-align: center;
  box-shadow: 0.2rem 0.2rem 0.1rem #ccc
  width: 90%;
  box-sizing: border-box;
}

// built-in functions
// 根据基础色以及百分比 设置 最终想要的颜色
lighten(map-get($colors, main), 80%) 
```

新增文件 _variables.scss

```scss
// 使用 variable  要在文件顶部定义
$size-default: 1rem;
$main-color: #521751;
// List - an array of values
$border-default: 0.05rem solid $main-color;
// Map - an array of key-value pairs 
$colors: (main: #521751, secondary: #fa9a3f)

```

typography.css --rename--> typography.scss

并且在其中 @import "_variables.scss"

编译

```bash
// compile
$ sass main.scss main.css
$ sass --watch main.scss main.css
```

可以查看 Chrome / Inspect / Network 网络请求只有一个 main.css 文件 - **Partials 的使用**

怎么通过 scss 提高 media query？

```scss
@meida (min-width: 40rem){
  .container {
    ...A
  }
  .sass-introduction {
    ...B
  }
}
// 改成 如下 的形式
.container {
  @meida (min-width: 40rem){
    ...A
  }
}

.sass-introduction {
  @meida (min-width: 40rem){
    ...B
  }
}
```

Inheritance 

```scss
.sass-introduction {
  boder: $border-default;
  backgrond: lighten(map-get($color, main), 73%);
  padding: 2rem;
  text-align: center;
  box-shadow: 0.2rem 0.2rem 0.1rem #ccc;
  width: 90%;
  box-sizing: border-box;
}

.sass-details {
  boder: $border-default;
  backgrond: lighten(map-get($color, main), 73%);
  padding: 1rem;
  text-align: center;
  margin: 2rem 0;
  width: 90%;
  box-sizing: border-box;
}

// 重构成 ==> 下列的形式
.sass-section {
  // 把重复的 styling 提取出来
	boder: $border-default;
  backgrond: lighten(map-get($color, main), 73%);
  text-align: center;
  width: 90%;
  box-sizing: border-box;
}
.sass-introduction {
  @extend .sass-section;
  padding: 2rem;
  box-shadow: 0.2rem 0.2rem 0.1rem #ccc;
}
.sass-details {
  @extend .sass-section;
  padding: 1rem;
  margin: 2rem 0;
}
```

伪类的使用

```scss
// css 文件中的 伪类 可以重构成
.documentation-links .documentation-link:hover,
.documentation-links .documentation-link:active{
  color: white;
  background: map-get($colors, secondary);
  border-color: map-get($colors, secondary);
}
// 👇
.documentation-links {
  .documentation-link{
    &:hover, &:active{
      color: white;
  		background: map-get($colors, secondary);
  		border-color: map-get($colors, secondary);
    }
  }
}
```

Mixins - 用户自己的函数

```scss
@mixin display-flex() {
  display: -webkit-box;
  display: -ms-flexbox;
  display: -webkit-flex;
  display: flex;
}
// mixin 使用 参数的 方式
@mixin media-min-width($width) {
  @media(min-width: $width){
    // font-size: 125%;
    @content;
  }
}

// 将 .container 重构成 👇
.container {
  @include display-flex();
  ...
}
html{
  // @media(min-width: 40rem){
  //   font-size: 125%;
  // }
  @include media-min-width(40rem){
    font-size: 125%;
  };
}
```

scss --compile--> vanilla css 的形式

mixin 比 inheritance 更灵活，可以有逻辑、参数化、loop、content



【Popular CSS Library】

- Bootstrap

- Foundation

- Pure CSS

- Mobi CSS

- Semantic UI

[**Bootstrap**](https://getbootstrap.com/)

 引入 Bootstrap.min.css 及 js 文件

```html
<head>
  <link href=".../*.css" rel="stylesheet">
</head>
<body>
  <div class="container-fluid">
    <div class="row">
      <div class="col-sm-4 col-md-8">
        col 1
      </div>
      <div class="col-sm-8 col-md-4">
        col 2
      </div>
    </div>
  </div>
  <script src=".../*.js"></script>
</body>
```

bootstrap 把每行分成了 12 格，可以帮忙快速实现 responsive design，比如：

👆的设置 ==> 小窗口时 4 + 8，大窗口时 8 + 4

Break point：540px   720px  960px   1140px

​                        col-sm   md       lg           xl

【UI Design principles】

User familiarity

Consistency

Minimal surprise

Typography + primary typefaces

Color Palette + primary colours

Spacing and Positioning + grid system

Layout

UI Elements + navigation + buttons + forms

##### 伪元素选择器

伪元素，表示页面中一些特殊的并不真实存在的元素（特殊的位置）

​	伪元素使用 :: 开头

​	::first-letter 表示第一个字母

​	::first-line 表示第一行

​	::selection 表示选中的内容

​	::before 元素的开始位置

​	::after 表示元素的最后	

​		- 需要结合 content 来使用，开发中用得还挺多的

```css
p::first-line{
  background-color:yellow;
}
p::selection{
  background-color:green;
}
p::before{
  content: '【'; /* 通过 css 向 html 添加内容，且无法通过鼠标选中 */
  color:red;
}
p::after{
  content: '】'; 
  color:red;
}
```

```html
<q>hello</q>  <!-- 自动给加引号 -->
```

##### 样式的继承

​	我们为一个元素设置的样式同时也会应用到它的后代元素上

​	继承是发生在祖先和后代之间的

​	继承的设计是为了方便我们开发，

​	利用继承我们可以将一些通用的样式统一设置到共同的祖先元素上，

​	这样只需设置一次即可以让所有的元素都具有该样式，如 字体

​	注意：并不是所有的样式都会被继承

​		比如：背景相关的，布局 border 相关的这些样式不会被继承	

​	也可以查文档，看某个属性的 Inherited 值是 yes 还是 no



##### 超链接的伪类

​	a:link{} - 表示没访问过的链接（正常的链接）
​	a:visited - 访问过的链接，由于隐私的原因，该伪类只能修改链接的颜色
​	a:hover - 用来表示鼠标移入的状态
​	a:active - 用来表示鼠标正在点击
​	上面两个是 a 独有的，hover 和 active 所有元素都可以使用



##### 选择器的权重

​	样式的冲突

		- 当我们通过不同的选择器，选中相同的元素，并且为相同的样式设置不同的值时，此时就产生了样式的冲突
	发生样式冲突时，应用哪个样式由选择器的权重（优先级）决定
	
		- 选择器的权重
		内联样式     		1，0，0，0
		id选择器     	 0，1，0，0
		类和伪类选择器   0，0，1，0
		元素选择器      0，0，0，1
		通配选择器      0，0，0，0
		继承的样式      没有优先级
	
	比较优先级时，需要将所有的选择器的优先级进行相加和计算，最后优先级越高，则越优先显示（分组选择器是单独计算的），
	选择器的累加不会超过其最大的数量级，类选择器再高也不会超过 id选择器
	如果优先级计算后相同，此时优先级使用靠下的样式
	
	可以在某一个样式的后边添加 !important，则此时该样式会获取到最高的优先级，甚至超过内联样式，
	注意：在开发中一定要慎用！

#### 页面布局

**正常的布局流 ** 是将元素放置在浏览器视口内的系统。默认情况下，块级元素在视口中垂直布局——每个都将显示在上一个元素下面的新行上，并且它们的外边距将分隔开它们；

如果两个相邻元素都在其上设置外边距，并且两个外边距接触，则两个外边距中的较大者保留，较小的一个消失——这叫[外边距折叠](https://developer.mozilla.org/zh-CN/docs/Web/CSS/CSS_Box_Model/Mastering_margin_collapsing)；

absolute 绝对定位的元素不再存在于正常文档布局流中，[`top`](https://developer.mozilla.org/zh-CN/docs/Web/CSS/top)，[`bottom`](https://developer.mozilla.org/zh-CN/docs/Web/CSS/bottom)，[`left`](https://developer.mozilla.org/zh-CN/docs/Web/CSS/left)和[`right`](https://developer.mozilla.org/zh-CN/docs/Web/CSS/right) - 指定元素应距离每个包含元素的边的距离，而不是指定元素应该移入的方向；

绝对定位元素的“包含元素“ - 取决于绝对定位元素的父元素的position属性；如果所有的父元素都没有显式地定义position属性，那么所有的父元素默认情况下position属性都是static，绝对定位元素会被放在< html>元素的外面，并且根据浏览器视口来定位；绝对定位元素在HTML源代码中，是被放在< body>中的，但是在最终的布局里面，它离页面(而不是< body>)的左边界、上边界有30px的距离。

```css
/* static - 默认值，relative - 配合 top left right bottom 使用 */
.positioned {
  position: static; /* relative, absolute */
  background: yellow;
}
```

##### 【floats & positioning】

居中布局方法一：

```js
import styled from "styled-components";

const Panel = styled.div`
  position: absolute;
  top: 50%;
  left: 50%;                              
  transform: translate(-50%, -50%);
`;
```

居中布局方法二：

```js
import styled from "styled-component";

const Wrapper = styled.div`
  display: flex;
  justify-content: center;
  align-items: center;
`;
```

Divider 的 做法

```js
const Divider = styled.div`
	width: 2px;
	background: rgbd(255, 255, 255, 0.7);
	margin: 0 1.5rem;
`;
```

横线 的实现方法

```js
const Line = styled.div`
	width: 50%;
	height: 2px;
	background: white;
`;
```

styled(Temperature) 的实现

```js
import styled from "styled-component";

const Temperature = ({
  value,
  className,
})=>(
  <div className={className}>
  { value }
		°
  </div>
)

const StyledTemperature(Temperature)`
	font-size: 5rem;
`;

const CurrentCity = () => {
  <StyledTemperature value="24.13"/>
}
```

提取 Forecast 和 OtherCities 的公共部分组件

```js
const Forecast = () => (
	<div>
  	<Header title="Forecast">
  	<DayList />
  </div>
);

const OtherCities = () => (
	<div>
  	<Header title="OtherCities">
  	<CityList />
  </div>
);

// 重写成 👇
const SubContent = ({
  title,
  content,
}) => (
	<div>
  	<Header title={title}>
  	{content}
  </div>
);

const Forecast = () => (
	<SubContent
  	title="Forecast">
  	content={(<DayList />)}
  />
);
// ... OtherCities 类似

// 继续重写 👇，使用 children 
const SubContent = ({
  title,
  children,
}) => (
	<div>
  	<Header title={title} />
  	{children}
  </div>
);
const Forecast = () => (
	<SubContent title="Forecast"> 
  /* 所有传递于 开tag 和 闭tag 之间的内容，都会通过 children 传递 */
    <DayList />
  </SubContent>
);
```

Weather icon 的样式设置

```js
/* 相邻两个的话 左侧保持距离 */
const Container = styled.div`
	text-align: center;
	
	& ~ & {
		margin-left: 2rem; 
	}
`;
```

浮动元素会脱离正常的文档布局流，并吸附到其父容器的左边；

在正常布局中位于该浮动元素之下的内容，此时会围绕着浮动元素，填满其右侧的空间。

```css
img {
  float: left;
  margin-right: 30px;
}
```

多列布局

```css
/* 在宽度达到900px之前，整个视图的宽度将达到90%，在超过900px后，它将保持在这个宽度，并在视窗中居中 */
body {
  width: 90%;
  max-width: 900px;
  margin: 0 auto;
}

/* 默认情况下，子元素(这个<h1> (en-US) 和两个 <div>)将跨越整个body宽度的100%。如果我们希望将两个<div>放在一起，那么我们需要将它们的宽度设置为父元素的宽度的100%，或者更小 */
div:nth-of-type(1) {
  width: 48%;
  float: left;
  margin-bottom: 2%;
}

div:nth-of-type(2) {
  width: 48%;
  float: right;
}

footer {
  clear: both;
  margin-top: 2%;
}

```

float 的问题之一：非浮动元素的外边距不能用于它们和浮动元素之间来创建空间；

【流式布局（**liquid layout**）】

【基础盒模型】

```css
box-sizing: content-box;
box-sizing: border-box;
```

【Flex Box】- 一维布局

```css
flex-basis:auto; /* - 参照我的`width`和`height`属性 */
flex-basis:"30%";/* - 相对于其父弹性盒容器主轴尺寸的百分数 */
flex-basis:content; /* - 基于 flex 的元素的内容自动调整大小 */
/* 其他值包括：fit-content, max-content, min-content, fill */

text-align: center; /*定义行内内容如何相对它的块父元素对齐 */
```

【Gird】- 二维布局

可用 Firefox 开发者工具（Firefox Developer Tools）中的网格检查器（ [Grid Inspector](https://firefox-source-docs.mozilla.org/devtools-user/page_inspector/how_to/examine_grid_layouts/index.html) ）查看这些元素是如何被摆放在网格中的	

```css
.wrapper {
   display: grid;
   grid-template-columns: repeat(3, 1fr);
   grid-auto-rows: minmax(100px, auto);
   grid-column-gap: 10px;
   grid-row-gap: 1em;
   // 也可合并成 grid-gap 
}
.box1 {
    grid-column-start: 1;
    grid-column-end: 4;
    grid-row-start: 1;
    grid-row-end: 3;
}
.box2 {
    grid-column-start: 1;
    grid-row-start: 3;
    grid-row-end: 5;
}
footer {
  clear: both; //清除 float
}
```

#### 其他

##### **三种不同的前端渲染模式**

