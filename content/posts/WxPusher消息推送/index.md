---
title: "WxPusher小程序推送消息"
subtitle: ""
date: 2023-11-22T19:30:14+08:00
lastmod: 2023-11-22T19:30:14+08:00
draft: true

tags: []
categories: []
---
[WxPusher微信推送服务 (zjiecode.com)](https://wxpusher.zjiecode.com/docs/#/?id=http%e8%b0%83%e7%94%a8)

```python
def send_wechat(title, content):
    """Send Message."""
    payload = {
        "summary": title,
        "content": content,
        "appToken": "AT_2W92UXQOYUNo0iu8ncKzpm36ReLv2PB7", 
        "contentType": 1,
        # "topicIds": [123],
        "uids": ["UID_32mmCWTWS0EPK20xgeNtXclfr9ch"],   
        # "url": "http://wxpusher.zjiecode.com" // 原文链接，可选参数
    }
    url = 'http://wxpusher.zjiecode.com/api/send/message'
    return requests.post(url, json=payload).json()
```


```python
    result = send_wechat(title='投递任务运行结束',
                        content="submit job done!")
```
