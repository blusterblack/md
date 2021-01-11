# Create React App from scratch

## 0. Lazy

```bash
npm init -y
npm install react react-dom react-hot-loader @reduxjs/toolkit react-redux 
npm install --save-dev eslint @babel/core @babel/preset-react @babel/preset-env @babel/cli webpack webpack-cli webpack-dev-server style-loader css-loader babel-loader
.\node_module\.bin\eslint --init
```

## 1. Init

Init npm and git

```bash
npm init -y
git init
npm install --save-dev eslint
```

```bash
./node_modules/.bin/eslint --init 
```

Create public/index.html to host React app

```html
<!DOCTYPE html>
<html>
  <head>
    <meta charset="UTF-8" />
    <meta
      name="viewport"
      content="width=device-width, initial-scale=1, shrink-to-fit=no"
    />
    <title>Your app title</title>
  </head>

  <body>
    <div id="root"></div>
    <noscript>
      You need to enable JavaScript to run this app.
    </noscript>
    <script src="../dist/bundle.js"></script>
  </body>
</html>
```

Create .gitignore

```
node_modules/
dist/
```

## 2. Babel

Babel transform code to browser-compatible code

Preset-env: for ES6+

--save-dev: Package will appear in your devDependencies(only for devlopment, user dont need)

preset: collection of plugins

```bash
npm install --save-dev @babel/core @babel/preset-react @babel/preset-env @babel/cli
```

Create .babelrc file to load preset

```json
{
  "presets": ["@babel/env", "@babel/preset-react"]
}
```

## 3. Webpack

Webpack bundle your files into static asset.

Default webpack only work with JS and json file, need loader to bundle other files.

dev-server: live reloading with webpack

style-loader: inject CSS into DOM

```bash
npm install --save-dev webpack webpack-cli webpack-dev-server style-loader css-loader babel-loader
```

Create webpack.config.js:

entry: where to create dependancy graph

mode: optimization for bundling

rule: match files to loaders

```javascript
const path = require('path');
const webpack = require('webpack');

module.exports = {
  entry: './src/index.js',
  mode: 'development',
  module: {
    rules: [
      {
        test: /\.(js|jsx)$/,
        exclude: /(node_modules|bower_components)/,
        loader: 'babel-loader',
        options: { presets: ['@babel/env'] },
      },
      {
        test: /\.css$/,
        use: ['style-loader', 'css-loader'],
      },
    ],
  },
  resolve: { extensions: ['*', '.js', '.jsx'] },
  output: {
    path: path.resolve(__dirname, 'dist/'),
    publicPath: '/dist/',
    filename: 'bundle.js',
  },
  devServer: {
    contentBase: path.join(__dirname, 'public/'),
    port: 3000,
    publicPath: 'http://localhost:3000/dist/',
    hotOnly: true,
  },
  plugins: [new webpack.HotModuleReplacementPlugin()],
};
```

| script |                                       |
| ------ | ------------------------------------- |
| build  | webpack --mode development            |
| start  | webpack-dev-server --mode development |
| lint   | npx eslint                            |

## 4. React + Redux

hot-loader for live reload with webpack

```bash
npm install react react-dom react-hot-loader @reduxjs/toolkit
```

Create /src/index.js

```javascript
import React from 'react';
import ReactDOM from 'react-dom';
import { Provider } from 'react-redux';
import App from './components/App';
import store from './store';

ReactDOM.render(
  // eslint-disable-next-line react/jsx-filename-extension
  <Provider store={store}><App /></Provider>,
  document.getElementById('root'),
);
```

Create /src/components/App.jsx

```javascript
import React from 'react';
import { hot } from 'react-hot-loader';

function App() {
  return (
    <div>
      <h1> Hello, World! </h1>
    </div>
  );
}

export default hot(module)(App);
```
