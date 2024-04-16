---
title: "xampp搭建动态网页"
subtitle: ""
date: 2024-03-31T15:53:21+08:00
lastmod: 2024-03-31T15:53:21+08:00
draft: true

tags: []
categories: []
---
[Memos (daizixi.space)](https://memos.daizixi.space/?tag=web)

```shell
sudo chown griedzx /opt/lampp/htdocs/2021317210202
sudo chmod u+w /opt/lampp/htdocs/2021317210202
```

这是因为Web服务器（在你的情况下是Apache）被配置为在目录中查找并自动服务特定的默认文件。这些默认文件通常被命名为 `index.html`，`index.php`等。

当你访问一个目录（例如 `http://xampp.daizixi.space:1080/2021317210202/`）而不是具体的文件时，Web服务器会查看该目录下是否存在这些默认文件。如果存在，服务器就会自动返回这个文件的内容。

在你的情况下，`index.php`就是这个目录下的默认文件，所以当你访问 `http://xampp.daizixi.space:1080/2021317210202/`时，服务器就会返回 `index.php`的内容




griedzx: Access forbidden!

New XAMPP security concept:

Access to the requested directory is only available from the local network.

This setting can be configured in the file "httpd-xampp.conf".

GitHub Copilot: 这个错误信息表明，你正在尝试从非本地网络访问XAMPP，但是XAMPP的安全设置不允许这样做。默认情况下，XAMPP只允许从本地网络访问。

你可以修改 `httpd-xampp.conf`文件来改变这个设置。这个文件通常位于 `/opt/lampp/etc/extra/`目录下。

在 `httpd-xampp.conf`文件中，找到以下部分：

**apache**

```apache
<LocationMatch "^/(?i:(?:xampp|security|licenses|phpmyadmin|webalizer|server-status|server-info))">
    Require local
    ErrorDocument 403 /error/XAMPP_FORBIDDEN.html.var
</LocationMatch>
```

将 `Require local`改为 `Require all granted`，如下所示：

**apache**

```apache
<LocationMatch "^/(?i:(?:xampp|security|licenses|phpmyadmin|webalizer|server-status|server-info))">
    Require all granted
    ErrorDocument 403 /error/XAMPP_FORBIDDEN.html.var
</LocationMatch>
```

然后，保存文件并重启XAMPP。这样应该就可以从非本地网络访问XAMPP了。

请注意，这样做可能会增加安全风险，因为任何人都可以访问你的XAMPP。你应该确保你的XAMPP安装了最新的安全更新，并且只在信任的网络中使用这个设置。**#web**



[https://www.jianshu.com/p/0b9aecff290c](https://www.jianshu.com/p/0b9aecff290c)

hugo模板框架

[https://blog.csdn.net/qq_39490713/article/details/81161786](https://blog.csdn.net/qq_39490713/article/details/81161786)

xampp端口占用

[https://www.cnblogs.com/gangzi2013/p/6030157.html](https://www.cnblogs.com/gangzi2013/p/6030157.html)

**text**

```text
(base) [root@dzx lampp]# ./xampp start
Starting XAMPP for Linux 8.2.12-0...
XAMPP: Starting Apache...fail.
httpd: Syntax error on line 522 of /opt/lampp/etc/httpd.conf: Syntax error on line 6 of /opt/lampp/etc/extra/httpd-xampp.conf: Cannot load modules/mod_perl.so into server: libnsl.so.1: cannot open shared object file: No such file or directory
XAMPP: Starting MySQL...ok.
XAMPP: Starting ProFTPD...already running.
```

XAMPP启动失败，主要是因为Apache无法加载mod_perl.so模块，因为它依赖的libnsl.so.1库文件找不到。

在某些Linux发行版中，libnsl.so.1库可能不再默认安装。你可以尝试安装这个库来解决问题

sudo yum install libnsl

[https://askubuntu.com/questions/1102355/mysql-is-not-working-in-xampp-7-3-0-0-opt-lampp-bin-mysql-server-260-kill-n](https://askubuntu.com/questions/1102355/mysql-is-not-working-in-xampp-7-3-0-0-opt-lampp-bin-mysql-server-260-kill-n)

**text**

```text
2024-03-29 6:32:00 0 [ERROR] Can't start server: Bind on TCP/IP port. Got error: 98: Address already in use 
2024-03-29 6:32:00 0 [ERROR] Do you already have another mysqld server running on port: 3306 ? 
2024-03-29 6:32:00 0 [ERROR] Aborting 2024-03-29 06:32:01 51844 mysqld_safe mysqld from pid file /opt/lampp/var/mysql/dzx.pid ended 
2024-03-29 06:32:13 52226 mysqld_safe Starting mysqld daemon with databases from /opt/lampp/var/mysql
```

**text**

```text
(base) [root@dzx lampp]# /opt/lampp/bin/mysql.server: line 262: log_success_msg: command not found
```

[https://stackoverflow.com/questions/72753116/how-to-fix-opt-lampp-bin-mysql-server-line-261-log-success-msg-command-not-f](https://stackoverflow.com/questions/72753116/how-to-fix-opt-lampp-bin-mysql-server-line-261-log-success-msg-command-not-f)

sudo yum install redhat-lsb-core
