# VMware-ESXI-6.5集成第三方驱动

## 本文档介绍ESXI6.5如何集成第三方网卡、磁盘阵列驱动

### 前提条件 [GitHub](https://github.com/chensch/esxi-data "访问github")

> 硬件：H3C R4900G3； 网卡驱动：[i40en-1.7.11-1OEM.650.0.0.4598673.x86_64.vib](https://github.com/chensch/esxi-data/tree/master/vib "访问github")； 磁盘阵列驱动：[vmware-esxi-drivers-scsi-aacraid-600.6.2.1.54013.vib](https://github.com/chensch/esxi-data/tree/master/vib "访问github")； [ESXi-Customizer-PS-v2.6.0.ps1](https://github.com/chensch/esxi-data "访问github")； VMware-ESXi-6.5.0-4564106-depot.zip（自己下载）

###  #安装VMware.PowerCLI

- 管理员权限运行Windows PowerShell，执行命令`Install-Module -Name VMware.PowerCLI`,[详细说明](https://www.powershellgallery.com/packages/VMware.PowerCLI/6.5.1.5377412 "")

- 提示安装模块？键入`A`，将会联网安装Windows PowerShell的VMware.PowerCLI模块

- 安装可能比较慢，耐心等待，有问题[点我](https://www.google.com.hk/ "")

### #设置PowerShell执行策略

- `Set-ExecutionPolicy RemoteSigned`

- 是否要更改执行策略?键入`A`

- `Get-ExecutionPolicy`返回`RemoteSigned`为正常

### #生成自定义镜像
- 新建vib文件夹，把驱动文件都复制到vib

``` Mode                LastWriteTime         Length Name
----                -------------         ------ ----
d-----        2019/7/18     12:27                vib
-a----        2019/7/18      9:47          21003 ESXi-Customizer-PS-v2.6.0.ps1
-a----        2019/7/17     15:10      339994988 VMware-ESXi-6.5.0-4564106-depot.zip
```


- 执行`.\ESXi-Customizer-PS-v2.6.0.ps1 -v65 -izip .\VMware-ESXi-6.5.0-4564106-depot.zip -pkgDir .\vib`

- 等待...

