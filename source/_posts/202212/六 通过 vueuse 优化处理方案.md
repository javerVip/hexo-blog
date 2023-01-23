title: 六 通过 vueuse 优化处理方案
date: '2022-12-27 16:25:25'
updated: '2022-12-27 17:27:27'
tags: [vueuse, 响应式, 数据]
---
对于 `isMobileTerminal` 方法，此时还存在一个问题，那就是当切换浏览器设备时，它的结果并 **不是响应式** 的，这种让计算属性显得毫无意义了。

那么为什么会这样呢？
对于计算属性而言，它会在  **依赖的响应式数据发生变化时，重新计算** 。但是现在依赖的 `document.documentElement.clientWidth` 并非响应式数据，所以 **计算属性无法发生重新计算。**

那么要怎么做呢？

在这里需要给大家介绍一个新的库 [vueuse](https://vueuse.org/)， `vueuse` 是一个 **vue 的工具类库** 。它内部提供了很多的方法，可以进行很多的便捷操作。

比如说 [useWindowSize](https://vueuse.org/core/useWindowSize/) 这个方法，这个方法会给返回一个 **响应式** 的页面宽高，那么就可以利用这个响应式数据实现的 `isMobileTerminal`

1. 安装 `vueuse`
   
   ```
   npm i @vueuse/core@8.1.2
   ```
2. 在 `src/utils/flexible.js` 中使用 `useWindowSize` 方法
   
   ```
   import { useWindowSize } from '@vueuse/core'
   
   const { width } = useWindowSize()
   ```
3. 利用 `width` 计算 `isMobileTerminal`
   
   ```
   export const isMobileTerminal = computed(() => {
   	return width.value < PC_DEVICE_WIDTH
   })
   ```

演示效果：

![动画.gif](https://b3logfile.com/file/2022/12/动画-1iQ8Sg2.gif)



