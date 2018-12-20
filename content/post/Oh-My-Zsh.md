---
title: Oh-My-Zsh安装
date: 2018-01-10 15:05:06
tags: ["工具"]
draft: false
---


1. 安装Git以及zsh
```
# apt-get install git zsh
```

2. 下载项目到本地（有点慢）
```
git clone https://github.com/robbyrussell/oh-my-zsh.git ~/.oh-my-zsh
```

3. 如果根目录之下有.zshrc这个zsh的配置文件则备份
```
cp ~/.zshrc ~/.zshrc.back
```

4. 通过oh-my-zsh的配置模板新建zsh的配置文件
```
cp ~/.oh-my-zsh/templates/zshrc.zsh-template ~/.zshrc
```

5. 安装工作完毕，更换默认shell，需要重启会话
```
# chsh -s /bin/zsh
```

6. 重新打开一个终端，可能会发现乱码，原因是没有安装PowerLine的字体
```
# apt-get install fonts-powerline
```

7. Theme更换,编辑.zshrc文件,找到ZSH_THEME这一行修改即可 （[内置主题列表](https://github.com/robbyrussell/oh-my-zsh/wiki/Themes)）
```
vim ~/.zshrc
```