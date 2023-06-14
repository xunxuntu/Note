```
# 直接点击 Download， 他会自动识别系统下载最新的版本
https://www.anaconda.com/download

# 进入下载文件夹，运行安装文件
bash Anaconda3-2023.03-1-Linux-x86_64.sh

# 接受安装协议，按enter确定；阅读注册信息，一直按空格键阅读；确定anaconda的安装位置，按enter确定，初始化Anaconda3,输入yes；加入环境变量的提示信息，输入yes

# 加入环境变量
sudo gedit ~/.bashrc

# 在文件最后两行写入
export PATH="~/anaconda3/bin":$PATH
source ~/anaconda3/bin/activate

# 应用配置
source ~/.bashrc

# 重新打开一个终端，会发现自动进入（base）环境，即可默认使用Anaconda3

# 设置 `自动进入base环境` 为False就不会默认显示(base)
conda config --set auto_activate_base false

# 验证anaconda是否安装成功
conda -V
```



Reference

https://blog.csdn.net/abc20150125/article/details/129998028