



- 前置条件：你得有一张显卡。
- docker `sudo apt-get install docker`。查看是否安装好：`docker`
- Nvidia Driver. [NVIDIA驱动官网](https://www.nvidia.cn/Download/index.aspx?lang=cn)。查看是否安装好：`nvidia-smi`
- 接下来安装`nvidia-docker`。

```
# 注意这是一条命令，直接全部复制即可
distribution=$(. /etc/os-release;echo $ID$VERSION_ID) \
   && curl -s -L https://nvidia.github.io/nvidia-docker/gpgkey | sudo apt-key add - \
   && curl -s -L https://nvidia.github.io/nvidia-docker/$distribution/nvidia-docker.list | sudo tee /etc/apt/sources.list.d/nvidia-docker.list
```

```
sudo apt-get update
sudo apt-get install -y nvidia-docker2

# 重启一下docker
sudo systemctl restart docker

# 接下来你就可以愉快的使用nvidia-docker了
```





```
# 验证是否安装成功
sudo docker run --rm --gpus all nvidia/cuda:11.6.2-base-ubuntu20.04 nvidia-smi

# 执行上面的命令，如果显示跟下面类似的内容，说明nvidia-docker2已经安装成功。
Unable to find image 'nvidia/cuda:11.6.2-base-ubuntu20.04' locally
11.6.2-base-ubuntu20.04: Pulling from nvidia/cuda
846c0b181fff: Pull complete
b787be75b30b: Pull complete
40a5337e592b: Pull complete
8055c4cd4ab2: Pull complete
a0c882e23131: Pull complete
Digest: sha256:9928940c6e88ed3cdee08e0ea451c082a0ebf058f258f6fbc7f6c116aeb02143
Status: Downloaded newer image for nvidia/cuda:11.6.2-base-ubuntu20.04
Tue Jun 13 12:24:47 2023
+-----------------------------------------------------------------------------+
| NVIDIA-SMI 525.105.17   Driver Version: 525.105.17   CUDA Version: 12.0     |
|-------------------------------+----------------------+----------------------+
| GPU  Name        Persistence-M| Bus-Id        Disp.A | Volatile Uncorr. ECC |
| Fan  Temp  Perf  Pwr:Usage/Cap|         Memory-Usage | GPU-Util  Compute M. |
|                               |                      |               MIG M. |
|===============================+======================+======================|
|   0  NVIDIA GeForce ...  Off  | 00000000:01:00.0 Off |                  N/A |
|  0%   45C    P8    10W / 184W |    170MiB / 12288MiB |      0%      Default |
|                               |                      |                  N/A |
+-------------------------------+----------------------+----------------------+

+-----------------------------------------------------------------------------+
| Processes:                                                                  |
|  GPU   GI   CI        PID   Type   Process name                  GPU Memory |
|        ID   ID                                                   Usage      |
|=============================================================================|
+-----------------------------------------------------------------------------+
```



Reference

https://blog.csdn.net/qq_41776453/article/details/129794608

https://juejin.cn/post/7190264823744036922

https://blog.csdn.net/biejieyu1016/article/details/120874915

