# Project Setup without Create React App

This project was created from scratch without using create-react-app package

## 1. Create a Node project

In the project directory, you can run:

### `npm init -y`

This will create package.json file

## 2. Install Babel dependencies

In the project directory, you can run:

### `npm install --save-dev @babel/core babel-loader @babel/cli @babel/preset-env @babel/preset-react`

Babel is a compiler that converts your modern JavaScript into backward-compatible versions to be supported by older browsers or environments

## 3. Install Webpack dependencies

In the project directory, you can run:

### `npm install --save-dev webpack webpack-cli webpack-dev-server`

Webpack is a static module bundler for modern JavaScript applications. It can take different files and bundles them into a single JavaScript file

## 4. Install HtmlWebpackPlugin

In the project directory, you can run:

### `npm install --save-dev html-webpack-plugin`

The HtmlWebpackPlugin is the package that simplifies the creation of HTML files to serve your Webpack bundles

## 5. Install React dependencies

In the project directory, you can run:

### `npm install react react-dom `

React is a JavaScript library for creating user interfaces.
The React package itself contains only the functionality necessary to define React components therefore it is typically used together with a React renderer like react-dom to create elements for the web. react and react-dom are the main dependencies we need to actually use React in our apps

## 6. Add React files

create a public folder and in the created folder create an index.html file and add the following code in it

###

```
<!DOCTYPE html>
<html lang="en">
  <head>
    <meta charset="UTF-8" />
    <meta http-equiv="X-UA-Compatible" content="IE=edge" />
    <meta name="viewport" content="width=device-width, initial-scale=1.0" />
    <title>Pienary Code</title>
  </head>
  <body>
    <div id="root"></div>
  </body>
</html>
```

## 7. create an src folder and in it create an App.js file and add the following code

```
import React from "react";

export default function App() {
  return <h1>Welcome to Pienary Code !!!</h1>;
}

```

## 8. create an index.js which will be the entry of our app in the src folder

```
import React from "react";
import { createRoot } from "react-dom/client";
import App from "./App";

const container = document.getElementById("root");

const root = createRoot(container);
root.render(<App />);
```

## 9. configure Babel

In the root folder create a file named .babelrc and add the following code

###

```
{
    "presets": ["@babel/preset-env","@babel/preset-react"]
}
```

## 10. configure Webpack

Create a file named webpack.config.js and add the following code

###

```
const HtmlWebpackPlugin = require("html-webpack-plugin");
const path = require("path");

module.exports = {
  entry: "./src/index.js",
  mode: "development",
  output: {
    path: path.resolve(__dirname, "./dist"),
    filename: "index_bundle.js",
  },
  target: "web",
  devServer: {
    port: "5000",
    static: {
      directory: path.join(__dirname, "public"),
    },
    open: true,
    hot: true,
    liveReload: true,
  },
  resolve: {
    extensions: [".js", ".jsx", ".json"],
  },
  module: {
    rules: [
      {
        test: /\.(js|jsx)$/,
        exclude: /node_modules/,
        use: "babel-loader",
      },
    ],
  },
  plugins: [
    new HtmlWebpackPlugin({
      template: path.join(__dirname, "public", "index.html"),
    }),
  ],
};

```

## 11. add scripts in package.json

In the package.json file in the scripts object scripts that will be used to run Webpack and start our application
add scripts as mentioned below

###

```
"scripts": {
    "start": "webpack-dev-server .",
    "build": "webpack ."
  }
```

## 12. start your application

Run `npm start` to start the application

###
