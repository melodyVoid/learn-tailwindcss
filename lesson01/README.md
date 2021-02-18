# tailwindcss 安装

本期视频主要分享两种安装 tailwindcss 的方式

1. 以 PostCSS 插件的形式安装 Tailwind CSS
2. 不依赖 PostCSS 使用 Tailwind

## 以 PostCSS 插件的形式安装 Tailwind CSS

### 初始化工程

```bash
mkdir tailwind-with-postcss
cd tailwind-with-postcss
npm init -y
```

### 通过 npm 或 yarn 来安装 tailwindcss

```bash
npm install tailwindcss postcss-cli autoprefixer -D
# or
yarn add tailwindcss postcss-cli autoprefixer -D
```

### 作为 PostCSS 插件来添加 Tailwind

新建 tailwindcss 配置文件 `tailwind.config.js` 和 postcss 配置文件 `postcss.config.js`

可以通过命令行生成

```bash
npx tailwind init -p
```
`-p` 的意思是同时生成 `postcss.config.js`

然后我们会看到

```bash
  tailwindcss 2.0.3
  
  ✅ Created Tailwind config file: tailwind.config.js
  ✅ Created PostCSS config file: postcss.config.js
```

postcss.config.js

```js
module.exports = {
  plugins: {
    tailwindcss: {},
    autoprefixer: {},
  },
}
```

tailwind.config.js

```js
module.exports = {
  purge: [],
  darkMode: false, // or 'media' or 'class'
  theme: {
    extend: {},
  },
  variants: {
    extend: {},
  },
  plugins: [],
}
```

### 包含 Tailwind 到您的 CSS 中

创建文件 `src/style.css`

```css
/* ./src/styles.css */
@tailwind base;
@tailwind components;
@tailwind utilities;
```

### 生成您的 CSS

在 `package.json` 中添加构建指令

```json
"scripts": {
  "build": "postcss src/style.css -o dist/tailwind.css"
},
```

然后运行

```bash
yarn build
```

我们会看到生成了 `dist/tailwind.css`

### 使用 tailwindcss

新建 `dist/index.html` 并引入构建好的 `tailwind.css`

```html
<!DOCTYPE html>
<html lang="en">
<head>
  <meta charset="UTF-8">
  <meta http-equiv="X-UA-Compatible" content="IE=edge">
  <meta name="viewport" content="width=device-width, initial-scale=1.0">
  <!-- 引入 tailwind.css -->
  <link rel="stylesheet" href="tailwind.css">
  <title>Document</title>
</head>
<body>
  
</body>
</html>
```

添加一些样式

```html
<div class="container mx-auto bg-indigo-400">
  <div class="text-4xl text-center m-4 p-4">Hello World</div>
</div> 
```

然后我们通过浏览器打开就会看到效果，说明 tailwindcss 安装成功了。

![](./preview.png)

## 不依赖 PostCSS 使用 Tailwind

### 初始化工程

```bash
mkdir tailwind-demo
cd tailwind-demo
npm init -y
```

### 通过 npm 或 yarn 来安装 tailwindcss

```bash
npm install tailwindcss autoprefixer -D
# or
yarn add tailwindcss autoprefixer -D
```

### 生成 tailwindcss 配置文件

```bash
npx tailwind init
```

### 包含 Tailwind 到您的 CSS 中

创建文件 `src/style.css`

```css
/* ./src/styles.css */
@tailwind base;
@tailwind components;
@tailwind utilities;
```

### 生成您的 CSS

在 `package.json` 中添加构建指令

```json
"scripts": {
  "build": "tailwind build src/style.css -o dist/tailwind.css"
},
```

然后运行

```bash
yarn build
```

我们会看到生成了 `dist/tailwind.css`

```bash
  tailwindcss 2.0.3
  
  🚀 Building: src/style.css

  ✅ Finished in 2.29 s
  📦 Size: 3.74MB
  💾 Saved to dist/tailwind.css
```

### 使用 tailwindcss

新建 `dist/index.html` 并引入构建好的 `tailwind.css`

```html
<!DOCTYPE html>
<html lang="en">
<head>
  <meta charset="UTF-8">
  <meta http-equiv="X-UA-Compatible" content="IE=edge">
  <meta name="viewport" content="width=device-width, initial-scale=1.0">
  <!-- 引入 tailwind.css -->
  <link rel="stylesheet" href="tailwind.css">
  <title>Document</title>
</head>
<body>
  
</body>
</html>
```

添加一些样式

```html
<div class="container mx-auto bg-indigo-400">
  <div class="text-4xl text-center m-4 p-4">Hello World</div>
</div> 
```

然后我们通过浏览器打开就会看到效果，说明 tailwindcss 安装成功了。

![](./preview.png)