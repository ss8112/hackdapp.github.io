---
title: C++基础语法（EOS完全开发指南）
categories: EOS完全开发指南
url: eosdev_cplus_basic
tags:
  - EOS完全开发指南
  - C++导读
  - EOS合约开发教程
keywords:
  - EOS完全开发指南
  - C++导读
  - EOS合约开发教程
abbrlink: 7231
date: 2019-01-28 18:16:50
toc: true
---
`Author: zhangliang | WeChat: rushking2009 | Mail: zhangliang@cldy.org`

```c
/* filename: myapp.cpp
   date: 2019-01-28 3:06 PM
   auth: zhangliang<zhangliang@cldy.org> */

#include <iostream> //定义头文件
#include <stdlib.h>

int main()
{
    using namespace std;    //命令空间, 简化后续变量或方法调用。e.g. std::string 等同于 string

    string msg = "hi, my first dapp"; //定义变量

    cout << msg <<endl; //打印字符串
}

//tryit: http://tpcg.io/Tulum1
```

以上代码便是C++最简单可运行的最小示例。基本包含了在程序结构中所必须的一些语言特性。

根据上述程序结构，我们可以大致将它拆分成五部分内容：

<!-- more -->

## 1. `#include <iostream>`

头文件定义主要用于引用第三方函数库，通过调用第三方函数可以减少开发代码量，提高开发效率，同时也避免了不必要的重复造轮子。

比如：通过引用`<cmath>`库，可以帮助我们快速使用里面的函数进行一些数学运算。

![函数列表](https://ws3.sinaimg.cn/large/006tNc79ly1fzmer35re6j30l30j6myt.jpg)

所以，后续我们需要学会便是如何查阅C++文档库，不断积累与完善对于第三方标准库的方法学习与理解。

## 2. `int main()`

`main`函数区别于其它普通函数之处在于: main函数默认被系统定义为应用入口调用方法。除此之外，与其他函数无任何区别。

```c
#include <iostream>
#include <stdlib.h>

using namespace std;

string sayHi(string username)
{
    return string("hi, ").append(username).append("!");
}

int main()
{
    cout << sayHi("www.hackdapp.com") << endl;
}
//tryit: http://tpcg.io/uHUkzy
```

函数定义，其实对于所有编程语言的定义方式大致相同, 都可以表现为以下形式

```c
<返回类型|void> 方法名(参数定义1, 参数定义2，参数定义...)
{
    //do some stuff
    return <返回数据>
}
```

如果你之前已经在使用其他编程语言，那么应该对于C++其实也可以很好的理解它的程序结构。

注： 在后续的第二部分，我们会详细介绍函数的多种定义及使用方式，包括形参实参、重载以及虚函数等。

## 3. `string message = "hi, my first app"`

变量定义，在程序开发过程，往往需要定义一些临时变量，用于存储在数据逻辑处理过程所必须的临时存储。

而变量的类型，主要分为字符、整型，长/短整型、单精度、双精度、布尔类型以及字符串。
我们在实际应用场景中，需要明确了解与知道这些基础数据类型的定义及边界范围，比如，无符号整型、单精度。

尤其是对数字类型的字段，如果不了解其边界范围，很可能会导致运算溢出等问题，特别是在合约开发过程中，数字溢出很可能导致的便是相当大的经济损失。

换个角度讲，合理的使用变量类型，也可能在一定程序中节省资源的浪费。因为在EOS合约中存储数据是需要消耗资源的。

另外，对于变量的名称定义，其名称只能是由数字、字母以及下划线组成且不可能以数字开头，而且根据不同平台，对于名称的长度其实也是存在限制的。

## 4. `cout << msg <<endl`

`cout`是`iostream`函数库中的一个流数据输出函数，一般用于在程序调用过程向控制台输入一些调试信息；与此对应的是`cin`, 用于接收输入数据流。

不过, 在EOS合约中无法调用此函数。举而代之的是，EOSLIB库自己封装的`print`函数.

## 5. `//单行注解 or /*多行注解*/`

在程序开发过程，往往需要通过语言描述某个代码文件所要实现的整体功能或者某个函数的功能、参数及约束说明。这时候就需要用到注解。

而注解同样也所有的编程语言中也大致相同，一般分为单行注释与多行注释。

单行注释适用于短小的描述某一行运行逻辑；而多行注释多用于描述函数说明以及文件功能说明。

----
`注：` 在教程中如出现不易理解或存在错误的问题🐛，欢迎评论留言！

