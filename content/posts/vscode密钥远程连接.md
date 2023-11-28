---
title: "Vscode密钥远程连接"
subtitle: ""
date: 2023-11-20T19:58:51+08:00
lastmod: 2023-11-20T19:58:51+08:00
draft: true

tags: []
categories: []
---
配置密钥

```powershell
PS C:\Users\griezdzx\.ssh> ssh-keygen
Generating public/private rsa key pair.
Enter file in which to save the key (C:\Users\griezdzx/.ssh/id_rsa): #
```

设定目录下会出现密钥对文件：id_rsa.pub是公钥 id_rsa是私钥

公钥放server(远程主机)上，私钥放本机上

建议直接cat 本地的id_rsa.pub，然后复制内容到服务器的~/.ssh/authorized_keys中新增一行

#客户端

```powershell
PS C:\Users\griezdzx\.ssh> cat id_rsa.pub
```

#服务端

```shell
(base) yh@localhost 21:21:38 ~/.ssh
$ vim authorized_keys
```


修改vscode的config file，加入 IdentityFile 和对应的**本机私钥**路径

修改.ssh/config文件：加入IdentityFile的路径（也就是私钥在本机的所在位置）


vscode登录server就不用输入密码了
