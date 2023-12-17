---
title: "Xrdp"
subtitle: ""
date: 2023-11-30T12:39:52+08:00
lastmod: 2023-11-30T12:39:52+08:00
draft: true

tags: []
categories: []
---
## Ubuntu 22.04 安装 Xrdp

宝塔安装

```shell
wget -O install.sh https://download.bt.cn/install/install-ubuntu_6.0.sh && sudo bash install.sh ed8484bec
```


### 安装桌面环境

Ubuntu 服务器通常使用命令行进行管理，并且默认没有安装桌面环境。如果你正在运行 Ubuntu 桌面版，忽略这一步。

在 Ubuntu 源仓库有很多桌面环境供你选择。一个选择是安装 Gnome，它是 Ubuntu 20.04 的默认桌面环境。另外一个选项就是安装 xfce。它是快速，稳定，并且轻量的桌面环境，使得它成为远程服务器的理想桌面。

运行下面任何一个命令去安装你选择的桌面环境：

* 安装 Gnome

```
sudo apt update
sudo apt install ubuntu-desktop
```

* 安装 Xfce

```
sudo apt update
sudo apt install xubuntu-desktop
```

### 安装xrdp

```
sudo ap
```

默认情况下，Xrdp 使用 `/etc/ssl/private/ssl-cert-snakeoil.key`,它仅仅对“ssl-cert” 用户组成语可读。运行下面的命令，将 `xrdp`用户添加到这个用户组：

```
sudo adduser xrdp ssl-cert  
```

重启 Xrdp 服务，使得修改生效：

```
sudo systemctl restart xrdp
```

[(1 封私信 / 56 条消息) 免费密码管理器 bitwarden 的实际使用体验如何？ - 知乎 (zhihu.com)](https://www.zhihu.com/question/58299407)
