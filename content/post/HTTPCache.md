---
title: HTTP缓存
date: 2018-12-26 15:00:00
tags: ["笔记"]
draft: true
---

### 分类

* 服务端缓存，又分为代理服务器缓存和反向代理服务器缓存
* 客户端缓存，即浏览器缓存
<!--more-->

#### 浏览器的缓存

* <b>Expires</b> HTTP/1.0中的实现，返回的到期时间是服务器的时间，这样一来如果浏览器和服务器时间相差特别大，缓存时间差别就很大，比如服务器和浏览器跨时区。这是弊端，所以HTTP/1.1中采用了Cache-Control: max-age=number代替

* <b>Cache-Control</b> 与Expires类似，都是指明当前资源的有效期，告诉浏览器直接读缓存还是从服务器重新拉取。Cache-Control拥有比Expires更多的选择。(如果同时存在Cache-Control与Expires，则Cache-Control优先级高)

以上二者都是强缓存，就是说若是命中缓存且缓存还有效就不发送请求，直接返回200(from cache)

Cache-Control的值可以是以下几种：

* public 可以被任何可缓存区缓存(包括代理服务器以及客户端)
* private 单个用户的缓存，不可被共享，对于其他用户的请求无效，不允许代理服务器缓存
* no-cache 请求或消息不能(或不使用？)缓存
* no-store 完全不存
* no-transform 代理不转换资源类型，例如image/jpg -> image/png
* must-revalidate 和no-cache类似，暂时没弄明白
* proxy-revalidate 代理缓存一旦过期则需向服务器请求
* max-age 资源有效期，单位是秒

### Last-Modified/If-Modified-Since和Etag/If-None-Match(协商缓存？Etag(HTTP/1.1引入)优先比对)

这二者都要配合Cache-Control使用，当资源过期时(例如Cache-Control使用了max-age声明)，若发现资源带有Last-Modified或Etag声明，则向服务器请求时带上If-Modified-Since或If-None-Match。If-Modified-Since表示请求时间，服务器收到后与资源最后的修改时间做对比，若发现这个请求时间比最后修改时间新，则说明资源自上次缓存后没有修改过，服务器直接返回304，反之则需返回新的资源。而Etag则是服务器生成并且告知浏览器的当前资源在服务器的唯一标识，If-None-Match标识Etag的值，服务器收到后可以进行比对，相同则返回304，不同则返回整个资源。

### 用户行为与协商缓存

|用户行为 | Expires/Cache-Control | Last-Modified/Etag|
|--------|:----------------------:|:------------------:|
|地址栏回车|有效|有效|
|页面链接跳转|有效|有效|
|新开窗口|有效|有效|
|前进、后退|有效|有效|
|F5刷新|无效|有效|
|Ctrl+F5刷新|无效|无效|


#### 参考

1. [浏览器HTTP协议缓存机制详解](https://www.cnblogs.com/520yang/articles/4807408.html)
2. [浏览器缓存机制](http://www.cnblogs.com/skynet/archive/2012/11/28/2792503.html)