i386是32位系统， x86_64是64位系统

1.su 进入root账号
2.reboot重启系统

3.查看系统参数：uname -a

4.使用户能够使用sudo
在root下输入：visudo
找到  root   ALL(ALL)   ALL
在下面添加 adimn  ALL(ALL)  ALL

5.关机 sudo shutdown -h now
  重启 sudo shutdown -r now

6.golang 安装
解压 tar -zxf  go1.8.3xxxxxxx -C /usr/local
环境配置：
	用户下输入:vi ~/.bashrc
	在最后面输入：export GOROOT='/usr/local/go'
		      export PATH=$PATH:$GOROOT/bin
		      export GOBIN=$GOROOT/bin
	保存退出，输入：go version 检查是否配置成功
	在home下新建gopath文件下，在gopath文件夹下新建bin、src、pkg、文件夹
	添加以下变量：export GOPATH='/home/gopath'
		      

7.查看ip地址，ip address |ifconfig

8.若无法链接到外网，则：
	切换到系统网络配置目录：$ cd /etc/sysconfig/network-scripts
	修改enp0s3文件:		$ vi ifcfg-enp0s3
	ONBOOT=no改为 yes
	BOOTPROTO=dhcp
	保存退出，重启网络服务器 $ service network restart

  若无法ping到虚拟机，则：
	$ cd /etc/sysconfig/network-scripts
	$ vi ifcfg-enp0s8
	ONBOOT=no改为yes
	BOOYPTOYO=static
	添加固定ip： IPADDR=192.168.56.101
	添加子网掩码： NETMASK=255.255.255.0
	保存退出，重启网络服务器

9.wget https.....   从网络下载东西

10.软件一般安装在/usr/local/

11.grep "miner" -rl 搜索有miner单词的文件

12. 打开多个终端
ctrl+alt+F1一个终端ctrl+alt+F2第二个终端.......一直到F6，F7的话就是回到Xwindow

13. 挂载命令mount

	mount -t auto /dev/cdrom /mnt/cdrom

解释一下：
mount就是挂载命令了。
-t auto的意思是告诉mount命令我们需要挂载的那个device上的filesystem是什么类型的，这里用auto好了，CentOS会自动识别。
/dev/cdrom这是说明我们要挂载的设备访问路径。其实你仔细观察cdrom这个文件你就会发现，其实cdrom只是个链接文件，链接到sr0上。
/mnt/cdrom这个是说挂载之后的目标路径。换句话说，这就是光盘内容将要被映射之后的访问路径。需要注意的是，如果这个/mnt/cdrom不存在，那么要先用mkdir创建这个目录。一般mnt是存在的，只是cdrom不存在。

14.rpm -qa|grep mysql
rpm -qa 按照完整名查询
pm -qa http 不能查到 httpd
rpm -qa | grep 把查询到的东西交给 grep 过滤，可以模糊查询
