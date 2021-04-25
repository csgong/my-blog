# Ubuntu20.04 安装笔记

## 安装常用软件
### 1. qv2ray
```shell
apt install gnupg ca-certificates curl
wget -sSL https://qv2ray.net/debian/pubkey.gpg
sudo apt-key add pubkey.gpg
echo "deb [arch=amd64] https://qv2ray.net/debian/ stable main" | sudo tee /etc/apt/sources.list.d/qv2ray.list
sudo apt-get update
sudo apt-get install qv2ray
```
安装完`qv2ray`后，需要配置`v2ray core`，从[https://github.com/v2fly/v2ray-core/releases](https://github.com/v2fly/v2ray-core/releases)下载v2ray-linux-64.zip包，解压至`/home/用户/.config/qv2ray/vcore`目录下即可，完成以上操作后即可导入配置
### 2. chrome
从[https://dl.google.com/linux/direct/google-chrome-stable_current_amd64.deb](https://dl.google.com/linux/direct/google-chrome-stable_current_amd64.deb)下载软件，然后安装即可
```bash
sudo apt install google-chrome-stable_current_amd64.deb
```
### 2. uget+aria2
```bash
sudo add-apt-repository ppa:plushuang-tw/uget-stable
sudo apt update
sudo apt install uget aria2
```  
* 软件配置  
  打开`edit->settings`,将`plug-in`设置为`aria2+curl`
右键`all category->properties`在`default for new download 1`中设置代理以及默认的保存路径。    
* 将`uget`设置为`chrome`默认的下载器  
  参考[https://github.com/ugetdm/uget-integrator](https://github.com/ugetdm/uget-integrator)安装方法安装`uget-integrator`，然后安装chrome插件[Chrome Extension](https://chrome.google.com/webstore/detail/uget-integration/efjgjleilhflffpbnkaofpmdnajdpepi)

