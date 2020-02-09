---
title: Rest
date: 2019-12-29 21:49:38
tags:
- Web
- Spring Boot
categories: Readings
---

# 聊一聊一点都没看懂的REST架构

虽然一直在用（大概也许应该），但是感觉自己一直没有完全搞懂这玩意，所以决定认真去学习一下，人在长大的同时记忆力的衰减真是无不恐怖的，所以还是得认真记录orz

## 清晰的总结

首先，我们必须知道REST这个单词代表了什么，代表了什么呢，Representational State Transfer，翻译为表现层状态转移。对的，我也觉得这完全不是人话。

在知乎上的[@Ivony](https://www.zhihu.com/people/6ef2e77274cb0719253a577665cf690e)老师的一句话确实很精辟：URL定位资源，用HTTP动词（GET、POST、DELETE等）描述操作。

REST描述的是网络中client和server的一种交互方式，本身并不实用，实用的是如何设计RESTful接口。

Server提供的RESTful接口中，URL只使用名词来指定资源，原则上不使用动词。“资源”是REST架构或者说整个网络处理的核心。

![img](https://pic1.zhimg.com/80/7405939b62a73f28846533de08db3a80_hd.jpg)

Server和Client之间传递某资源的一个表现形式，比如用JSON，XML传输文本，或者用JPG，WebP传输图片等。当然还可以压缩HTTP传输时的数据（on-wire data compression）。

用 HTTP Status Code传递Server的状态信息。比如最常用的 200 表示成功，500 表示Server内部错误等。

## 详细的说明

### REST的具体含义

Transfer：通俗来讲就是：资源在网络中以某种表现形式进行状态转移。分解开来：
Resource：资源，即数据（前面说过网络的核心）。比如 newsfeed，friends等；
Representational：某种表现形式，比如用JSON，XML，JPEG等；
State Transfer：状态变化。通过HTTP动词实现。

### 为什么要使用RESTful结构

"古代"网页是前端后端融在一起的，比如之前的PHP，JSP等。在之前的桌面时代问题不大，但是近年来移动互联网的发展，各种类型的Client层出不穷，RESTful可以通过一套统一的接口为 Web，iOS和Android提供服务。另外对于广大平台来说，比如Facebook platform，微博开放平台，微信公共平台等，它们不需要有显式的前端，只需要一套提供服务的接口，于是RESTful更是它们最好的选择。

![img](https://pic2.zhimg.com/80/06ee404783540f0af299042057738a99_hd.jpg)

### Server的API如何设计才满足RESTful要求

BAD

- /getProducts
- /listOrders
- /retrieveClientByOrder?orderId=1

GOOD

- GET /products : will return the list of all products
- POST /products : will add a product to the collection
- GET /products/4 : will retrieve product #4
- PATCH/PUT /products/4 : will update product #4

