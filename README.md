# My React Boilerplate

## Step by Step
- npm init
- npm install webpack webpack-dev-server path // installing webpack and few dependencies
- config webpack in ./webpack.config.js
```
inside ./webpack.config.js

const path = require('path');
module.exports = {
  entry: './client/index.js',
  output: {
    path: path.resolve('dist'),
    filename: 'index_bundle.js'
  },
  module: {
    loaders: [
      { test: /\.js$/, loader: 'babel-loader', exclude: /node_modules/ },
      { test: /\.jsx$/, loader: 'babel-loader', exclude: /node_modules/ }
    ]
  }
}
```
- npm install babel-loader babel-core babel-preset-es2015 babel-preset-react --dev // install babel
- config babel in ./babelrc
```
inside ./.babelrc

{
    "presets":[
        "es2015", "react"
    ]
}
```
- create folder client in root and index.html and index.js inside client folder

```
you can skip this section for basic testing to verify the set-up is works

inside index.js add

console.log("hello world")

inside index.html add

<!DOCTYPE html>
<html>
  <head>
    <meta charset="utf-8">
    <title>React App Setup</title>
  </head>
  <body>
    <div id="root">

    </div>
  </body>
</html>



```
- npm install html-webpack-plugin
- update file ./webpack.config.js
```
./webpack.config.js

const path = require('path');

const HtmlWebpackPlugin = require('html-webpack-plugin');
const HtmlWebpackPluginConfig = new HtmlWebpackPlugin({
  template: './client/index.html',
  filename: 'index.html',
  inject: 'body'
})

module.exports = {
  entry: './client/index.js',
  output: {
    path: path.resolve('dist'),
    filename: 'index_bundle.js'
  },
  module: {
    loaders: [
      { test: /\.js$/, loader: 'babel-loader', exclude: /node_modules/ },
      { test: /\.jsx$/, loader: 'babel-loader', exclude: /node_modules/ }
    ]
  },
  plugins: [HtmlWebpackPluginConfig]
}
```
- adding start script in package.json
```
{
  "name": "myreactboilerplate",
  "version": "1.0.0",
  "description": "learn to setup react environment",
  "main": "index.js",
  "scripts": {
    "test": "echo \"Error: no test specified\" && exit 1",
    "start": "webpack-dev-server"
  },
  "repository": {
    "type": "git",
    "url": "git+https://github.com/elepampam/MyReactBoilerplate.git"
  },
  "author": "elepampam",
  "license": "MIT",
  "bugs": {
    "url": "https://github.com/elepampam/MyReactBoilerplate/issues"
  },
  "homepage": "https://github.com/elepampam/MyReactBoilerplate#readme",
  "dependencies": {
    "babel-core": "^6.26.0",
    "babel-loader": "^7.1.2",
    "babel-preset-es2015": "^6.24.1",
    "babel-preset-react": "^6.24.1",
    "html-webpack-plugin": "^2.30.1",
    "path": "^0.12.7",
    "webpack": "^3.8.1",
    "webpack-dev-server": "^2.9.3"
  }
}
```
- npm start //try to start the set-up