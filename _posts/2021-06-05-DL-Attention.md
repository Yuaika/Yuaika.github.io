---
layout:     post
title:     Object Detection
subtitle:   CV注意力机制
date:       2021-06-05
author:     BY Yuaika
header-img: img/post-bg-debug.png
catalog: true
tags:
    - Deep Learning
    - Object Detection
---
# 一.通道注意力与空间注意力

> Squeeze-and-Excitation Networks

![](../img/SENet-1.png)

Instantiation

![](../img/SENet-2.png)



> CBAM: Convolutional Block Attention Module

Overview

<img src="../img/CBAM-1.png" style="zoom: 67%;" />

Sub module

<img src="../img/CBAM-2.png" style="zoom:67%;" />

Grad-Cam Visualization

<img src="../img/CBAM-3.png" style="zoom:67%;" />



> SKNet

自适应的选择卷积核

![](../img/SKNet.png)

> ECA-Net

选择邻近的k个通道做卷积

<img src="../img/ECANet.png" style="zoom:80%;" />



# 二. Nonlocal 

> Non-local Neural Networks

<img src="../img/NonlocalNN.png" style="zoom: 67%;" />



> Asymmetric Non-local Neural Networks for Semantic Segmentation

考虑到图像中的一些像素点比其他点更加重要。

用SPP来降低维度，N->S。

<img src="../img/APNB-1.png" style="zoom:67%;" />

<img src="../img/APNB-2.png" style="zoom:67%;" />



> Real-Time Semantic Segmentation With Fast Attention

Idea在Efficient Attention: Attention with Linear Complexities已经被提出。

快速的self-attention，还能扩展到Video语义分割中

核心思想：cos相似度代替softmax，改变self-attention的计算顺序

![](../img/FANet.png)



> GCNet: Non-local Networks Meet Squeeze-Excitation Networks and Beyond

结合SENet和Nonlocal，并简化。



应用：

> Non-locally Enhanced Encoder-Decoder Network for Single Image De-raining

将Nonlocal用于去雨。

> Efficient Image Super-Resolution Using Pixel Attention

像素级的注意力，CHW。





# 三.小目标识别

> Small Object Detection using Context and Attention

Extend ResNet-SSD with context and attention

<img src="../IMG/fa-ssd-1.png" style="zoom:80%;" />

Feature fusion module

<img src="../img/FA-SSD-2.png" style="zoom: 80%;" />



> HRDNet: High-resolution Detection Network for Small Objects

使用不同深度的网络处理不同分辨率的图像，然后用一个多尺度金字塔来融合



> MultiResolution Attention Extractor for Small Object Detection

对FPN的特征做Attention

![](../img/MRAE.png)

> IPG-Net: Image Pyramid Guidance Network for Small Object Detection



> Coordinate Attention for Efficient Mobile Network Design

宽度与高度上attention分离

> Polarized Self-Attention: Towards High-quality Pixel-wise Regression

使某个方向的特征保持高分辨率

https://zhuanlan.zhihu.com/p/392148142
