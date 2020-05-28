# SSH服务的安装和配置

- ## 安装SSH工具

1. 打开终端按入如下命令：

   ```
   apt-get install openssh-server
   ```

2. 如果安装了就不用选择Y如果没有安装选择Y执行：

   ![](C:\Users\Administrator\Desktop\Ubuntu18.04下安装配置SSH服务和FTP服务\ssh\2020-05-26_162506.png)

   ![](C:\Users\Administrator\Desktop\Ubuntu18.04下安装配置SSH服务和FTP服务\ssh\2020-05-26_162545.png)

- ## 启动SSH服务

  1. 键入如下命令：

     ```
     /etc/init.d/ssh start
     ```

     ![](C:\Users\Administrator\Desktop\Ubuntu18.04下安装配置SSH服务和FTP服务\ssh\2020-05-26_162723.png)

     注：重启命令与关闭命令如下：

     ```
     /etc/init.d/ssh start	#启动（开始）SSH服务
     /etc/init.d/ssh restart	#重启SSH服务
     /etc/init.d/ssh stop	#关闭SSH服务
     ```

  2. 查看进程，检查是否启动成功，键入如下命令

     ```
     ps -e | grep sshd
     ```

     ![](C:\Users\Administrator\Desktop\Ubuntu18.04下安装配置SSH服务和FTP服务\ssh\2020-05-26_162842.png)

     有了进程才能进行ssh服务的使用

- ## 配置SSH服务

  Ubuntu中SSH服务安装完成后查看是否允许root用户登陆，若不允许则无法远程登陆root用户，需要修改配置

  1. 首先，打开“/etc/ssh/sshd_config”

     ```
     vim /etc/ssh/sshd_config
     ```

  2. 查看是否有“PermitRootLogin yes”，没有修改即可，完成后保存退出

     ![](C:\Users\Administrator\Desktop\Ubuntu18.04下安装配置SSH服务和FTP服务\ssh\2020-05-26_163327.png)

- ## 验证能否连接成功

  1. 检查本机ip地址，键入ifconfig

     ```
     ifconfig
     ```

     ![](C:\Users\Administrator\Desktop\Ubuntu18.04下安装配置SSH服务和FTP服务\ssh\2020-05-26_163504.png)

  2. 获取本机IP之后，在window下测试连接，本人使用的是xshell，可以使用其他诸如Putty、secureCRT等

     （1）新建会话

     	![](C:\Users\Administrator\Desktop\Ubuntu18.04下安装配置SSH服务和FTP服务\ssh\2020-05-26_164148.png)

     （2）输入账户名和密码

     	![](C:\Users\Administrator\Desktop\Ubuntu18.04下安装配置SSH服务和FTP服务\ssh\2020-05-26_164613.png)

     (3)测试远程连接普通用户可以直接连接上了，但是root用户不可以，还得修改一下配置文档

     ```
     vim /etc/ssh/sshd_config
     ```

     在这个文件中修改的吗，这是没有修改前的：

     ![](C:\Users\Administrator\Desktop\Ubuntu18.04下安装配置SSH服务和FTP服务\ssh\2020-05-26_165448.png)

     修改后的：

     ![](C:\Users\Administrator\Desktop\Ubuntu18.04下安装配置SSH服务和FTP服务\ssh\2020-05-26_165515.png)

     然后在终端输入重新启动SSH服务

     ```
     /etc/init.d/ssh restart
     ```

     重新使用root连接就可以了

     ![](C:\Users\Administrator\Desktop\Ubuntu18.04下安装配置SSH服务和FTP服务\ssh\2020-05-26_165515.png)

