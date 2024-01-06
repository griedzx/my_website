---
title: "Script"
subtitle: ""
date: 2024-01-05T16:46:16+08:00
lastmod: 2024-01-05T16:46:16+08:00
draft: true

tags: []
categories: []
---

打印出指定列中出现重复的行  

```
awk -F ',' '{print $1}' /path/to/your_file | sort | uniq -d | while read line; do grep -F "$line" /path/to/your_file; done
```
