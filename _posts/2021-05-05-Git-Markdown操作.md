---
layout:     post
title:     Markdown学习
subtitle:   基本语法
date:       2021-05-05
author:     BY Yuaika
header-img: img/post-bg-debug.png
catalog: true
tags:
    - Markdown
---
输入[TOC]即可产生菜单，菜单会自动更新

[TOC]

# **Markdown基本语法**



## 一.字体加粗，倾斜，下划线，文字引用

加粗： `Ctrl + B`,  **jojo**

字体倾斜 ：`Ctrl+I`,  *jojo*

下划线：`Ctrl+U`,  <u>jojo</u>

> 文字引用 ：`Ctrl+Shift+Q`



## 二.多级标题，有序列表，无序列表

多级标题： `Ctrl + 1~6`

有序列表：`Ctrl + Shift + [`

1.
2.
3.


无序列表：`Ctrl + Shift + ]`

- 
- 



## 三.图片，公式，表格

插入图片： `Ctrl + Shift + I`

![](https://ak.hypergryph.com/special/2nd-anniversary/assets/01.ae48f28d.jpg)

插入公式： `Ctrl + Shift + M`

$$
E=mc^2
$$
插入链接： `Ctrl + K`

超链接：[my blog](yuaika.github.io)

公式支持 **LaTeX** 编辑显示支持，访问 [MathJax ](http://meta.math.stackexchange.com/questions/5020/mathjax-basic-tutorial-and-quick-reference)参考更多使用方法。

推荐一个常用的数学公式在线编译网站：https://private.codecogs.com/latex/eqneditor.php

插入表格：`Ctrl+T`

|  1   |  1   |  1   |
| :--: | :--: | :--: |
|  1   |  1   |  1   |
|  1   |  1   |  1   |



## 四.代码

``表示行内代码块

`行内代码块`

使用四个空格缩进表示代码块

    #include<iostream>
    int main(){
    
    }



