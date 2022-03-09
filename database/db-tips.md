# 数据库笔记

## redis

### 1. centos系统中使用docker安装redis
下载镜像
```bash
docker pull redis
```
下载配置文件[redis.conf](http://download.redis.io/redis-stable/redis.conf)

修改配置文件：
* bind 127.0.0.1 #注释掉这部分，这是限制redis只能本地访问
* appendonly yes redis持久化
* requirepass 你的密码 #给redis设置密码

使用配置文件启动容器
```bash
docker run  --restart=always -p 6379:6379 --name redis -v /data/redis/redis.conf:/etc/redis/redis.conf  -v /data/redis/data:/data -d redis redis-server /etc/redis/redis.conf
```

## mysql

### docker下创建数据库用户并赋予权限
进入容器
```bash
docker exec -it mysql bash
```
使用root账号登录mysql
```bash
mysql -uroot -p
```
创建数据库，用户并分配权限

```bash
# 查看数据库
show databases;
# 查看用户
select user,host from mysql.user;
CREATE DATABASE IF NOT EXISTS dbname  DEFAULT CHARSET utf8 COLLATE utf8_general_ci;
create user 'username'@'%' identified by 'password';
grant all privileges  on dbname.* to 'username'@'%';
flush privileges; # 刷新权限
#查看权限
show grants for username;
+----------------------------------------------+
| Grants for yzw@%                             |
+----------------------------------------------+
| GRANT USAGE ON *.* TO 'yzw'@'%'              |
| GRANT ALL PRIVILEGES ON `yzw`.* TO 'yzw'@'%' |
+----------------------------------------------+
```