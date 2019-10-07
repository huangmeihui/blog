---
title: Debian 安装 Oh-My-Zsh
date: 2019-10-07
tags: ["工具"]
draft: false
---

* 安装 Git 以及 zsh

```bash
sudo apt update
sudo apt install git zsh
```

<!--more-->

* 下载项目到本地

```bash
git clone https://github.com/robbyrussell/oh-my-zsh.git ~/.oh-my-zsh --depth 1
```

* 如果根目录之下有 .zshrc 这个 zsh 的配置文件则备份

```bash
cp ~/.zshrc ~/.zshrc.back
```

* 通过 oh-my-zsh 的配置模板新建 zsh 的配置文件

```bash
cp ~/.oh-my-zsh/templates/zshrc.zsh-template ~/.zshrc
```

* 安装工作完毕，更换默认 shell ，需要重启会话

```bash
chsh -s /bin/zsh
```

* 重新打开一个终端，可能会发现乱码，原因是没有安装 PowerLine 的字体（不同的 Linux 发行版可能有不同的包，建议先搜索一下）

```bash
sudo apt install fonts-powerline
```

* Theme更换,编辑 .zshrc 文件,找到 ZSH_THEME 这一行修改即可 （[内置主题列表](https://github.com/robbyrussell/oh-my-zsh/wiki/Themes)）

```bash
vim ~/.zshrc
## 举个栗子
ZSH_THEME = "agnoster"
```

* 手动更新

```bash
upgrade_oh_my_zsh
```