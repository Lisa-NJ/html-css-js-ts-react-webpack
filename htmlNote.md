table tbody tr td

<dl>
  <dt>A</dt>
  <dd>Apple</dd>
  <dd>Ant</dd>
   <dt>B</dt>
  <dd>Before</dd>
  <dd>Below</dd>
</dl>

#### 常识

软件分 B/S C/S 两种，前端工程师 主要负责开发：B/S 中的 B；

伯纳斯李 1994年建立 万维网联盟(W3C)，该组织的出现：为了制定网页开发的标准，以使同一个网页在不同的浏览器中有相同的效果；我们编写的网页都需要遵循 W3C 的规范。

文件的后缀名决定了打开文件的软件，.html --> 浏览器

SEO - *Search engine optimization*

##### **进制**

十进制

二进制：所有数据在计算机底层都会以二进制的形式保存

八进制

十六进制：配合二进制使用，十六进制的写法比二进制的更容易理解；

内存：可以想像为一个有多许多小格子组成的容器，每一个小格子中可以存储一个1或者一个0

8bit = 1 bytes（字节）

1024 byte = 1 kb（千字节）

1024 kb = 1 mb（兆字节）

1024 mb = 1 gb（吉字节）

1024 gb = 1 tb（特字节）

1024 tb = 1 pb

##### **字符编码**

所有数据在计算机中存储时都是以二进制形式存储的，文字也不例外；

存储到内存中时 - 编码：字符 --> 二进制 的过程

读取内存时，发生 - 解码：字符 <-- 二进制 的过程

字符集（Charset）：编码和解码所采用的规则

乱码：如果编码和解码采用不同的字符集 会导致

常见的字符集：ASCII、ISO88591、GB2312、GBK、UTF-8

ASCII - 7位  128

ISO88591 - 8位 256

GB2312 - 国标

GBK - 扩展

UTF-8 - 万国码，包含所有国家的符号 - 开发使用的字符集

##### **工具** **& 资源**：

zeal - 可以查看离线文档，windows 版，报错：SSL handshake failed；//...待解决

Dash - mac 版

==> MDN - 比较权威，上面两个软件下载的文档来自于 MDN 

W3school - 中文的，有些内容偏旧

学习真实网站：京东、Amazon等

#### 基础

<标签开始>内容</ 标签结束>

```html
<h1>回乡偶书</h1>
<h2>贺知章</h2>
<p>少小离家老大回</p>
<p>乡音无改鬓毛衰</p>
<p>儿童相见不相识</p>
<p>笑问客从何处来</p>
```

完整的网页 = 根标签 + head + body

```html
<!doctype html>  <!--文档声明：html5-->
<html>
  <head>
    <!--head 是网页的头部，head 中的内容不会直接出现在网页中，主要用来帮助浏览器或搜索引擎来解析网页-->
    <!-- meta：元数据 -->
    <!-- charset 属性可设置网页的字符集，避免乱码，要与当前编码一致 -->
    <meta charset='utf-8'>
    <!-- title 中的内容会显示在浏览器标题栏，搜索引擎会主要根据title中的内容来判断网页的主要内容 -->
    <titile>网页的标题</titile>
  </head>
  <body>
    <!--网页的可见部分，注释的写法，注释会被浏览器忽略，不显示在网页中-->
    <!--标签一般成对出现，但是也有特例：自结束标签-->
    <img>
    <input>
    <p>
      <!--属性的语法：值对，使用"" 或 ''-->
      This is <font color='red'>the 3rd</font>font> page.
    </p>
  </body>  
</html>
```

windows 操作系统下 建议使用 Notepad++，而不使用 记事本；

注释不能嵌套；

自结束标签

<img> 或 <img />

<input> 或 <input />

浏览器解析源码时是一行一行从上向下解析的；

迭代 网页的版本：HTML4 HTML5 XHTML2.0 ...

```　html
<!-- 多个空格 -->
<p>
  Today is         good!
  a<b>c 
</p>
```

在网页中编写的多个空格默认情况下会自动被浏览器解析为一个空格；

在 html 中，有些时候不能直接书写一些特殊符号

​	比如：多个连续空格，或者字母两侧的大于和小于号 a<b>c 会被解析成 a**c**

如果我们需要在网页中书写这些特殊的符号，需要使用 html 中的实体（转义字符）

实体的语法：**&实体名;**  -- 更多的可以查询 W3School/实体

​	& nbsp;  - 空格，可以写多个 non break space

​	& gt; - 大于号

