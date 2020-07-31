# Start Project With Webpack

_GLOBAL WEBPACK_

> npm install -g webpack

## package.json 作成

Myproject に移動して、下記のようにする。

> yarn init -y

package.json が生成される

## webpack, webpack-cli をローカルインストール

> yarn add webpack webpack-cli --dev

**_--dev すると devDependencies に追記される
(単に yarn add した場合は、dependencies に追記される)_**

- devDependencies は開発時にのみ必要なモジュール
- dependencies は実行時にも必要なモジュール

## webpack.config.js の作成

webpack.config.js を作成して下記のように設定

```javascript:
const path = require("path");

module.exports = {
  mode: "development",
  entry: "./src/index.js",
  output: {
    filename: "bundle.js",
    path: path.join(__dirname, "public"),
  },
};
```

## Babel をローカルインストール

> yarn add babel-loader @babel/core @babel/preset-env --dev

## webpack.config.js に babel を使うための設定を追加

```javascript:
    {
        ...
       module: {
            rules: [
            {
                test: /\.js$/,
                exclude: /node_modules/,
                use: [
                {
                    loader: "babel-loader",
                    options: {
                    presets: [["@babel/preset-env", { modules: false }]],
                    },
                },
                ],
            },
            ],
        },
    }
```
