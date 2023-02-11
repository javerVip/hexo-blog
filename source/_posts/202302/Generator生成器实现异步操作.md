title: Generator生成器实现异步操作
date: '2023-02-11 13:02:00'
updated: '2023-02-11 13:02:00'
tags: [生成器, Generator, 异步, 操作]
---

生成器在使用时要注意：

1. 生成器可以传参
2. 生成器需要配合 `function*` 和 `yield` 关键字使用 

下面演示了异步操作时，使用生成器保证调用链的顺序。完整代码如下：

```html
<!DOCTYPE html>
<html lang="zh-CN">

<head>
    <meta charset="UTF-8">
    <meta http-equiv="X-UA-Compatible" content="IE=edge">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Document</title>
    <script src="https://cdn.bootcdn.net/ajax/libs/jquery/3.6.3/jquery.min.js"></script>
</head>

<body>
    <script>
        function showUI() {
            console.log("load page...");
        }

        function loadData() {
            console.log("load data...");
            setTimeout(() => {
                console.log("load data success");
                mainLoad.next();
            }, 1000);
        }

        function hideUI() {
            console.log("hide page");
        }
        
        function* main() {
            showUI();
            yield loadData();
            hideUI();
        }

        let mainLoad = main();
        mainLoad.next();
    </script>
</body>

</html>
```

运行结果为：

```
load page...
load data...
load data success
hide page
```
