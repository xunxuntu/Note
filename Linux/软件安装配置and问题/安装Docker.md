

```
# 导入新的HTTPS应用库(repository)
sudo apt update
sudo apt install apt-transport-https ca-certificates curl gnupg-agent software-properties-common

# 导入应用库的 GPG 密钥
curl -fsSL https://download.docker.com/linux/ubuntu/gpg | sudo apt-key add -

# 把APT应用库加载入我们的系统
sudo add-apt-repository "deb [arch=amd64] https://download.docker.com/linux/ubuntu $(lsb_release -cs) stable"

# 安装最新版本的Docker
sudo apt update
sudo apt install docker-ce docker-ce-cli containerd.io

# 查看docker 版本
docker version

# 查看docker运行状态
sudo systemctl status docker

# 执行下面的命令会下载一个Docker测试镜像，并在容器中执行一个“hello-world”样例程序。
sudo docker run hello-world

# 如果你看到类似下方的输出，那么祝贺你，Docker能够正常运行在你的Ubuntu系统中了。
ubuntu@VM-16-10-ubuntu:~$ sudo docker run hello-world
Unable to find image 'hello-world:latest' locally
latest: Pulling from library/hello-world
2db29710123e: Pull complete 
Digest: sha256:53f1bbee2f52c39e41682ee1d388285290c5c8a76cc92b42687eecf38e0af3f0
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



拓展

```
# 设置Docker服务在每次开机时自动启动
sudo systemctl enable docker

# 查看docker运行状态
systemctl status docker

# 启动Docker服务
sudo systemctl start docker
```



# Reference

https://esharing.net/linux/239/%E5%A6%82%E4%BD%95%E5%9C%A8ubuntu20-04%E5%AE%89%E8%A3%85docker/

https://www.cnblogs.com/Can-daydayup/p/16472375.html

