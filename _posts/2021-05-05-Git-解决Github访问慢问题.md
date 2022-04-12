---
layout:     post
title:     Git学习
subtitle:   Github访问问题
date:       2021-05-05
author:     BY Yuaika
header-img: img/post-bg-debug.png
catalog: true
tags:
    - Markdown
    - Git
---
# **解决Github访问慢的问题**

1.初始情况

    ping github.com
    正在 Ping github.com [192.30.253.112] 具有 32 字节的数据:
    请求超时。
    请求超时。
    请求超时。
    请求超时。

2.原因：Github访问需要通过DNS寻址完成，经过层层寻址需要消耗大量的时间。

3.解决思路：直接访问Github的主域名和子域名的IP地址

域名解析网站：https://www.ipaddress.com/

在输入框中输入 `github.com` 域名后开始解析该域名的相关信息,不仅找到了域名对应的 `ip` 地址还查询到相关网站的域名信息。

![](https://github.com/Yuaika/Yuaika.github.io/blob/master/img/b5hwng1q1e.png)

DNS查询网站：http://tool.chinaz.com/dns/?type=1&host=github.com&ip=

在上述网站中输入子域名，找到TTL值最小的响应IP。

将这些IP地址和对应的子域名填入C:\Windows\System32\drivers\etc\hosts文件中

    #IP地址 对应的子域名
    52.74.223.119  github.com
    69.171.235.101 github.global.ssl.fastly.net
    52.74.223.119 gist.github.com
    13.250.162.133 codeload.github.com
    185.199.108.153 desktop.github.com  
    185.199.108.153 guides.github.com   
    185.199.108.153 blog.github.com 
    140.82.113.18 status.github.com   
    185.199.108.153 developer.github.com    
    185.199.108.153 services.github.com 
    192.30.253.175 enterprise.github.com   
    34.195.49.195 education.github.com    
    185.199.108.153 pages.github.com    
    34.196.237.103 classroom.github.com

4.最终情况

    ping github.com
    正在 Ping github.com [52.74.223.119] 具有 32 字节的数据:
    来自 52.74.223.119 的回复: 字节=32 时间=96ms TTL=39
    来自 52.74.223.119 的回复: 字节=32 时间=96ms TTL=39
    来自 52.74.223.119 的回复: 字节=32 时间=96ms TTL=39
    来自 52.74.223.119 的回复: 字节=32 时间=97ms TTL=39




## Reference：

https://cloud.tencent.com/developer/article/1426844



