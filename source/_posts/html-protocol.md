---
title: HTTP协议简单说明
date: 2020-05-05 21:25:33
tags:
- http
copyright: true
categories:
- 前端

---
HTTP 是超文本传输协议，它定义了客户端和服务器之间交换报文的格式和方式，默认使用 80 端口。它使用 TCP 作为传输层协议，保证了数据传输的可靠性。
<!--more-->

## 前言——何为协议
<p><strong>协议就是事先规定好的通信规则，在双方约定的规则下进行通信，才能让双方建立正确有效的信息传输。</strong></p>
<p><strong>驯兽师拍拍手，动物就自觉坐下。这就是一种定义好的协议。</strong></p>

## HTTP构成
<p><strong>客户端与服务端 客户端发送请求至服务端 服务端返回响应（http中数据称为资源，由URL定位）。</strong></p>

## URL统一资源定位符
<p><strong><span style="color: #99cc00;">protocol协议、<span style="color: #00ccff;">host主机、<span style="color: #000000;">port端口（可选）、</span><span style="color: #ff9900;">path路径，<span style="color: #000000;">query查询（可选）</span></span></span></span></strong></p>
<p><strong>
<p><strong><a href="https://www.cnblogs.com/nydus/"><span style="color: #99cc00;">https://<span style="color: #00ccff;">www.cnblogs.com/<span style="color: #ff9900;">nydus/</span></span></span></a></strong></p>

## 发送http请求
<p><strong><img src="https://img2020.cnblogs.com/blog/2018457/202005/2018457-20200504124456195-455474342.jpg" alt="" /></strong></p>

### 请求方式
<p><strong><img src="https://img2020.cnblogs.com/blog/2018457/202005/2018457-20200504124531051-279752497.jpg" alt="" /></strong></p>

## 接受HTTP响应
<p><strong>HTTP 响应报文的第一行叫做状态行，后面的行是首部行，最后是实体主体。</strong></p>
<p><strong>状态行包含了三个字段：协议版本字段、状态码和相应的状态信息。</strong></p>
<p><strong>实体部分是报文的主要部分，它包含了所请求的对象。</strong></p>
<div class="cnblogs_Highlighter">
<pre class="brush:html;gutter:true;"><strong>HTTP/1.0 200 OK
Content-Type: text/plain
Content-Length: 137582
Expires: Thu, 05 Dec 1997 16:00:00 GMT
Last-Modified: Wed, 5 August 1996 15:55:28 GMT
Server: Apache 0.84

&lt;html&gt;
  &lt;body&gt;Hello World&lt;/body&gt;
&lt;/html&gt;</strong></pre>
</div>

### 常见的HTTP状态码：
<ul>
<li><strong>200 OK- 请求成功 一般用于GET与POST请求</strong></li>
<li><strong>301 Moved Permanently - 资源（网页等）被永久转移到其它URL（重定向）</strong></li>
<li><strong>404 Not Found - 客户端请求的资源（网页等）不存在</strong></li>
<li><strong>500 Internal Server Error- 服务端错误</strong></li>
</ul>

## Cookie
<p><strong>HTTP不记录客户端信息，每次发送请求要指明是同一客户端要使用Cookie辨别用户身份。</strong></p>
<p><strong>Cookie，有时也用其复数形式&nbsp;Cookies。类型为&ldquo;小型文本文件&rdquo;，是某些网站为了辨别用户身份，进行Session跟踪而储存在用户本地终端上的数据（通常经过加密），由用户客户端计算机暂时或永久保存的信息。</strong></p>
<p><strong><img src="https://img2020.cnblogs.com/blog/2018457/202005/2018457-20200504131855076-2107951053.jpg" alt="" /></strong></p>

## HTTP/2 协议
<p><strong>2009 年，谷歌公开了自行研发的 SPDY 协议，主要解决 HTTP/1.1 效率不高的问题。这个协议在 Chrome 浏览器上证明 可行以后，就被当作 HTTP/2 的基础，主要特性都在 HTTP/2 之中得到继承。2015 年，HTTP/2 发布。</strong></p>

## HTTP/2 新特性：

### 二进制协议
<p><strong>HTTP/2 是一个二进制协议。在 HTTP/1.1 版中，报文的头信息必须是文本（ASCII 编码），数据体可以是文本，也可以是二进制。HTTP/2 则是一个彻底的二进制协议，头信息和数据体都是二进制，并且统称为"帧"，可以分为头信息帧和数据帧。 帧的概念是它实现多路复用的基础。减小了文件体积。</strong></p>

