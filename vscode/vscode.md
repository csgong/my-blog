#  Visual Studio Code 笔记

## 安装扩展
### 1. GitLens     
GitLens 是git扩展，可以显示git log ，file history，compare branches or commits
### 2. Markdown插件  
Markdown插件需要安装`Markdown All in One`以及`Markdown Preview Github Styling`
### 3. Eclipse Keymap  
Ubuntu系统默认`switch-to-workspace-up`和`switch-to-workspace-down`快捷键和eclipse的整行复制快捷键冲突，需要禁用Ubuntu的系统对应的快捷键  
```bash
gsettings set org.gnome.desktop.wm.keybindings switch-to-workspace-up  "['']"
gsettings set org.gnome.desktop.wm.keybindings switch-to-workspace-down "['']"
```  
如果安装了网易云音乐，也会和云音乐的调整音量快捷键冲突，打开云音乐，将`启用全局快捷键`勾选掉就可以了
