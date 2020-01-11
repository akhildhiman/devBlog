---
title: 'Setting up a React project using Webpack and Babel'
date: '2019-12-22'
category: "React"
---

![](https://miro.medium.com/max/1200/1*c5BkVEjwpew7yjKixdIdYQ.png)

Webpack is currently one of the hottest tools out there. It is quite difficult to understand in the beginning but I'd say Webpack is a really beneficial tool that optimizes your Web application. Let's first understand the basics.

As our application grows, we split it into multiple files, known as modules. Webpack is a module bundler for all our assets. In simple words, webpack processes all the modules and generates a single file known as **bundle** and give it to the browser that it will understand. 
 
 
In this article, we're going to set up our React application using Webpack and Babel. So let's get started.

```js
mkdir react-webpack-setup

npm init -y
```

```npm init-y``` will generate a package.json file in your root folder of ```react-webpack-setup``` with all the information.

```js
{
  "name": "react-webpack-setup",
  "version": "1.0.0",
  "description": "",
  "main": "index.js",
  "scripts": {
    "test": "echo \"Error: no test specified\" && exit 1"
  },
  "keywords": [],
  "author": "",
  "license": "ISC"
}
```

It will also generate a **Node_Modules** folder which contains npm libraries such as react, react-dom (which we're going to use) that our project needs. You shouldn't push it to  Github, instead create a ```.gitignore``` file and push inside it. Whosoever clones your repo will be able to download it themselves based on your ```package.json```

Now, we're going to create an src folder where we'll have our index.js and index.css files.

```js
touch src/index.js
touch src/index.css
```
We're also going to install react and react-dom from npm.

```js
npm i react react-dom --save
```

```index.js``` would look something like this. Here we have a simple App component. 



```js
import React from "react"
import ReactDOM from "react-dom"
import "./index.css"

const App = () => {
    return (
        <div className="App">
            Hello World
        </div>
    )
}


ReactDOM.render(<App />, document.getElementById("root"))
```

Interestingly, ```index.js``` is a module that contains some modern things like JSX and arrow functions. That's where Babel comes in. We'll discuss that later.

Next up, we're going to install some dependencies. 

```js
npm install --save-dev @babel/core @babel/preset-env @babel/preset-react
webpack webpack-cli webpack-dev-server babel-loader css-loader
style-loader html-webpack-plugin
```
Notice these are all **dev dependencies**. So, there's something you should know about dependencies. Normal dependencies like ```react``` and ```react-dom``` are the ones that our application needs in order to **run** whereas dev-dependencies are the ones that our application needs in order to **build**.

**Webpack takes all our modules (we only have a single index.js module here), and create a single bundled file that we can later reference in our ```index.html``` file.**

Now, in order to configure webpack, we need to create a ```webpack.config.js``` file in our root folder.

```js 
touch webpack.config.js
```

```js
const path = require("path")
const HtmlWebpackPlugin = require("html-webpack-plugin")
const MiniCssExtractPlugin = require("mini-css-extract-plugin");


module.exports = {
    entry: "./src/index.js",
    mode: "development",
    devtool: 'inline-source-map',
    output: {
        path: path.resolve(__dirname, "dist"),
        filename: "bundle.js"
    },
    
    module: {
        rules: [
            {test: /\.(js|jsx)$/, use: "babel-loader"},
            {test: /\.(css)$/, use: ["style-loader", "css-loader"]}
        ]
    },

    plugins: [
        new HtmlWebpackPlugin({
          template: "./src/index.html"
        }),
        new MiniCssExtractPlugin({
            filename: "bundle.css"
        })
    ]
}

```
We're telling webpack the entry point of our application i.e., ```index.js```.
Mode can be set to development or production.
Source-maps are cool in case of debugging. Source map keeps the transformed code and the original code in sync so that when debugging, the developer has the option to look into the original code instead of the complex bundled code. 
Finally, we're telling webpack to emit the bundle in the dist folder.

Next, there's a module with a set of rules defined. It simply says whenever a js/jsx module is encountered, hand it over to the babel-loader. Babel-loader simply converts/transpiles the ES6 code to the code that the browser can understand. 

The css-loader interprets ```@import``` and ```url()``` like ```import/require()``` and will resolve them. Style loader takes the css and insert into the page.

HtmlWebpackPlugin generates an```index.html``` automatically which includes a reference to the ```bundle.js``` file. We can also create an index.html file. Webpack uses index.html as a template. It would look something like this.

```js
<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <meta http-equiv="X-UA-Compatible" content="ie=edge">
    <title>React Webpack Setup</title>
</head>
<body>
    <div id="root"></div>
</body>
</html>
```

We're mounting our React app here ```<div id="root"></div>```.We're not using script tag here, because HtmlWebpackPlugin will create a dist folder with index.html and add a script tag automatically referencing bundle.js. Basically, we're creating a template for the generated HTML file, not the actual file.
HtmlWebpackPlugin will copy that template, and add your changes on top of it in the index.html that it spits out.

MiniCssExtractPlugin extracts CSS from every module and returns a single bundled CSS file called **bundle.css**.


Now, create a .babelrc file.

```js
{
 "presets": [
        "@babel/preset-env", "@babel/preset-react"
    ]
}
```

We know that Babel transpiles code that the browser can understand. It uses various plugins like ```'@babel/plugin-transform-arrow-functions'``` which transpiles ES6 arrow functions. Babel has moved one step ahead by creating presets. Presets contain various in-built plugins so that we don't have to use separate plugins for every other transformation. How cool!

```@babel/preset-env``` transpiles ES6 syntax to ES5 or whatever the browser can understand whereas ```@babel/preset-react``` handles the conversion of JSX modules into the simpler form.


Now, we've set up everything, it's time to start the server, and to do that, we're going to add a script in our package.json file.

```js
    "start": "webpack"
```

After you type npm start, you'll see **Hello World** on the screen. Also, you'll get a brand new dist folder with index.html and bundle.js file.

Alternatively, if you use ```webpack-dev-server```, you won't see the dist folder. Stackoverflow says- **webpack-dev-server serves from memory. If you want to see the files on disk during development with webpack-dev-server, you'll need to run a standard webpack build concurrently.**


Thank You for reading this article. Follow me on [Twitter](https://www.twitter.com/_himalayan_) for more updates.



































