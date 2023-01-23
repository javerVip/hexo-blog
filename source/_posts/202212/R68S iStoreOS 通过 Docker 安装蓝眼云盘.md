title: R68S iStoreOS 通过 Docker 安装蓝眼云盘
date: '2022-12-16 19:13:52'
updated: '2022-12-16 20:01:45'
tags: [云盘, docker, R68S, iStoreOS]
permalink: /articles/2022/12/16/1671189232486.html
---
## MySQL 镜像

### 通过命令拉取 MySQL 指定平台镜像

```docker
docker pull --platform linux/amd64 mysql:5.7.40
# 或，取决于你想使用的平台
docker pull --platform linux/x86_64 mysql:5.7.40
```

> 上面的方式拉取可以成功，但是运行大概率失败，推荐安装 MariaDB

### 通过可视化界面拉取 MariaDB 镜像

![image.png](https://b3logfile.com/file/2022/12/image-g6t2DU1.png)

等待ing...

![image.png](https://b3logfile.com/file/2022/12/image-ZNikor7.png)

拉取完成。

![image.png](https://b3logfile.com/file/2022/12/image-Hxv4LXm.png)

### 运行 MySQL/MariaDB 镜像

```
# mysql
docker run --name dockermysql -p 13306:3306 -e MYSQL_ROOT_PASSWORD=123456 -e MYSQL_DATABASE=tank -e TZ=Asia/Shanghai -d mysql:5.7.40 --character-set-server=utf8mb4 --collation-server=utf8mb4_unicode_ci --default-time_zone=+8:00

# mariadb
docker run --name dockermysql -p 13306:3306 -e MYSQL_ROOT_PASSWORD=123456 -e MYSQL_DATABASE=tank -e TZ=Asia/Shanghai -d arm64v8/mariadb:latest --character-set-server=utf8mb4 --collation-server=utf8mb4_unicode_ci --default-time_zone=+8:00
```

运行成功。

```
root@iStoreOS:~# docker run --name dockermysql -p 13306:3306 -e MYSQL_ROOT_PASSWORD=123456 -e MYSQL_DATABASE=tank -e TZ=Asia/Shanghai -d arm64v8/mariadb:latest --character-set-server=utf8mb4 --collation-server=utf8mb4_unicode_ci --default-time_zone=+8:0
0
82d53ed40aece69d76dbf2b00459caa39a3de83ade4bbde08e0dc7f40bc17103
root@iStoreOS:~# docker ps -a
CONTAINER ID   IMAGE                    COMMAND                  CREATED         STATUS         PORTS                                         NAMES
82d53ed40aec   arm64v8/mariadb:latest   "docker-entrypoint.s…"   5 seconds ago   Up 2 seconds   0.0.0.0:13306->3306/tcp, :::13306->3306/tcp   dockermysql
root@iStoreOS:~#
```

## 蓝眼云盘镜像

截止发文，蓝眼云盘最新版本号为：**3.1.6**

![image.png](https://b3logfile.com/file/2022/12/image-UskAVNM.png)

### 通过可视化界面拉取蓝眼云盘镜像

![image.png](https://b3logfile.com/file/2022/12/image-J8mxO64.png)

> 此处不能通过 eyeblue/tank:latest 方式获取最新版，需要指定版本号！切记。

等待ing...

![image.png](https://b3logfile.com/file/2022/12/image-ythEsCq.png)

拉取完成。

![image.png](https://b3logfile.com/file/2022/12/image-2NiGTNy.png)

### 运行蓝眼镜像

```
docker run --name tank -p 6010:6010 --link dockermysql:mysql -v ~/data/dockermatter:/data/build/matter -d eyeblue/tank:3.1.6
```

运行结果：

```
root@iStoreOS:~# docker run --name tank -p 6010:6010 --link dockermysql:mysql -v ~/data/dockermatter:/data/build/matter -d eyeblue/tank:3.1.6
WARNING: The requested image's platform (linux/amd64) does not match the detected host platform (linux/arm64/v8) and no specific platform was requested
6ea5c496c9bcfe33b2c03ff05e368c605e0206906bd253e71d855e158f5e08fc
root@iStoreOS:~# docker ps -a
CONTAINER ID   IMAGE                    COMMAND                  CREATED          STATUS                     PORTS                                         NAMES
6ea5c496c9bc   eyeblue/tank:3.1.6       "/data/build/tank"       12 seconds ago   Exited (1) 9 seconds ago                                                 tank
82d53ed40aec   arm64v8/mariadb:latest   "docker-entrypoint.s…"   11 minutes ago   Up 11 minutes              0.0.0.0:13306->3306/tcp, :::13306->3306/tcp   dockermysql
root@iStoreOS:~#
```

很明显，平台架构问题，不支持这么玩儿。那就不使用 Docker 部署蓝眼云盘，自己编译 linux/arm64 的包启动即可。

linux/arm64 编译好的安装包下载：[tank3.1.6.zip](https://b3logfile.com/file/2022/12/tank-3.1.6-CHIhm72.zip)

## 上传文件

![image.png](https://b3logfile.com/file/2022/12/image-2oy2Der.png)

点击上传按钮，上传后的路径是：`/tmp/upload/tank3.1.6.zip`

## 移动并解压文件

```shell
cd ~
mkdir app
mv /tmp/upload/tank3.1.6.zip ./app/
unzip tank3.1.6.zip
```

## 通过 screen 启动蓝眼云盘

> 前提：记得在软件包安装 `screen`

```
screen -ls
screen -R tank
cd ~/app/tank-3.1.6
./tank
# 按住 Ctrl + a 后再按 d，即可保持这个screen到后台并回到主终端
```

## 放行蓝眼云盘 访问端口

如图：

![image.png](https://b3logfile.com/file/2022/12/image-4AlWunV.png)

## 访问及配置

访问 `路由LAN-IP:6010`：

![image.png](https://b3logfile.com/file/2022/12/image-ilSsyFt.png)

如图配置即可使用。

![image.png](https://b3logfile.com/file/2022/12/image-3ZwGHYt.png)

![image.png](https://b3logfile.com/file/2022/12/image-m31AhL9.png)

![image.png](https://b3logfile.com/file/2022/12/image-a7YwPZY.png)

---

至此，安装完成。

![image.png](https://b3logfile.com/file/2022/12/image-uZOu2MR.png)

## 参考资料

- [安装 | 蓝眼云盘](https://tank-doc.eyeblue.cn/basic/install.html#docker)
- [Golang 显示支持的os和arch列表](https://javer.vip/articles/2022/12/16/1671190815863.html)

