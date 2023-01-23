title: Docker 安装 Oracle 12c
date: '2022-12-13 20:09:52'
updated: '2022-12-13 20:09:52'
tags: [docker, oracle]
---
## 拉取镜像

```
docker pull sath89/oracle-12c
```

## 运行容器

```
docker run -d -p 8080:8080 -p 1521:1521 sath89/oracle-12c
```

这个期间等待的比较久，以 I5-12600KF，32G(DDR4-3200)，1TSSD为例，实测完整启动时间为 8分50秒：

```
2022-12-13 19:39:30 Database not initialized. Initializing database.
2022-12-13 19:39:30 Starting tnslsnr
2022-12-13 19:39:54 Copying database files
2022-12-13 19:39:54 1% complete
2022-12-13 19:40:19 3% complete
2022-12-13 19:40:19 11% complete
2022-12-13 19:40:59 18% complete
2022-12-13 19:41:34 37% complete
2022-12-13 19:41:34 Creating and starting Oracle instance
2022-12-13 19:42:00 40% complete
2022-12-13 19:42:10 45% complete
2022-12-13 19:43:48 50% complete
2022-12-13 19:43:48 55% complete
2022-12-13 19:43:49 56% complete
2022-12-13 19:43:49 60% complete
2022-12-13 19:43:49 62% complete
2022-12-13 19:43:49 Completing Database Creation
2022-12-13 19:43:49 66% complete
2022-12-13 19:43:49 70% complete
2022-12-13 19:43:49 73% complete
2022-12-13 19:43:49 85% complete
2022-12-13 19:45:46 96% complete
2022-12-13 19:45:46 100% complete
2022-12-13 19:45:46 Look at the log file "/u01/app/oracle/cfgtoollogs/dbca/xe/xe.log" for further details.
2022-12-13 19:45:47 Configuring Apex console
2022-12-13 19:47:20 Database initialized. Please visit http://#containeer:8080/em http://#containeer:8080/apex for extra configuration if needed
2022-12-13 19:47:20 Starting web management console
2022-12-13 19:47:20 
2022-12-13 19:47:20 PL/SQL procedure successfully completed.
2022-12-13 19:47:20 
2022-12-13 19:47:20 Starting import from '/docker-entrypoint-initdb.d':
2022-12-13 19:47:20 Import finished
2022-12-13 19:47:20 
2022-12-13 19:47:20 Database ready to use. Enjoy! ;)
2022-12-13 19:47:20 ls: cannot access /docker-entrypoint-initdb.d/*: No such file or directory
```

## 访问验证

### http 访问

docker启动命令携带了8080的web映射，可以访问 [http://localhost:8080/apex](http://localhost:8080/apex) 查看是否启动成功，

- 默认账号：`ADMIN`
- 默认密码：`0Racle$`

**登录会要求输入符合规则的新密码**。

### Navicat 访问

配置如下：

- 连接类型：`Basic`
- 主机：`localhost`
- 端口：`1521`
- 服务名：`xe`
- 服务类型：`SID`
- 用户名：`oracle`

默认的连接配置内容为：

```
hostname: localhost
port: 1521
sid: xe
service name: xe.oracle.docker
username: system
password: oracle
```

至此，`Docker 安装 Oracle 12c` 结束。

## 参考资料

- [konnecteam/docker-oracle-12c - Docker Image | Docker Hub](https://hub.docker.com/r/konnecteam/docker-oracle-12c/)

