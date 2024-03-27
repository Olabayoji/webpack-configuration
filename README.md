# Webpack Configuration

## Description

This project provides a basic webpack configuration setup for bundling JavaScript files, handling SVG files, and styling with CSS. It includes configurations for both development and production environments.

## Installation

To use this configuration, make sure you have Node.js and npm installed on your machine.

1. Clone this repository or create a new project directory.
2. Navigate to the project directory in your terminal.
3. Run `npm install` to install all the dependencies specified in the `package.json` file.

## Usage

- `npm start`: Starts the webpack development server.
- `npm run build`: Builds the project for production using webpack.
- `npm test`: No tests specified in this configuration.

## Dependencies

- **webpack**: "^5.91.0"
- **webpack-cli**: "^5.1.4"
- **webpack-dev-server**: "^5.0.4"
- **@babel/core**: "^7.24.3"
- **babel-loader**: "^9.1.3"
- **html-webpack-plugin**: "^5.6.0"
- **css-loader**: "^6.10.0"
- **style-loader**: "^3.3.4"
- **svg-loader-js**: "^1.0.7"
- **path**: "^0.12.7"

## Webpack Configuration

```javascript
const HtmlWebpackPlugin = require("html-webpack-plugin");
const path = require("path");

module.exports = {
  entry: "./app/index.js",
  module: {
    rules: [
      {
        test: /\.(svg)$/i,
        use: "svg-loader-js",
      },
      {
        test: /\.css$/i,
        use: ["style-loader", "css-loader"],
      },
      {
        test: /\.(js)$/,
        use: "babel-loader",
      },
    ],
  },
  output: {
    path: path.resolve(__dirname, "dist"),
    filename: "bundle.js",
  },
  plugins: [new HtmlWebpackPlugin()],
  mode: process.env.NODE_ENV === "production" ? "production" : "development",
};
```
