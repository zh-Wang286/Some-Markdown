> 整理自菜鸟教程 https://www.runoob.com/

[toc]

## Docker Hello World

使用 **docker run** 命令来在容器内运行一个应用程序，运行Hello World

```bash
sudo docker run ubuntu /bin/echo "Hello World"
```

![image-20211016195348503](image-20211016195348503.png)

参数解析

| docker                  | run                                | ubuntu                                                       | /bin/echo "Hello World"  |
| ----------------------- | ---------------------------------- | ------------------------------------------------------------ | ------------------------ |
| Docker 的二进制执行文件 | 与前面的 docker 组合来运行一个容器 | 指定要运行的镜像，Docker 首先从本地主机上查找镜像是否存在，如果不存在，Docker 就会从镜像仓库 Docker Hub 下载公共镜像。 | 在启动的容器里执行的命令 |

## 运行交互式容器

```bash
sudo docker run -i -t ubuntu /bin/bash
```

![image-20211016200501051](image-20211016200501051.png)

`-i`允许对容器内的标准输入（STDIN）进行交互

`-t`在新容器内指定一个伪终端或终端

尝试在容器中运行命令`cat /proc/version`和`ls`分别查看当前系统的版本信息和当前目录下的文件列表

![image-20211016200843966](image-20211016200843966.png)

![image-20211016200902301](image-20211016200902301.png)

## 运行后台容器

创建一个以进程方式运行的容器

```bash
sudo docker run -d ubuntu /bin/sh -c "while true; do echo hello world; sleep 1; done"
```

```
# 返回 c01dfdbe8c20c95c3bdeacf035c2541cf4d4210c8e9fef2469a94cc1cbcdc915
```

`-d`参数默认不会进入容器，想要进入容器需要使用指令` docker exec`

![image-20211016201442413](image-20211016201442413.png)

查看容器列表

```bash
sudo docker ps
```

![image-20211016201309076](image-20211016201309076.png)

| CONTAINER ID | 容器 ID                        |
| ------------ | ------------------------------ |
| IMAGE        | 使用的镜像                     |
| COMMAND      | 启动容器时运行的命令           |
| CREATED      | 容器创建的时间                 |
| STATUS       | 容器状态                       |
| PORTS        | 容器的端口信息和使用的类型连接 |
| NAMES        | 自动分配的容器名               |

其中，STATUS容器状态有7种

| STATUS       | 描述   |
| ------------ | ------ |
| created      | 已创建 |
| restarting   | 重启中 |
| running / up | 运行中 |
| removing     | 迁移中 |
| paused       | 暂停   |
| existed      | 停止   |
| dead         | 死亡   |

在宿主机内，查看容器内的标准输出

```bash
sudo docker logs [CONTAINER ID]/[NAMES]
```

![image-20211016202117303](image-20211016202117303.png)

## 停止容器

```bash
sudo docker stop [CONTAINER ID]/[NAMES]
```

