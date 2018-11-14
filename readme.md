### Setup react with webpack

1. npm install webpack webpack-cli --save-dev
2. npm install react react-dom --save
3. npm install @babel/core babel-loader @babel/preset-env @babel/preset-react --save-dev
- babel-core: Transforms ES6 code to ES5
- babel-loader: Webpack helper to transpile code, given the the preset.
- babel-preset-env: Preset which helps babel to convert ES6, ES7 and ES8 code to ES5.
- babel-preset-react: Preset which Transforms JSX to JavaScript.
4. npm install css-loader style-loader --save-dev
5. npm install html-webpack-plugin --save-dev
6. Create **.babelrc** file with the following configurations:
```
{
  "presets": ["@babel/preset-env", "@babel/preset-react"]
}
```
7. Create **webpack.config.js** file with the following configurations:
```
const path = require("path");
const HtmlWebpackPlugin = require("html-webpack-plugin");

module.exports = {
  entry: "./src/index.js",
  output: {
    path: path.join(__dirname, "/dist"),
    filename: "index-bundle.js"
  },
  module: {
    rules: [
      {
        test: /\.js$/,
        exclude: /node_modules/,
        use: ["babel-loader"]
      },
      {
        test: /\.css$/,
        use: ["style-loader", "css-loader"]
      }
    ]
  },
  plugins: [
    new HtmlWebpackPlugin({
      template: "./src/index.html"
    })
  ]
};
```
8. Create src folder with index.js and index.html file