## Ubuntu20.04 修改静态ip

```

# 修改配置文件，有可能不叫50-cloud-init.yaml这个名字
sudo vi /etc/netplan/50-cloud-init.yaml
network:
    ethernets:
        ens33:  # 有可能叫eno1
            dhcp4: no
            addresses: [192.168.1.100/24]  # /24 一定要带上
            optional: true
            gateway4: 192.168.1.1
 
    version: 2
    
 # 重启网络配置
 sudo netplan apply
 
 # 查看ip地址
 ip addr
```

