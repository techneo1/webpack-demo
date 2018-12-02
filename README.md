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

# Asset management - Loading Images/Fonts

```
# package.json
yarn add file-loader --dev

# webpack.config.js
module: {
    rules: [
        {
            test: /\.(jpg|png|svg|gif)$/,
            loader: "file-loader"
        },
        {
            test: /\.(woff|Woff2|eot|ttf|otf)$/,
            loader: "file-loader"
        }
    ]
}
```

# Output Management

```
# Creating Multiple bundles
entry: {
    app: './scr/index.js',
    print: './src/print.js'
},
output: {
    filename: "[name].bundle.js"
}
```

# Output Management: Auto update index.html with bundle references

> html-webpack-plugin

```
# package.json
yarn add html-webpack-plugin --dev
```

```
# webpack.config.js
const HtmlWebpackPlugin = require('html-webpack-plugin');

plugins: [
    new HtmlWebpackPlugin({
        title: 'Output Management'
    })
]
```

# Output Management: Cleaning up /dist folder

> clean-webpack-plugin

```
# package.json
yarn add clean-webpack-plugin --dev
```

```
# webpack.config.js
const CleanWebpackPlugin = require('clean-webpack-plugin');

plugins: [
    new CleanWebpackPlugin['dist']
]
```

# Output Management: Adding Manifest file

> manifest-webpack-plugin

```
# package.json
yarn add manifest-webpack-plugin --dev
```

```
# webpack.config.js
const ManifestWebpackPlugin = require("manifest-webpack-plugin");

plugins: [
    new ManifestWebpackPlugin(path.join("dist", "manifest.json"))
]
```
