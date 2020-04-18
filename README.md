# Code Style Implementation Guide
Before you start any project follow this guideline to setup ECMAScript Linting for your project

1. Initialize Package
```sh
npm init -y
```
2. Install linting Packages
```sh
npm i -D eslint eslint-config-airbnb eslint-config-airbnb-base eslint-plugin-import
```
3. To install eslint in your editor VS Code visit the plugin page:
https://marketplace.visualstudio.com/items?itemName=dbaeumer.vscode-eslint

4. Create a `.editorconfig` file
```
# top-most EditorConfig file
root = true

[*]
charset = utf-8
indent_style = space
indent_size = 2
trim_trailing_whitespace = true
insert_final_newline = true
```
5. Create a `.eslintrc.js` file
```
module.exports = {
  "extends": "airbnb-base",
  "rules": {
    "no-undef": "off",
    "no-alert": "off",
    "quote-props": "off",
    "brace-style": 2,
    "object-shorthand": "off",
    "no-console": "off"
  }
};
```