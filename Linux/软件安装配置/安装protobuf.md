## 安装前的环境

以下几个库都有安装

```
sudo apt-get install autoconf automake libtool curl make g++ unzip
```



## 安装

这里有两种方式安装，一种是通过apt方法安装，另外一种是通过下载源码进行编译安装，这里使用编译源码安装方式

1. 下载protobuf3.11.4

```
去github下载压缩包
```

2. 解压

```
unzip xxx3.11.4.zip
```

3. 编译安装

```
cd protobuf-3.11.4
git init
git submodule update --init --recursive
sudo ./autogen.sh
sudo  ./configure --prefix=/usr/local/protobuf  #--prefix指定安装目录,也可以不指定，即默认
sudo make
sudo make check
sudo make install
sudo ldconfig # refresh shared library cache.
```

4. 配置环境变量和动态连接库

```
更改环境变量：
vim /etc/profile
在文件的末尾添加如下的两行:
export PATH=$PATH:/usr/local/protobuf/bin/
export PKG_CONFIG_PATH=/usr/local/protobuf/lib/pkgconfig/

更改完成之后，执行如下命令立即执行：
source /etc/profile

配置动态链接库
vim /etc/ld.so.conf
在文件中添加/usr/local/protobuf/lib（注意: 在新行处添加）

更改完成之后，执行如下命令立即执行：
ldconfig

安装成功
protoc --version
```

## 卸载

> ```csharp
> sudo apt-get remove libprotobuf-dev
> ```

https://blog.csdn.net/m0_46392035/article/details/124697124