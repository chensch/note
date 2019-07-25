# Esxi 6.5 更新到Esxi 6.7

## #上传Esxi6.7的ZIP包到Esxi6.5的数据存储区

- [官网下载Esxi 6.7](https://www.vmware.com/ "VMWare官网")

- 上传下载的zip包到根数据存储区

## #SSH连接Esxi 6.5

- 浏览器打开Esxi 6.5的web ui控制面板

- 主机 > 操作 > 服务 > 启用安全Shell（SSH）

- 用XShell等软件SSH到Esxi 6.5

## #升级操作

- 明确Esxi 6.7文件的路径，存储 > datastore* > 位置（如果多块磁盘，选择存储了esxi 6.7那块）

- 路径为：`位置/上传文件的名字（包含扩展名）`

- 查看升级包信息`esxcli software sources profile list -d  路径`

  ```
  esxcli software sources profile list -d  /vmfs/volumes/5d317b21-2fe52b34-29be-04d7a54540f3/update-from-esxi6.7-6.7_update02.zip
  ```
- 得到如下结果

  ```
    Name                              Vendor        Acceptance Level  Creation Time        Modification Time
  --------------------------------  ------------  ----------------  -------------------  -------------------
  ESXi-6.7.0-20190402001-no-tools   VMware, Inc.  PartnerSupported  2019-03-27T04:46:55  2019-03-27T04:46:55
  ESXi-6.7.0-20190401001s-no-tools  VMware, Inc.  PartnerSupported  2019-03-27T04:46:55  2019-03-27T04:46:55
  ESXi-6.7.0-20190402001-standard   VMware, Inc.  PartnerSupported  2019-03-27T04:46:55  2019-03-27T04:46:55
  ESXi-6.7.0-20190401001s-standard  VMware, Inc.  PartnerSupported  2019-03-27T04:46:55  2019-03-27T04:46:55
  ```
- 选择一个进行更新`esxcli software profile update -d  路径 -p 名字`

  ```
  esxcli software profile update -d  /vmfs/volumes/5d317b21-2fe52b34-29be-04d7a54540f3/update-from-esxi6.7-6.7_update02.zip -p ESXi-6.7.0-20190402001-standard
  ```

- 重启Esxi检查是否成功

  > 如果没有报错，提示升级完成请重启，重启后检查Esxi版本是不是6.7

  - `reboot`

  - `vmware -vl`
  
  
## 修改Esxi的主机名
  
## #基本命令

> 详细内容[点我](https://kb.vmware.com/s/article/1010821?lang=zh_CN "更改 ESX 或 ESXi 主机的名称")， [hostname和fqdn的区别](https://blog.51cto.com/cuidehua/1788240 "hostname和fqdn的区别")

  
- `esxcli system hostname set --host=hostname`
  
- `esxcli system hostname set --fqdn=fqdn`

## #修hostname为test-server

- `esxcli system hostname set --host=test-server`
