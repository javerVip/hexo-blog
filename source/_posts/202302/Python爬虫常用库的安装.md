---
title: Python爬虫常用库的安装
date: 2023-02-15 17:46:09
tags: [python, 爬虫, 常用, 安装]
---

## urllib

在 python 命令行模式输入下面的代码

```python
import urllib
import urllib.request
urllib.request.urlopen('http://3.cn')
```

回车不报错，并且有响应：

```
<http.client.HTTPResponse object at 0x0000022F88466C70>
```

## re

在 python 命令行模式输入下面的代码

```python
import re
```

回车不报错即可。

## requests

输入 `pip install requests` 安装，在 python 命令行模式输入下面的代码

```python
import requests
requests.get('http://3.cn')
```

回车不报错，并且有响应：

```
<Response [200]>
```

## selenium

输入 `pip install selenium` 安装，在 python 命令行模式输入下面的代码

```python
import selenium
from selenium import webdriver
driver = webdriver.Chrome()
```

响应：

```
Traceback (most recent call last):
  File "<stdin>", line 1, in <module>
  File "C:\Users\javer\AppData\Roaming\Python\Python39\site-packages\selenium\webdriver\chrome\webdriver.py", line 80, in __init__
    super().__init__(
  File "C:\Users\javer\AppData\Roaming\Python\Python39\site-packages\selenium\webdriver\chromium\webdriver.py", line 104, in __init__
    super().__init__(
  File "C:\Users\javer\AppData\Roaming\Python\Python39\site-packages\selenium\webdriver\remote\webdriver.py", line 286, in __init__
    self.start_session(capabilities, browser_profile)
  File "C:\Users\javer\AppData\Roaming\Python\Python39\site-packages\selenium\webdriver\remote\webdriver.py", line 378, in start_session
    response = self.execute(Command.NEW_SESSION, parameters)
  File "C:\Users\javer\AppData\Roaming\Python\Python39\site-packages\selenium\webdriver\remote\webdriver.py", line 440, in execute
    self.error_handler.check_response(response)
  File "C:\Users\javer\AppData\Roaming\Python\Python39\site-packages\selenium\webdriver\remote\errorhandler.py", line 245, in check_response
    raise exception_class(message, screen, stacktrace)
selenium.common.exceptions.WebDriverException: Message: unknown error: cannot find Chrome binary
Stacktrace:
Backtrace:
        (No symbol) [0x011337D3]
        (No symbol) [0x010C8B81]
        (No symbol) [0x00FCB36D]
        (No symbol) [0x00FE9190]
        (No symbol) [0x00FE6FC9]
        (No symbol) [0x01021ED5]
        (No symbol) [0x01021B2C]
        (No symbol) [0x0101B216]
        (No symbol) [0x00FF0D97]
        (No symbol) [0x00FF253D]
        GetHandleVerifier [0x013AABF2+2510930]
        GetHandleVerifier [0x013D8EC1+2700065]
        GetHandleVerifier [0x013DC86C+2714828]
        GetHandleVerifier [0x011E3480+645344]
        (No symbol) [0x010D0FD2]
        (No symbol) [0x010D6C68]
        (No symbol) [0x010D6D4B]
        (No symbol) [0x010E0D6B]
        BaseThreadInitThunk [0x75BB00F9+25]
        RtlGetAppContainerNamedObjectPath [0x77267BBE+286]
        RtlGetAppContainerNamedObjectPath [0x77267B8E+238]
```

## chromedriver

前往 [ChromeDriver - WebDriver for Chrome - Downloads](https://chromedriver.chromium.org/downloads) 下载 win32 版本。

将 `chromedriver.exe` 复制到 `C:\ProgramData\Anaconda3` 目录下。

尝试在 cmd 中输入 `chromedriver` 得到：

```
Starting ChromeDriver 111.0.5563.19 (378a38865270d286695aeb86f190564911ef7bc2-refs/branch-heads/5563@{#251}) on port 9515
Only local connections are allowed.
Please see https://chromedriver.chromium.org/security-considerations for suggestions on keeping ChromeDriver safe.
ChromeDriver was started successfully.
```

在 python 命令行模式输入下面的代码

```python
import selenium
from selenium import webdriver
driver = webdriver.Chrome()
driver.get('http://3.cn')
```

可以看到 chrome 弹出并打开了 http://3.cn 这个网址。

![2023-02-11_231230.png](/posts-img/2023-02-11_231230.png)

> 1. `driver.page_source` 可以打印出网页源码。
> 
> 2. chromedriver 应当和 chrome 版本号差别不大于3个小版本。

## phantomjs

在后台运行，可以不弹出浏览器页面。

前往 [Download PhantomJS](https://phantomjs.org/download.html) 下载。

运行下方代码：

```
phantomjs
new Date()
// Ctrl+c 退出
```

输入下方命令验证：

```python
import selenium
from selenium import webdriver
driver = webdriver.PhantomJS()
driver.get('http://3.cn')
driver.page_source
```

整个过程都没有浏览器窗口。

> 如果出现 `AttributeError: module 'selenium.webdriver' has no attribute 'PhantomJS'` 报错，
> 
> ```
> pip uninstall selenium
> pip install selenium==2.48.0
> ```
>
> 即可解决。

## lxml

网页解析工具。

```
pip install lxml
```

## beautifulsoup

网页解析工具，依赖于 lxml。

```
pip install beautifulsoup4
```

输入下方命令验证：

```python
from bs4 import BeautifulSoup
soup = BeautifulSoup('<html></html>','lxml')
```

不报错即可。

## pyquery

网页解析工具。

```
pip install pyquery
```

输入下方命令验证：

```python
from pyquery import PyQuery as pq
doc = pq('<html></html>')
doc = pq('<html>Hello</html>')
result = doc('html').text()
result
```

## pymysql

```
pip install pymysql
```

输入下方命令验证：

```python
import pymysql
conn = pymysql.connect(host='localhost', user='root', password='123456', port=3306, db='mysql')
cursor = conn.cursor()
cursor.execute('select * from sys')
cursor.fetchone()
```