### 多路复用
<p><strong>HTTP/2 实现了多路复用，HTTP/2 仍然复用 TCP 连接，但是在一个连接里，客户端和服务器都可以同时发送多个请求或回应，而且不用按照顺序一一发送，这样就避免了"队头堵塞"的问题。</strong></p>

### 数据流
<p><strong>HTTP/2 使用了数据流的概念，因为 HTTP/2 的数据包是不按顺序发送的，同一个连接里面连续的数据包，可能属于不同的请求。因此，必须要对数据包做标记，指出它属于哪个请求。HTTP/2 将每个请求或回应的所有数据包，称为一个数据流。每 个数据流都有一个独一无二的编号。数据包发送的时候，都必须标记数据流 ID ，用来区分它属于哪个数据流。</strong></p>

### 头信息压缩
<p><strong>HTTP/2 实现了头信息压缩，由于 HTTP 1.1 协议不带有状态，每次请求都必须附上所有信息。所以，请求的很多字段都是重复的，比如 Cookie 和 User Agent ，一模一样的内容，每次请求都必须附带，这会浪费很多带宽，也影响速度。</strong></p>
<p><strong>HTTP/2 对这一点做了优化，引入了头信息压缩机制。一方面，头信息使用 gzip 或 compress 压缩后再发送；另一方面， 客户端和服务器同时维护一张头信息表，所有字段都会存入这个表，生成一个索引号，以后就不发送同样字段了，只发送索引号，这样就能提高速度了。</strong></p>

### 服务器推送
<p><strong>HTTP/2 允许服务器未经请求，主动向客户端发送资源，这叫做服务器推送。使用服务器推送，提前给客户端推送必要的资源 ，这样就可以相对减少一些延迟时间。这里需要注意的是 http2 下服务器主动推送的是静态资源，和WebSocket 以及使用 SSE 等方式向客户端发送即时数据的推送是不同的。</strong></p>

## HTTPS 协议

### HTTP 存在的问题
<ol>
<li>
<p><strong>HTTP 报文使用明文方式发送，可能被第三方窃听。</strong></p>
</li>
<li>
<p><strong>HTTP 报文可能被第三方截取后修改通信内容，接收方没有办法发现报文内容的修改。</strong></p>
</li>
<li>
<p><strong>HTTP 还存在认证的问题，第三方可以冒充他人参与通信。</strong></p>
</li>
</ol>

### HTTPS 简介
<p><strong>HTTPS 指的是超文本传输安全协议，HTTPS 是基于 HTTP 协议的，不过它会使用 TLS/SSL 来对数据加密。使用 TLS/ SSL 协议，所有的信息都是加密的，第三方没有办法窃听。并且它提供了一种校验机制，信息一旦被篡改，通信的双方会立刻发现。它还配备了身份证书，防止身份被冒充的情况出现。</strong></p>

#### TLS 握手过程
<ol>
<li>
<p><strong>第一步，客户端向服务器发起请求，请求中包含使用的协议版本号、生成的一个随机数、以及客户端支持的加密方法。</strong></p>
</li>
<li>
<p><strong>第二步，服务器端接收到请求后，确认双方使用的加密方法、并给出服务器的证书、以及一个服务器生成的随机数。</strong></p>
</li>
<li>
<p><strong>第三步，客户端确认服务器证书有效后，生成一个新的随机数，并使用数字证书中的公钥，加密这个随机数，然后发给服务器。并且还会提供一个前面所有内容的 hash 的值，用来供服务器检验。</strong></p>
</li>
<li>
<p><strong>第四步，服务器使用自己的私钥，来解密客户端发送过来的随机数。并提供前面所有内容的 hash 值来供客户端检验。</strong></p>
</li>
<li>
<p><strong>第五步，客户端和服务器端根据约定的加密方法使用前面的三个随机数，生成对话秘钥，以后的对话过程都使用这个秘钥来加密信息。</strong></p>
</li>
</ol>
<p><strong>tips：TLS是SSL的标准化后的产物</strong><br /><strong>有1.0 1.1 1.2三个版本，默认使用1.0</strong><br /><strong>TLS1.0和SSL3.0几乎没有区别</strong></p>