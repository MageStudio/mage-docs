# Bundling your application

This section of the documentation is not going to be a in-depth explanation on how bundling tools work or how you can configure them, but it will provide examples you can use and extend depending on your needs.

Each configuration will assume two outputs for your app, one for css in `dist/app.css` and the main script in `dist/app.js`.

## Webpack

First, install the required dependencies:

```bash
npm i --save webpack webpack-cli babel-loader @babel/core @babel/preset-env @babel/plugin-transform-runtime @babel/plugin-proposal-class-properties
```

### webpack.config.js

```js
const path = require('path');

module.exports = {
    mode: 'production',
    cache:   false,
    devtool: false,
    entry: {
        'app': './src/index.js'
    },
    output: {
        path: path.resolve(__dirname, 'dist'),
        filename: 'app.js',
    },
    module:  {
        rules: [{
            test: /\.js$/,
            loader: 'babel-loader',
            exclude: [/node_modules/, /static/]
        }]
    },
    resolve: {
        modules: [
            'static',
            'src',
            'node_modules'
        ]
    },
    performance: {
        hints: false,
        maxAssetSize: 1000000,
        maxEntrypointSize: 800000,
    },
    plugins: [],
};
```

As you can see this example is using `babel-loader`. Its configuration will look like this:

### babel.config.js

```js
const config = {
    presets: [
        ["@babel/preset-env", {
            "targets": {
                "browsers": ["> 0.25%", "ie >= 11"]
            }
        }],
    ],
    plugins: [
        "@babel/plugin-transform-runtime",
        "@babel/plugin-proposal-class-properties"
    ]
};

module.exports = config;
```
