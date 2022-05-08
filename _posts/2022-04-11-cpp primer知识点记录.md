---
layout:     post
title:     cpp primer知识点记录
subtitle:   
date:       2021-04-11
author:     BY Yuaika
header-img: img/post-bg-debug.png
catalog: true
tags:
    - C++
---

# C++ Primer

> 对C++ Primer的部分内容的记录

0.gcc编译cpp程序的过程

https://www.cnblogs.com/burner/p/gcc-bian-yiccde-si-ge-guo-cheng.html



1.一些关键字

constexpr类型：由编译器来验证变量的值是否为一个常量表达式

类型别名：typedef，using

类型推导：auto，decltype

预处理：#ifdef，#ifndef，#endif，#define



2.命名空间

namespace

C++11引入内敛的命名空间，用途：区分多个不同版本的代码

使用using声明便捷使用命名空间的成员，也可使用别名，注意避免冲突。



3.跳转语句

break语句负责终止离它最近的while，do while，for或switch语句，并从这些语句之后的第一条语句开始继续执行。

continue语句终止最近的循环中的当前迭代并立即开始下一次迭代。

goto语句能无条件跳转到同一函数内的另一条语句，不要使用。

return语句终止当前正在执行的函数并将控制权返回到调用该函数的地方。能为返回类型是非常量引用的函数的结果赋值。



4.异常处理

try   throw catch



5.类型处理

static_cast，const_cast，reinterpret_cat，dynamic_cast

static_cast改变底层const之外的属性，const_cast只能改变底层const。



6.调试帮助（6.5.3节，215页）

assert与NDEBUG



7.lambda表达式

基本形式：[capture list] (parameter list) -> return type { function body }，其中参数列表与返回类型可以省略。

lambda表达式的捕获方式分为：值捕获，引用捕获与隐式捕获。

```
例子：
(1) 查找第一个长度大于等于sz的元素
auto wc = find_if(words.begin(), words.end(), [sz](const string &a){return a.size()>=sz;});
(2) 使用for_each函数 
for_each(wc, words.end(), [](const string &a){cout<<a<<" ";});
(3) 捕获this指针
std::sort(v.begin(), v.end(), [this](auto a, auto b){ return this->cmp(a, b);});
```

lambda表达式的使用场合：只在一两个地方使用的简单操作，需要捕获局部变量的场合。

如果要为函数提供局部变量，需要借助bind函数。

bind函数接受一个可调用对象，生成一个新的可调用对象。

bind的调用形式：auto newCallable = bind(callable, arg_list);

arg_list中的参数可能包括占位符_n，在命名空间std::placeholders中定义。



8.类的设计

8.1.动态内存管理类

new将内存分配与对象构造组合在了一起，delete将对象析构和内存释放组合在了一起。

为将内存分配与对象构造分离，使用标准库allocator类。

一个动态内存管理类（如13.5节，465页）定义三个指针成员指向其元素所使用的内存：

- elements，指向分配的内存中的首元素
- first_free，指向最后一个实际元素之后的位置
- cap，指向分配的内存末尾之后的位置

需要的工具函数：

- alloc_n_copy会分配内存，拷贝一个给定范围中的元素
- free会销毁构造的元素并释放内存
- check_n_alloc会保证至少有容纳一个新元素的空间
- reallocate在内存用完时会分配新的内存；在重新分配内存的过程中使用移动而不是拷贝元素

8.2.拷贝控制

- 拷贝构造函数，拷贝赋值运算符，析构函数。


```
使用default与delete：
struct NoCopy{
	NoCopy() = default;
	NoCopy(const NoCopy &) = delete;
	NoCopy& operator=(const NoCopy &) = delete;
	~NoCopy() = default;
}
```

- 注意引用计数与swap函数的设计。


- 移动构造函数，移动赋值运算符。

使用std::move将左值转化为右值。

在一些情况下对象拷贝后就立即销毁了，这个时候要使用移动操作。

```
为StrVec类定义移动构造函数,使用noexcept告诉标准库移动构造函数可以安全使用
StrVec::StrVec(StrVec &&s) noexcept
:elements(s.elements), first_free(s.first_free), cap(s.cap)
{
	s.elements=nullptr; s.first_free=nullptr; s.cap=nullptr;
}
```

8.3

- 常量对象，以及常量对象的引用或指针都只能调用常量成员函数

```
重载下标运算符时需要定义两个版本：
std::string& operator[](std::size_t n) { return elements[n]; }
const std::string& operator[](std::size_t n) const { return elements[n]; }
```

- 函数调用运算符

```
struct absInt
{
	int operator() (int val) const {
		return val<0 ? -val : val;
	}
};

int i= -42; absInt absObj;
int abs_i = absObj(i);
```

编译器会将lambda表达式翻译成一个未命名类的未命名对象。

8.4 OOP

- 继承，多态，抽象基类
- 多重继承，虚继承

8.5 模板

- 可变参数模板
- 模板特例化



9.其它

- 使用tuple组合一系列数据
- 使用bitset处理二进制位
- 正则表达式regex
- C++程序不应该使用库函数rand，而应该使用default_random_engine类和恰当的分布类对象
- 重载new与delete
