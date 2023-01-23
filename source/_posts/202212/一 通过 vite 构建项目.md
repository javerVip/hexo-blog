title: 一 通过 vite 构建项目
date: '2022-12-27 16:25:20'
updated: '2022-12-27 16:33:54'
tags: [Vue3, Vite, 构建, 项目]
permalink: /articles/2022/12/27/1672129524292.html
---
## 安装 vite

```
npm install -g vite@2.8.5
```

**查看 vite 版本**：

```
C:\Users\Administrator>vite -v
vite/2.8.5 win32-x64 node-v18.12.0
```

> Vite 需要 nodejs 版本 ≥ 12.0.0

## 构建项目

使用 `npm init vite@latest` 创建项目，步骤如下：

```
npm init vite@latest
Need to install the following packages:
  create-vite@4.0.0
Ok to proceed? (y) y
√ Project name: ... 项目名称
√ Select a framework: » Vue
√ Select a variant: » JavaScript

Scaffolding project in C:\Users\Administrator\项目名称...

Done. Now run:

  cd 项目名称
  npm install
  npm run dev
```

执行 `npm run dev` 得到输出：

```
VITE v4.0.3  ready in 314 ms
  ➜  Local:   http://localhost:5173/
  ➜  Network: use --host to expose
  ➜  press h to show help
```

浏览器访问 `http://localhost:5173/` 可以看到：

![image.png](https://b3logfile.com/file/2022/12/image-uHCXoWD.png)

## 允许其他 IP 访问本地服务

将`package.json` 第 7 行的内容由 `vite` 修改为 `vite --host`，修改后的文件如下：

```
{
  "name": "imooc-front",
  "private": true,
  "version": "0.0.0",
  "type": "module",
  "scripts": {
    "dev": "vite --host",
    "build": "vite build",
    "preview": "vite preview"
  },
  "dependencies": {
    "vue": "^3.2.45"
  },
  "devDependencies": {
    "@vitejs/plugin-vue": "^4.0.0",
    "vite": "^4.0.0"
  }
}
```

再次 `npm run dev` 启动：

```
VITE v4.0.3  ready in 304 ms

  ➜  Local:   http://localhost:5173/
  ➜  Network: http://10.0.0.149:5173/
  ➜  press h to show help
```

通过 IP 访问：

![image.png](https://b3logfile.com/file/2022/12/image-ij9KapA.png)



