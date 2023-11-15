# Golang with Tailwind

setup tailwind css with golang using postcss
Based on: [https://github.com/tailwindlabs/tailwindcss-setup-examples/blob/3f4c23077c4362de8cd0db0645161b7688e4135d/examples/golang-postcss-only/README.md?plain=1]()

## Setup

Use npm tailwind,postcss and postcss-cli 

```bash
npm install tailwindcss postcss postcss-cli --save-dev
```
install watch

```bash
npm install watch --save
```
now run to create package.json
```bash
npm init -y
```
create postcss.config.js with this config
```js
const tailwindcss = require("tailwindcss")
const autoprefixer = require("autoprefixer")

module.exports = {
  plugins: [
    tailwindcss,
    autoprefixer,
  ]
}
```
before editing the package.json file the project structure should be something like that
```bash
├── static
  ├── css
    ├── master.css
  ├── dist
├── templates
  ├── index.html
├── main.go
├── postcss.config.js
├── package.json
```
so package.json will be like that
```js
{
  "name": "app name",
  "version": "1.0.0",
  "description": "tailwind setup with golang app using postcss",
  "main": "index.js",
  "scripts": {
    "build:tailwind": "postcss ./static/css/master.css -o ./static/dist/tailwind.css",
    "watch": "watch \"npm run build:tailwind\" ./templates"
  },
  "devDependencies": {
    "postcss": "^7.0.17",
    "postcss-cli": "^6.1.2",
    "tailwindcss": "^1.0.3"
  },
  "dependencies": {
    "watch": "^1.0.2"
  },
  "keywords": [],
  "author": "",
  "license": "ISC"
}

```
index.html is so simple
```html
<!DOCTYPE html>
<html lang="en">
<head>
  <title>Tailwind</title>
  <link href="/static/dist/tailwind.css" rel="stylesheet">
</head>
<body>
</body>
</html>
```
master.css
```css
@tailwind base;
@tailwind components;
@tailwind utilities;
```

now you can run npm to get the job done
```bash
npm run build:tailwind
#or
npm run watch
#to watch any changes
```

## Use go generate command to generate styles as defined in gen.go (Go generation), another option

It's Done!!
## License
[MIT](https://choosealicense.com/licenses/mit/)