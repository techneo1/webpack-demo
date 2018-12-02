# Basic Setup

> Local installation is recommended

```
# webpack-cli is required for Webpack4
yarn add webpack webpack-cli --dev
```

# Creating a bundle

```
# without using any configuration file
npx webpack
```

```
# with configuration
npx webpack --config webpack.config.js
or
npx webpack     // webpack.config.js will be picked by default
```

# Asset management - Loading CSS

```
# package.json
yarn add css-loader style-loader --dev

# webpack.config.js
module: {
    rules: [
        {
            test: /\.css$/,
            loaders: ["style-loader", "css-loader"]
        }
    ]
}
```

> Loaders work from Right to Left

```
- Firstly, css-loader handles all the CSS imports
- Finally, style-loader injects styles into <style> of index.html
```

# Asset management - Loading Images

```
# package.json
yarn add file-loader --dev

# webpack.config.js
module: {
    rules: [
        {
            test: /\.(jpg|png|svg|gif)$/,
            loader: "file-loader"
        }
    ]
}
```
