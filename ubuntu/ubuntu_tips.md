# Ubuntu 使用过程中遇到的问题

## 1.ssh卡在debug1: SSH2_MSG_KEXINIT sent
在使用ssh连接服务器时，没有相应，连接时，使用`-v`参数时，发现卡在了`debug1: SSH2_MSG_KEXINIT sent`这一步
解决方法就是找到对应的网络设备并重新设置mtu大小，我的在`/sys/class/net/wlp4s0/mtu`.打开这个文件，修改值为1492。