​	& lt; - 小于号

​	& copy; - 版权符号

##### meta

用来设置网页中的一些元数据，元数据不是给用户看的

​	name 指定的数据的名字

​	content 指定的数据的内容

​	charset 字符集

```html
<!-- 
	keywords 显示网站的关键字，可同时指定多个关键字，关键字使用,隔开
	description 网站的描述，会显示在搜索引擎的搜索结果中
	title 标签的内容会作为搜索结果的超链接上的文字显示
	http-equiv 将页面 n秒  后重定向到另一个网站
-->
<meta name='keywords' content='html,frontend,css'>
<meta name='description' content='a good website'>
<meta http-equiv='refresh' content='3;url=https://www.mozilla.org'>
<title>Document</title>
```

[**语义化标签**](https://blog.51cto.com/u_15069489/4219928) - 文本结构和文本内容 semantics

在网页中 html 专门负责网页的结构，所以在使用 html 标签时，应该关注标签的语义，而不是它的样式；

h1 ～ h6 共六级，重要性递减，一般一个页面只会有一个 h1，一般情况下标题标签只会使用 h1～h3，标题标签都是块元素（在页面中独占一行的元素 block element）

行内元素（inline element）- 不独占一行

```html
<!-- 
hgroup 用来为标题分组，可以将一组相关的标题同时放入 hgroup 中；
p 表示页面的一个段落，也是一个块元素，会换行
em 表示语音语调、语气的加重，不换行 - 行内元素
strong 表示强调重要的内容
blockquote 表示一个长引用 - 块元素
q 短引用 - 行内元素
br 换行
sub
sup
small
span
-->
<hgroup>
  <h1>回乡偶书二首</h1>
  <h2>其一</h2>
</hgroup>
<p>少小离家<em>老大</em>回</p>
鲁迅说：
<blockquote>这句话我从来没有说过</blockquote>
子曰<q>学而时习之，不亦乐乎</q>
```

块元素（block element） - 用来对网页进行宏观布局

行内元素 -（inline element）- 包裹文字，设置特殊效果

一般情况下，会在块元素中放行内元素，反之不然；

p 元素中不能放任何的 块元素；

浏览器解析网页时，会自动对网页中不符合规范的内容进行修正 - 代码在内存中的结构，比如：

​	标签写在了根元素的外部；

​	p 元素中嵌套了块元素；

​	根元素中出现了 head 和 body 以外的子元素；

可以通过 开发者工具 的 Elements 来查看 网页在内存中的结构；

##### **列表** - list

html 中有三种列表：有序 ol、无序 ul、定义 dl，li 表示列表项；这三者用的最多的是 ul，常用来创建导航菜单

列表直接可以互相嵌套；

dl 创建定义列表，dt 表示定义的内容，dd 对内容进行解释说明

```html
<ul>
  <li>结构</li>
  <li>表现</li>
  <li>行为</li>
</ul>
<ol>
  <li>结构</li>
  <li>表现</li>
  <li>行为</li>
</ol>
<dl>
  <dt>结构</dt>
  <dd>结构表示网页的结构，</dd>
  <dd>用来规定网页中哪里是标题、段落</dd>
</dl>
```

- 和 1.2.3. 在不同的浏览器中表现不同，所以一般都会去掉 => 有序 和 无序 实际使用时没有太大区别；

##### **超链接 - 路径**

当需要跳转一个服务内部的页面时，一般我们都会使用相对路径，相对路径使用 . 或者 .. 开头

./  ../

./ 可以省略不写，如果不写 ./ 也不写 ../ 就相当于写了 ./

./ 表示当前文件所在的目录

../ 表示当前文件所在目录的上一级目录

```html
<!--
	target：_self 默认值，在当前页面中打开超链接，_blank 在新标签页打开 
	lorem 可以生成一串英文文本
	# 可以跳转至 页面顶部，开发中，可以作为一个占位符
	href=“javascript:;” 占位符，没有任何作用
	id属性：唯一不重复的，每个标签都可以添加一个 id属性，是元素的唯一标识
	#bottom：可跳转至 id为 bottom 的元素位置
-->
<a href="https://www.baidu.com" target="_blank">超链接1</a>
<a href="https://www.baidu.com" target="_self">超链接2</a>

<a href="#bottom">去底部</a>

<a id="bottom" href="#" target="_self">回顶部</a>
```

_blank 容易多打开新的空白窗口

##### **图片**

图片标签用于向当前页面中引入一个外部图片

使用 img 标签来引入外部图片，img 是一个自结束标签

img 属于替换元素（块和行内元素之间，具有两种元素的特点）

属性：

​	src - 指定外部图片的路径（规则和超链接的路径一样）

​	alt - 图片的描述，这个描述默认情况下不会显示，有些浏览器会在图片无法加载时显示；搜索引擎会根据 alt 中的内容来识别图片，如果不写 alt 属性则图片不会被搜索引擎收录

​	width - 图片宽度（单位：像素）

​	height - 图片高度，宽度和高度中如果只修改了一个，则另一个会等比例缩放

​	注意：一般情况在 pc 端，不建议修改图片的大小；但是在移动端，经常需要对图片进行缩放（大图缩小）

```html
<img src="./img/1.gif" alt="松鼠">
<img width="200" src="http://...">
<img src="...base64文件的内容...">
```

图片的格式：

| 格式        | 支持的颜色 | 透明效果     | 动图   | 用途                 |
| ----------- | ---------- | ------------ | ------ | -------------------- |
| jpeg（jpg） | 丰富       | 不支持       | 不支持 | 照片                 |
| gif         | 少         | 简单透明     | 支持   | 颜色单一的，动图     |
| png         | 丰富       | 支持复杂透明 | 不     | 专为网页而生         |
| webp        | 丰富       | 支持         | 支持   | Google / 小 / 兼容差 |

效果一样：用小的

效果不一样：用效果好的

base64 - 将图片使用 base64 编码，这样可以将图片转换为字符，通过字符的形式来引入图片；一般都是一些需要和网页一起加载的图片才会使用 base64

把图片转为 base64：上网 图片在线转换

##### 内联框架 - iframe

用于向当前页面中引入一个其他页面

src - 指定引入的页面的路径，既可以引入外部页面，也可以内部页面，不会被 SEO 使用

frame border - 指定内联框架的边框 0 表没有边框

```html
<iframe src="http://www.qq.com" width="800" height="600" frameborder="0"></iframe>
```

使用的机会不多

##### **音视频播放**

音视频文件引入时，默认情况下不允许用户自己控制播放停止；

audio 标签用来向页面中引入一个外部的音频文件

video 标签用来向页面中引入一个外部的视频文件

​	controls - 是否允许用户控制播放

​	autoplay - 是否自动播放，如果设置了 autoplay，则音乐在打开页面时会自动播放，但目前大部分浏览器不会自动对音乐进行播放，需等用户点击播放

​	loop - 循环播放

除了通过 src 来指定外部文件的路径外，还可以通过 source 来指定文件

```　html
<audio src="./source/audio.mp3" controls autoplay loop></audio>
<audio src="./source/audio.mp3" controls></audio>

<!-- 通过 source 来指定，考虑到兼容性 IE8不支持 source,但可以用 embed -->
<audio controls>
  对不起，您的浏览器不支持播放音频！请升级浏览器！
  <source src="./source/audio.mp3">
  <source src="./source/audio.ogg">
  <embed src="./source/audio.mp3" type="audio/mp3" width="300px" height="100px">
</audio>

<video controls>
  对不起，您的浏览器不支持播放视频！请升级浏览器！
  <source src="./source/audio.mp4">
  <embed src="./source/audio.mp4" type="video/mp4" width="300px" height="100px">
</video>
```



//...待整理 24/5

##### HTML编辑器：

推荐：VS Code 或者 Sublime Text

缺省：记事本（Windows），TextEdit（OS X），LINUX用户可选：vi、vim、emacs

其他浏览器可通过菜单“More Tools/Developer Tools”进入调试；

调试的方法：https://zh.javascript.info/debugging-chrome 

HTML元素=HTML标签（HTML tag）

开始/开放标签(opening tag)，结束/闭合标签(closing tag)

使用“/”关闭空元素更长远，HTML、XHTML和XML都接受这种方式；

##### 常见标签

head, title, meta, style, script, noscript, base, link

body, h1~h7, br, hr, p, div, a, img, 

pre, figure, 

label：扩大点击区域

template: 

``` html
<figure>
  <pre role="img" aria-label="ASCII COW">
      ___________________________
  &lt; I'm an expert in my field. &gt;
      ---------------------------
          \   ^__^
           \  (oo)\_______
              (__)\       )\/\
                  ||----w |
                  ||     ||
  </pre>
  <figcaption id="cow-caption">
    A cow saying, "I'm an expert in my field." The cow is illustrated using preformatted text characters.
  </figcaption>
</figure>
```

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

##### 
