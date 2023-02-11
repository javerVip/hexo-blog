---
title: Python3+pip环境配置
date: 2023-02-11 22:09:47
tags: [python, pip, 环境, 配置]
---

## 安装 AnaConda

前往 [Anaconda | The World's Most Popular Data Science Platform](https://www.anaconda.com/) Download 对应程序包。

![2023-02-11_221034.png](/posts-img/2023-02-11_221034.png)

一直下一步知道安装完成。

配置如下环境变量：

```
<path>\Anaconda3
<path>\Anaconda3\scripts
<path>\Anaconda3\Library\bin
```

### 验证 AnaConda 状态

打开 cmd 控制台，输入 `conda` 能否得到结果：

```
C:\Users\javer>conda
usage: conda-script.py [-h] [-V] command ...

conda is a tool for managing and deploying applications, environments and packages.

Options:

positional arguments:
  command
    clean        Remove unused packages and caches.
    compare      Compare packages between conda environments.
    config       Modify configuration values in .condarc. This is modeled after the git config command. Writes to the
                 user .condarc file (C:\Users\javer\.condarc) by default. Use the --show-sources flag to display all
                 identified configuration locations on your computer.
    create       Create a new conda environment from a list of specified packages.
    info         Display information about current conda install.
    init         Initialize conda for shell interaction.
    install      Installs a list of packages into a specified conda environment.
    list         List installed packages in a conda environment.
    package      Low-level conda package utility. (EXPERIMENTAL)
    remove       Remove a list of packages from a specified conda environment.
    rename       Renames an existing environment.
    run          Run an executable in a conda environment.
    search       Search for packages and display associated information.The input is a MatchSpec, a query language for
                 conda packages. See examples below.
    uninstall    Alias for conda remove.
    update       Updates conda packages to the latest compatible version.
    upgrade      Alias for conda update.
    notices      Retrieves latest channel notifications.

optional arguments:
  -h, --help     Show this help message and exit.
  -V, --version  Show the conda version number and exit.

conda commands available from other packages:
  build
  content-trust
  convert
  debug
  develop
  env
  index
  inspect
  metapackage
  pack
  render
  repo
  server
  skeleton
  token
  verify
```

输入 `conda list` 能否得到结果：

![2023-02-11_221515.png](/posts-img/2023-02-11_221515.png)

输入 `python -V` 能否得到结果：

```
C:\Users\javer>python -V
Python 3.9.13
```

再次输入 `conda install requests` 并输入 `y` 确认以安装依赖包：

![2023-02-11_221652.png](/posts-img/2023-02-11_221652.png)

至此配置完成

## 安装 PyCharm

由于电脑预先安装好了 [JetBrains Toolbox App: Manage Your Tools with Ease](https://www.jetbrains.com/toolbox-app/)，所以直接点开工具箱安装即可。

![2023-02-11_222012.png](/posts-img/2023-02-11_222012.png)

等待下载ing...

![2023-02-11_222043.png](/posts-img/2023-02-11_222043.png)

等待安装ing...

![2023-02-11_222129.png](/posts-img/2023-02-11_222129.png)

安装完成

![2023-02-11_222156.png](/posts-img/2023-02-11_222156.png)

安装 `Translation` 翻译插件

![2023-02-11_222302.png](/posts-img/2023-02-11_222302.png)

设置文件编码为 UTF-8

![2023-02-11_222416.png](/posts-img/2023-02-11_222416.png)

允许使用 Ctrl + 鼠标滚轮更改字号

![2023-02-11_222507.png](/posts-img/2023-02-11_222507.png)
