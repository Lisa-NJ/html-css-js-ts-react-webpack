把自己的代码打包转换成浏览器认识的{html+css+js}

套件让代码格式规范或漂亮

Vue、React、Angular 都会有 CLI，使用到 Webpack



```
mkdir webpack-demo
npm init  //生成 package.json
npm i -D webpack //--save-dev 缩写为 -D 
```

package.json - 应用的蓝图，显示已安装的npm应用

npm 类似 苹果手机的 App Store，npmjs.com

npm应用 是给开发者的，webpack 是其中之一

package.json / scripts - 可以下一些自定的指令

```json
"scripts": {
    "build": "webpack"
  },
```

执行命令

```bash
$ npm run build
Do you want to install 'webpack-cli' (yes/no): y
```

build完成后，生成 build / main.js

webpack 预设： 在没有新增 webpack.config.js时，预设把 src / index 当成专案的入口，将该入口所有 js 都变成一个 js，放在 dist 文件夹下；

新增文件 webpack.config.js，并且：

**配置 webpack.config.js** -- 参考[官方文档](https://webpack.js.org) / Documentation

Entry、Output、Loaders、Plugins、Mode

Loaders：读档有关的事

Plugins：通过引入插件，加强webpack没有的功能

Mode：开发模式 / 上线模式，开发模式下，代码不会被压缩

```js
const path = require('path');

module.exports = {
    //指定入口文件
    entry: './src/index.js',
    //指定打包文件所在的目录
    output: {
        //指定打包文件的路径
        path: path.resolve(__dirname, 'dist'),
        //打包后生成的文件
        filename: "main.bundle.js"
    },
}
```

配置另一条指令

```json
"dev":"webpack serve"
```

执行

```bash
$ npm run dev
 ...Would you like to install 'webpack-dev-server' package? (That will run 'npm install -D webpack-dev-server') (Y/n) y
```

webpack-dev-server 支持热加载，并对更改进行实时更新；

打包后，dist目录下并没有生成bundle.js文件，webpack-dev-server将打包好的文件放在了内存中；
 `把bundle.js放在内存中的好处是：加载速度快`;

html-webpack-plugin插件会自动把bundle.js注入到index.html页面；

打开浏览器，并输入：http://localhost:8080/

新建 dist / index.html，并补充

```html
<script src="./main.bundle.js"></script>
```

配置server

```js
devServer: {
  contentBase: path.join(__dirname, 'dist'),
}
```



**loader** 用于对模块的源代码进行转换。loader 可以使你在 `import` 或 "load(加载)" 模块时预处理文件。因此，loader 类似于其他构建工具中“任务(task)”，并提供了处理前端构建步骤的得力方式。loader 可以将文件从不同的语言（如 TypeScript）转换为 JavaScript 或将内联图像转换为 data URL。loader 甚至允许你直接在 JavaScript 模块中 `import` CSS 文件！

css-loader：把  .css 文件打包进 bundle.js

style-loader：把 .css 文件定义好的样式 存入 index.html <head> / <style> 里面

安装 css-loader、style-loader

```bash
yarn add -D css-loader style-loader
```

Webpack.config.js 文件中增加：

```js
   module: {
        rules: [
            {
                test: [/\.css$/],
                use: ['style-loader', 'css-loader']
            },
            {
                test: [/\.less$/],
                use: ['style-loader', 'css-loader', 'less-loader']
            }
        ],
    }
```

上面配置文件里面也包括了对 .less 文件的处理。



打包后 css 独立出来，需要插件 **MiniCssExtractPlugin**

```bash
$ yarn add -D mini-css-extract-plugin
```

Webpack.config.js

```js
const MiniCssExtractPlugin = require("mini-css-extract-plugin");

module.exports = {
  plugins: [new MiniCssExtractPlugin()],
  module: {
    rules: [
      {
        test: /\.css$/i,
        use: [MiniCssExtractPlugin.loader, "css-loader"],
      },
    ],
  },
};
```

