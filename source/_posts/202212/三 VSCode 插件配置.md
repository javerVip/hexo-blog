title: 三 VSCode 插件配置
date: '2022-12-27 16:25:22'
updated: '2022-12-27 17:09:24'
tags: [VSCode, 插件, 安装]
---
## Prettier - Code formatter

![image.png](https://b3logfile.com/file/2022/12/image-vSzuwA6.png)

注意作者为 `Prettier`，安装插件后在项目根目录下创建 `.prettierrc` 文件，内容为：

```
{
  // 代码结尾不加分号
  "semi": false,
  // 优先单引号
  "singleQuote": true,
  // 不添加尾随逗号
  "trailingComma": "none"
}
```

> 实际使用记得删除注释！！！

在你的 `.vue` 文件、`.js` 文件中，鼠标右键，选择 **使用…格式化文档**

![image.png](https://b3logfile.com/file/2022/12/image-z3sbKJf.png)

![image.png](https://b3logfile.com/file/2022/12/image-JlEVUib.png)

将 Prettier 配置为默认格式化程序。

## Tailwind CSS IntelliSense

我们知道 `tailwind` 的核心语法是  **一个类名表示一个 `css 属性`** ，但是我们知道 `css` 属性是非常多的，这也就会导致 `tailwind` 的 [类名](https://tailwindcss.com/docs/aspect-ratio) 非常多，那么这么多的类名如果我们想要在短时间内把它们全部记住是非常不现实的。

所以说 `tailwind` 为我们提供了一个 `VSCode` 的插件 [Tailwind CSS IntelliSense](https://tailwindcss.com/docs/editor-setup#intelli-sense-for-vs-code)

想要安装 `Tailwind CSS IntelliSense` 非常简单，我们只需要在 `VSCode` 插件中搜索 `Tailwind CSS IntelliSense` ，点击安装即可（PS：图片为安装之后的截图）

![image.png](https://b3logfile.com/file/2022/12/image-XHV996L.png)

安装成功之后，此时我们只需要在：**元素的 `class` 中，先按下《空格》，然后输入任意的 `tailwind` 类名，则可得到对应提示**

![image.png](https://b3logfile.com/file/2022/12/image-XK3duAK.png)

## Vue Language Features (Volar)

`Volar` 全名是 `Vue Language Features (Volar)` ，是一个专门的 `vue3` 辅助插件。

这个插件我们不需要做什么特殊的处理，只需要安装即可。（PS：图片为安装之后的截图）

![image.png](https://b3logfile.com/file/2022/12/image-9UzQOxB.png)

这一小节我们主要是安装了一些 `VSCode` 的插件，帮助我们进行辅助开发。

