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
