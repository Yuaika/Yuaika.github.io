---
layout:     post
title:     MIT Missing Semester 笔记
subtitle:   
date:       2022-04-15
author:     BY Yuaika
header-img: img/post-bg-debug.png
catalog: true
tags:
    - tool
---

### MIT Missing Semester 笔记

> Shell Tools and Scripting

- 使用通配符?，*；使用花括号{}展开
- 定位shell/bash脚本的工具：shellcheck
- man命令提供的信息过于详细，使用TLDR代替

- source加载.sh文件后可直接使用在.sh文件中定义的函数
- 使用管道将标准输入作为参数，使用xargs将标准输入转化为命令行参数

> Data Wrangling

- [配置ssh连接会话复用免密码登录](https://www.cnblogs.com/int32bit/p/5384641.html)；ssh使用单引号在远程机器上执行操作
- 使用sed对文本内容进行编辑
- 正则表达式，[regex debugger](https://regex101.com/r/qqbZqh/2)能帮助我们理解正则表达式，使用“捕获组”来保留内容
- awk是一种善于处理文本的编程语言

> Command-line Environment

- alias设置别名，比如简化长命令
- 使用版本控制系统管理配置文件，用脚本将配置文件符号链接到需要的位置
- 注意配置文件的可移植性

> Debug and Profiling

- 打印与日志；pdb，gdb，lldb等调试工具
- 性能分析：计时，CPU，内存（valgrind），系统事件分析（perf），火焰图
- 资源监控，基准测试（hyperfine）
