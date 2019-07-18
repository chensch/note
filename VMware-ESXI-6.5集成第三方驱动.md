# VMware-ESXI-6.5集成第三方驱动

## 本文档介绍ESXI6.5如何集成第三方网卡、磁盘阵列驱动

> 硬件：H3C R4900G3； 网卡驱动：[example link](http://example.com/ "With a Title")； 磁盘阵列驱动：[example link](http://example.com/ "With a Title")

###  #安装VMware.PowerCLI

- 管理员权限运行Windows PowerShell，执行命令`Install-Module -Name VMware.PowerCLI -RequiredVersion 6.5.1.5377412`

- 提示安装模块？键入`A`，将会联网安装Windows PowerShell的VMware.PowerCLI模块
