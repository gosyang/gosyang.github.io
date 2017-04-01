---
layout: post
title: 《RESTful Web APIs》读书笔记
categories: [Reading]
description: Safari online reading
keywords: RESTful, Web
---


## Introduction
1. 设计的目标是面对繁多的变化
2. 统一减少重复工作
3. Hypermedia is Hard
	* capable of handling changes gracefully

## 1. Surfing the Web

1. A URL identifies one and only one resource. Every resource should have its own URL.
2. Status Machine, by GET, POST, change to different url resources

## 2. A Simple API
1. HTTP GET is Safe, just to see what's behind it
2. Collection + Json, items contain all the href datas

#### Response
```
Content-Type: application/vnd.collection+json

{"collection":{
        "version":"1.0",
        "href":"http://www.youtypeitwepostit.com/api/",
        "items":[
            {
                "href":"http://www.youtypeitwepostit.com/api/04771712399087846",
                "data":[
                    {
                        "name":"text",
                        "value":"Squid!"
                    },
                    {
                        "name":"date_posted",
                        "value":"2017-04-01T03:01:27.482Z"
                    }
                ]
            }
        ],
        "template":{
            "data":[
                {
                    "prompt":"Text of message",
                    "name":"text",
                    "value":""
                }
            ]
        }
    }
}

```

3. Writing to an API: POST the template with own data - How resources are Born

#### Request

```
POST /api/ HTTP/1.1
Host: www.youtypeitwepostit.com
Content-Type: application/vnd.collection+json

{ "template":
	{
  		"data": [
   			{"prompt": "Text of the message", "name": "text", "value": "Squid!"}
  		]
 	}
}
```

#### Response:
```
HTTP/1.1 201 Created
Location: http://www.youtypeitwepostit.com/api/47210977342911065
```

4. 解放安全限制 **`没太明白`**
	- when don't what behind url, just GET and see zhe res
	- 通过collection+json格式，可以统一语义，便于理解
5. 统一语义 
	- **`统一成什么？`** 因为这种也是个人定义的

