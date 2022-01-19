> 整理自菜鸟教程 https://www.runoob.com/

[toc]



## 使用官方脚本自动安装

安装命令如下：

```bash
curl -fsSL https://get.docker.com | bash -s docker --mirror Aliyun
```

也可以使用国内 daocloud 一键安装命令：

```bash
curl -sSL https://get.daocloud.io/docker | sh
```

## 手动安装

### 卸载旧版本

Docker 的旧版本被称为 docker，docker.io 或 docker-engine 。如果已安装，请卸载它们（建议先运行一遍卸载命令）。

```bash
sudo apt-get remove docker docker-engine docker.io containerd runc
```

### 设置Docker仓库进行安装

在新主机上首次安装 Docker Engine-Community 之前，需要设置 Docker 仓库。之后，您可以从仓库安装和更新 Docker 。

```bash
sudo apt-get update #更新apt包索引
```

安装apt依赖包，用于通过HTTPS来获取仓库

```bash
sudo apt-get install \
    apt-transport-https \
    ca-certificates \
    curl \
    gnupg-agent \
    software-properties-common
```

### 添加 Docker 的官方 GPG 密钥

```bash
curl -fsSL https://mirrors.ustc.edu.cn/docker-ce/linux/ubuntu/gpg | sudo apt-key add -
```

9DC8 5822 9FC7 DD38 854A E2D8 8D81 803C 0EBF CD88 通过搜索指纹的后8个字符，验证您现在是否拥有带有指纹的密钥。

```bash
sudo apt-key fingerprint 0EBFCD88
```

```
pub   rsa4096 2017-02-22 [SCEA]
      9DC8 5822 9FC7 DD38 854A  E2D8 8D81 803C 0EBF CD88
uid           [ unknown] Docker Release (CE deb) <docker@docker.com>
sub   rsa4096 2017-02-22 [S]
```

### 更新 apt 包索引

```bash
sudo apt-get update
```

### 安装 Docker Engine-Community

安装最新版本的 Docker Engine-Community 和 containerd

```bash
sudo apt-get install docker-ce docker-ce-cli containerd.io
```

### 检测Docker是否安装成功

输入以下指令

```bash
sudo docker run hello-world
```

打印出以下信息则安装成功

```bash
Unable to find image 'hello-world:latest' locally
latest: Pulling from library/hello-world
1b930d010525: Pull complete                                                                                                                                  Digest: sha256:c3b4ada4687bbaa170745b3e4dd8ac3f194ca95b2d0518b417fb47e5879d9b5f
Status: Downloaded newer image for hello-world:latest


Hello from Docker!
This message shows that your installation appears to be working correctly.


To generate this message, Docker took the following steps:
 1. The Docker client contacted the Docker daemon.
 2. The Docker daemon pulled the "hello-world" image from the Docker Hub.
    (amd64)
 3. The Docker daemon created a new container from that image which runs the
    executable that produces the output you are currently reading.
 4. The Docker daemon streamed that output to the Docker client, which sent it
    to your terminal.


To try something more ambitious, you can run an Ubuntu container with:
 $ docker run -it ubuntu bash


Share images, automate workflows, and more with a free Docker ID:
 https://hub.docker.com/


For more examples and ideas, visit:
 https://docs.docker.com/get-started/
```

## 卸载docker

删除安装包：

```bash
sudo apt-get purge docker-ce
```

删除镜像、容器、配置文件等内容：

```bash
sudo rm -rf /var/lib/docker
```

## 附：常见问题

安装完运行时出现以下报错：

```bash
"Got permission denied while trying to connect to the Docker daemon socket at unix:///var/run/docker.sock: Get http://%2Fvar%2Frun%2Fdocker.sock/v1.26/images/json: dial unix /var/run/docker.sock: connect: permission denied"
```

摘自docker mannual上的一段话

> https://forums.docker.com/t/got-permission-denied-while-trying-to-connect-to-the-docker-daemon-socket/113292

```bash
Manage Docker as a non-root user

The docker daemon binds to a Unix socket instead of a TCP port. By default that Unix socket is owned by the user root and other users can only access it using sudo. The docker daemon always runs as the root user.

If you don’t want to use sudo when you use the docker command, create a Unix group called docker and add users to it. When the docker daemon starts, it makes the ownership of the Unix socket read/writable by the docker group
```



**解决方法1**

使用sudo获取管理员权限，运行docker命令

**解决方法2**

docker守护进程启动的时候，会默认赋予名字为docker的用户组读写Unix socket的权限，因此只要创建docker用户组，并将当前用户加入到docker用户组中，那么当前用户就有权限访问Unix socket了，进而也就可以执行docker相关命令

```bash
sudo groupadd docker     #添加docker用户组
sudo gpasswd -a $USER docker     #将登陆用户加入到docker用户组中
newgrp docker     #更新用户组
docker ps    #重启后，测试docker命令是否可以使用sudo正常使用
```

