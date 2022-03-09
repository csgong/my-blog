# NPM  

## 脚本中执行vue-cli-service 提示permission denied

这是 `node_modules/.bin/`目录下的程序没有执行权限，赋予执行权限即可

```bash
chmod -R 755 ./*
```