## 安装[leanote](https://github.com/leanote/leanote "访问github")

## #环境准备

1. 下载golang、Mongodb
2. 获取Revel和 Leanote 的源码

## #安装环境
1. 安装golang
> 因为被墙的缘故  所以先想办法获取到golang的源码包  再使用xftp上载到ubuntu服务器上

- xhell连接ubuntu后，点这个按钮![](图片链接 "optional title")

- 然后把golang的源码包从左边拖到右边

- xhell中输入`ls -alh`查看文件大小是否一样

- 解压golang压缩包`tar -xzvf go1.12.7.linux-amd64.tar.gz`（注意不同的压缩算法解压命令不同）

- 解压完后发现多了个go目录，添加环境变量`vim /etc/profile`在最后根据自己的路径添加

  ```
  export GOROOT=/home/user1/go
  export GOPATH=/home/user1/gopackage
  export PATH=$PATH:$GOROOT/bin:$GOPATH/bin
  ```
  
 - 然后生效环境变量`source /etc/profile`，然后`go version`输入go的版本信息，安装golang环境完成
 
   ```
   root@11:~# go version
   go version go1.12.7 linux/amd64
   ```
   
2. 按照上面的步骤安装Mongodb

- 环境变量配置：只需要吧mongodb解压后的bin目录添加到`/etc/profile`文件末尾就行

- 测试mongodb可用，新建一个data目录，启动mongodb：`mongod --dbpath /root/data`，然后xshell新建一个终端

  ```
  root@11:~# mongo
  MongoDB shell version: 3.0.1
  connecting to: test
  Welcome to the MongoDB shell.
  For interactive help, type "help".
  For more comprehensive documentation, see
    http://docs.mongodb.org/
  Questions? Try the support group
    http://groups.google.com/group/mongodb-user
  Server has startup warnings: 
  2019-08-07T21:23:21.111+0800 I CONTROL  [initandlisten] ** WARNING: You are running this process as the root user, which is not recommended.
  2019-08-07T21:23:21.111+0800 I CONTROL  [initandlisten] 
  2019-08-07T21:23:21.111+0800 I CONTROL  [initandlisten] 
  2019-08-07T21:23:21.111+0800 I CONTROL  [initandlisten] ** WARNING: soft rlimits too low. rlimits set to 7800 processes, 65535 files. Number of processes should be at least 32767.5 : 0.5 times number of files.
  > show dbs
  local  0.078GB
  > 
  ```

- mongodb安装成功

3. 安装leanote

- 解压leanote-all-master.zip，`unzip leanote-all-master.zip`

- 新建gopackge目录，把leanote-all-master里面的src目录拷贝到gopackge目录下

- 执行`go install github.com/revel/cmd/revel`安装revel

- 导入leanote初始数据：`mongorestore -h localhost -d leanote --dir /root/gopackage/src/github.com/leanote/leanote/mongodb_backup/leanote_install_data`，查看如下导入数据成功

  ```
  root@11:~# mongo
  MongoDB shell version: 3.0.1
  connecting to: test
  Server has startup warnings: 
  2019-08-07T21:34:37.168+0800 I CONTROL  [initandlisten] ** WARNING: You are running this process as the root user, which is not recommended.
  2019-08-07T21:34:37.168+0800 I CONTROL  [initandlisten] 
  2019-08-07T21:34:37.168+0800 I CONTROL  [initandlisten] 
  2019-08-07T21:34:37.168+0800 I CONTROL  [initandlisten] ** WARNING: soft rlimits too low. rlimits set to 7800 processes, 65535 files. Number of processes should be at least 32767.5 : 0.5 times number of files.
  > show dbs
  leanote  0.078GB
  local    0.078GB
  > use leanote
  switched to db leanote
  > show collections
  albums
  attachs
  blog_comments
  blog_likes
  blog_singles
  configs
  email_logs
  files
  find_pwds
  group_users
  groups
  has_share_notes
  leanote.ShareNotes
  leanote.has_share_notes
  note_content_histories
  note_contents
  note_images
  note_tags
  notebooks
  notes
  reports
  sessions
  share_notebooks
  share_notes
  suggestions
  system.indexes
  tag_count
  tags
  themes
  tokens
  traffics
  user_blogs
  users
  > 
  ```
- 修改配置文件`vim /root/gopackage/src/github.com/leanote/leanote/conf/app.conf`把端口改成80，随机修改app.secret中的几位字母

- 安装完成

4. 运行leanote

- `revel run github.com/leanote/leanote`




