title: 二 安装 tailwindcss 到项目中
date: '2022-12-27 16:25:21'
updated: '2022-12-27 16:25:24'
tags: [tailwind, CSS, 项目, 安装]
---
## 安装依赖

在安装 tailwindcss 前需要安装下面的依赖：

```
npm install -D tailwindcss@3.0.23 postcss@8.4.8 autoprefixer@10.4.2 sass@1.45.0
```

## 生成配置

执行下方命令以创建 tailwind.config.js 文件：

```
npx tailwindcss init -p
```

得到输出：

```
Created Tailwind CSS config file: tailwind.config.js    
Created PostCSS config file: postcss.config.js
```

`tailwind.config.js` 文件默认内容为：

```
module.exports = {
    content: [],
    theme: {
        extend: {},
    },
    plugins: [],
}
```

### 添加应用范围

修改 `tailwind.config.js` 文件为：

```
module.exports = {
    content: ['./index.html', './src/**/*.{vue,js}'],
    theme: {
        extend: {},
    },
    plugins: [],
}
```

### 添加指令

新增 src/styles/index.scss 文件，并写入内容：

```
@tailwind base;
@tailwind components;
@tailwind utilities;
```

### 引入 tailwindcss

修改 `src/main.js`，引入 tailwindcss 内容（见第四行）：

```
import { createApp } from 'vue'
import './style.css'
import App from './App.vue'
import './styles/index.scss'

createApp(App).mount('#app')
```

### 验证

在 src/App.vue 中为 img 标签增加一个 `class="bg-red-900"`

```
<img src="/vite.svg" class="logo bg-red-900" alt="Vite logo" />
```

查看页面发现样式发生了改变：

![image.png](https://b3logfile.com/file/2022/12/image-z864zX6.png)

---



安装完成！！！



