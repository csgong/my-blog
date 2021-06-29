# Ubuntu20.04 安装笔记

## 安装常用软件
### 1. qv2ray
```shell
sudo apt install gnupg ca-certificates curl
wget -SL https://qv2ray.net/debian/pubkey.gpg
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
### 3. navicat15
下载navicat并提取文件
```bash
#这个地址下载的版本是最新版，破解可能不支持，可以从https://github.com/HeQuanX/navicat-keygen-tools/releases/tag/recommended下载支持的旧版本
wget http://download3.navicat.com/download/navicat15-premium-cs.AppImage 
mkdir -p ./navicat15-premium-cs
sudo mount -o loop ./navicat15-premium-cs.AppImage ./navicat15-premium-cs
cp -r ./navicat15-premium-cs ./navicat15-premium-cs-patched
sudo umount ./navicat15-premium-cs
rm -rf ./navicat15-premium-cs
```
运行`docker`容器
```bash
docker run -it --rm --name navicat-keygen -v /home/sinclair/Downloads/navicat15-premium-cs-patched:/navicat15-premium-en-patched khoazero123/navicat-keygen /bin/bash
```
进入容器bash后，按照提示运行命令破解
```bash
/navicat-keygen/bin/navicat-keygen --text /RegPrivateKey.pem
```
在提示输入`Input request code in Base64`时，停止操作,另开启命令行窗口，将文件重新打包成AppImage
```bash
wget 'https://github.com/AppImage/AppImageKit/releases/download/continuous/appimagetool-x86_64.AppImage'
chmod +x appimagetool-x86_64.AppImage
./appimagetool-x86_64.AppImage ./navicat15-premium-cs-patched ./navicat15-premium-cs-patched.AppImage
```
打包完成后运行程序（要断网），在注册窗口填入破解程序生成的`Serial number`,，点击激活，这时由于没有网络会提示，激活失败，点击手动激活，将`Input request code`拷贝到破解程序中，按两次回车即可生成`Activation Code`

### 4. plank
参考[https://launchpad.net/~docky-core/+archive/ubuntu/stable](https://launchpad.net/~docky-core/+archive/ubuntu/stable)安装plank  
安装完成后，在`startup applications`中将plank设置为开机启动，plank路径为`/usr/bin/plank`  
需要设置plank时，按住`ctrl`+任意图标即可打开plank设置


### 5. 微信
首先安装deepin-wine  
```bash
wget -O- https://deepin-wine.i-m.dev/setup.sh | sh
```  
安装完成后安装微信即可，具体请参考[https://github.com/zq1997/deepin-wine](https://github.com/zq1997/deepin-wine)
```bash
sudo apt-get install com.qq.weixin.deepin
```   
安装后，如果遇到无法发送图片，或图片显示有问题，可以执行如下命令
```bash
sudo apt install libjpeg62:i386
``` 
### 6 云音乐
安装包在[官网](https://music.163.com/#/download)上，下载安装即可  
 ```bash
sudo dpkg -i netease-cloud-music_1.2.1_amd64_ubuntu_20190428.deb
```   
### 6 VLC media player 
参考[官网](https://www.videolan.org/vlc/download-ubuntu.html)，使用snap安装
 ```bash
sudo snap install vlc
``` 
安装完成后，给vlc更换皮肤，默认的太丑了  
去官网[这个页面](https://www.videolan.org/vlc/skins.php?sort=rating)下载皮肤,然后将下载的vlt文件拷贝到`/home/sinclair/snap/vlc/2288`目录下，打开vlc ，启用自定义皮肤`Tools->Preferences->Use custom skin`
