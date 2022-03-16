# LINUX 笔记

## 本地和服务器文件传输

```bash
# 上传文件到服务器
scp 本地文件 root@serverIp:serverDIr
#从服务器下载文件
scp root@serverIp:serverDIr 本地文件
```

## centos 7 安装nginx
安装依赖环境
```bash
yum install -y gcc-c++   pcre pcre-devel zlib zlib-devel openssl openssl-devel
```
下载nignx
```bash
wget -c https://nginx.org/download/nginx-1.20.0.tar.gz
```
解压手编译安装
```bash
make
make install
```

配置文件目录：

/usr/local/nginx/conf/nginx.conf

启动停止 nginx

```bash
cd /usr/local/nginx/sbin/
./nginx 
./nginx -s stop
./nginx -s quit
./nginx -s reload
```
