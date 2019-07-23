# ubuntu的基本使用

## #ubuntu18.04网络配置

> ubuntu18.04的网络配置跟之前的版本有很大的不同，已经不能用/etc/network/interface文件来配置网络，并且不存在文件/etc/init.d/networking，正确的姿势如下：

- 明确新版的网络配置文件为：`/etc/netplan/50-cloud-init.yaml￼￼`
- 重新加载配置文件的命令为：`sudo netplan apply`

> 配置静态ipv4例子：

- 50-cloud-init.yaml￼￼文件配置如下：
 ```
  network:
     ethernets:
         ens160:
             dhcp: no
             addresses:
             - 10.10.105.105/24
             gateway4: 10.10.105.254
             nameservers:
                 addresses: [202.96.209.133, 8.8.8.8]
     version: 2
 ```
 - 然后重新加载配置文件
 
 ## #修改主机名
 
 > 主机名为root@ubuntu
