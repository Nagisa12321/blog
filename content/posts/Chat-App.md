---
title: "Chat App"
date: 2022-05-30T11:50:18+08:00
draft: false
---

# 为什么我要做一个聊天的APP
### ---- just for fun ...
这个app其实我想做的时间就挺久啦! 其实以前就做过一两个版本，刚学习语言那会，用的Java写的。这次刚好趁着实习结束，处理毕业事宜这段时间，系统性质的认真做一次！
这个认真的定义是什么？首先必须有铺垫！何谓铺垫，即是各种框架，包含自己手写的，在公司实习学会的，以及一些开源框架。做好这些铺垫的同时再开始APP的书写，方才能做到水到渠成的效果。

# APP的功能大致描述
初步的大局是分客户端和后台来做。大思路是采用HttpClient+httpServer维护一个无连接状态的服务器；后台语言暂定，客户端确定是C++&QT5来搭建，也是我实习接触的重点内容XD。

### 功能模块
大概会分为几个功能板块来做：登录，注册，找回密码；进入APP后的好友列表，私聊，群聊；具体细节待定

### 主要内容
1. 客户端框架采用MVVM，采用基于绑定编程。客户端MVVM层均用MAIN线程来编程，因此不存在多线程的各种问题。
2. 多线程部分，包括工作线程，数据库存取线程, HTTP监听线程等，这些会基于libevent来写，这部分还没学；还要边学边写XD
3. LOG框架有点想自己手写一个，目前已经有接口了，就是后续多线程部分处理好之后会自己整一个LOG线程，和MAIN线程进行一个分离XD。（B计划是直接采用外部开源库如spdlog等）
4. 与后台通信协议暂定HTTP或者HTTPS，这个会不会太重了有待评估。
5. 后台的主要功能还需要进一步思考

### 目前进展
```txt
t@jt-arch ~/Desktop/project/chat-app [master]
± % tree .                                                                                           !10011
.
├── app_header
│   ├── CMakeLists.txt
│   └── include
│       ├── mvvm_bind
│       │   ├── handle.h
│       │   └── props.h
│       └── namespace
│           ├── cppheader.h
│           └── namespace.h
├── build.sh
├── CMakeLists.txt
├── compile_commands.json -> ./build/compile_commands.json
├── controller
│   ├── CMakeLists.txt
│   ├── include
│   │   └── hello_controller.h
│   └── src
│       └── hello_controller.cc
├── log
│   ├── CMakeLists.txt
│   ├── include
│   │   └── logger.h
│   └── src
│       └── logger.cc
├── model
│   ├── CMakeLists.txt
│   ├── include
│   ├── src
│   └── view
│       ├── include
│       └── src
├── mvvm
│   ├── CMakeLists.txt
│   ├── include
│   │   ├── abstract
│   │   └── mvvm
│   │       ├── controller.h
│   │       ├── model.h
│   │       └── view.h
│   └── src
│       └── mvvm
│           ├── controller.cc
│           ├── model.cc
│           └── view.cc
├── README.md
├── third_party
│   └── CMakeLists.txt
├── variant
│   ├── CMakeLists.txt
│   ├── include
│   │   └── variant.h
│   └── src
│       └── variant.cc
└── view
    ├── app.cc
    ├── CMakeLists.txt
    ├── include
    │   ├── hello_view.h
    │   └── hello_widget.h
    ├── resources
    │   └── helloworld-transparent.png
    ├── resources.qrc
    └── src
        ├── hello_view.cc
        └── hello_widget.cc

30 directories, 35 files
```
目前完成了基于mvvm绑定的helloworld程序，进度还算可以；真正app写起来会跟后台一起开展；还是有点挑战性呢XD

## To Be Continue...