# Ubuntu 使用过程中遇到的问题

## SSH 
1. ssh卡在debug1: SSH2_MSG_KEXINIT sent  
在使用ssh连接服务器时，没有相应，连接时，使用`-v`参数时，发现卡在了`debug1: SSH2_MSG_KEXINIT sent`这一步
解决方法就是找到对应的网络设备并重新设置mtu大小，我的在`/sys/class/net/wlp4s0/mtu`.打开这个文件，修改值为1492。
2. 记住服务器配置  
在连接服务器时，每次都要输入ip地址，用户以等很不方便，可以使用ssh_config解决这个问题，在.ssh目录下创建config文件，输入如下内容
```
Host=servername #服务器别名
	HostName=ip #服务器ip地址
	User=username #登录的用户名
	Port=22 #端口
	IdentityFile=/home/sinclair/.ssh/id_rsa #指定私钥文件路径，如果私钥文件已经放在.ssh/id_rsa，则不需要指定
```
这样配置以后，在使用`ssh`连接服务器时，只要指定servername就可以了
```bash
ssh servername
```
## File
有些时候在操作文件时，会提示**Text file busy**，发生此错误是因为当前文件已被占用，可以使用`fuser`命令查找哪个进程占用了该文件并杀死就可以了。
```bash
sudo fuser 文件名
sudo kill -9 进程id
```