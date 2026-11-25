# iChat — Qt 6 QML + C++ Network Chat Application

[中文版](#中文版) | [English Version](#english-version)

---

<a id="中文版"></a>

# 中文版

## 01 QT6 QML 高仿QQ iChat 网络聊天软件简介【QML与C++联合开发 准企业级软件架构】

> 项目：QT6 QML 与 C++ 联合开发 聊天软件 iChat｜整理日期：2026-11-22｜作者：瑞丰

---

### 一、项目简介

**iChat** 是基于 **QT6 QML + C++20** 开发的网络聊天软件，采用 **CMake** 构建、**vcpkg** 管理第三方库，覆盖客户端 UI、后台进程、服务端与公共组件库，适合有一定QML和C++基础，深入 **QML 与 C++ 联合开发、RPC 异步请求/响应/通知、网络通信、后台进程与高性能服务端开发，提升企业级软件系统架构设计水平**。

项目包含：

- **App UI**：QML 客户端 UI 进程
- **Host**：客户端后台进程
- **AuthServer**：服务端
- **Lib 动态库**：Auth、Core、model、proto、net、ipc、rpc、QianControl、RelaxControl、QuickFuture等组件

ichat 网络聊天软件功能免费体验：[ichat app体验](https://ichat.relaxwalk.com/downloads/ichat-release-20261122-1.0.0.7z)

欢迎大家进Q群交流： 1007976325

本专栏将对下面重点技术进行详细讲解，每个重点知识提供全部源码参考。

---

### 二、技术栈与开发环境

| 项目           | 说明                        |
| ------------ | ------------------------- |
| 开发语言         | QT6 QML（UI）+ C++20（业务逻辑）  |
| 项目构建         | CMake                     |
| 第三方库管理       | vcpkg                     |
| Windows 编译环境 | Win11：VS2026 / Qt Creator |
| Linux 编译环境   | GCC13                     |

**主要第三方依赖**：plog 日志、asio 消息循环、protobuf 序列化、openssl 加密、sqlite3 客户端数据库、libmariadb、libpng 图形验证码、librdkafka 消息队列、drogon HTTP/WebSocket、curl 邮件发送、hiredis 缓存、jsoncpp / nlohmann-json、brotli、c-ares、ffmpeg 语音消息与录音转存等。

---

### 三、ichat项目特点

#### 1. QT6 QML UI 开发，飞一般的感觉

- 受够了在C++源码中设置各种样式的苦，转QML的UI开发带来各种好处比如：UI开发与业务逻辑分离，UI开发因为QML的强大变得轻而易举，下面是部分列举
- 无边框窗口，自定义最小化 / 最大化 / 关闭
- 顶部与左侧拖动窗口
- 左中右三分屏：左侧固定，中间有限宽度调整，右侧无限扩展
- 左侧导航与中间、右侧窗口联动
- 树形展示好友分组、分组好友列表，支持展开 / 折叠
- 自定义可拖动对话框
- QML 自定义常用按钮 / 图标 / 原型头像
- ListView 自定义展示各类消息：文件、文本、语音、视频、图片
- 在 ichat-ui 纯UI基础上进一步优化，QML与 C++ 联合开发模式优化较多

#### 2. QML 与 C++ 联合开发，轻而易举

初学者对QML的UI如何与C++的数据模型，函数调用，状态更新，数据结构共享等比较难理解和应用，下面是部分举例，专栏将对这些重点特性进行源码举例介绍

- 完整的cmake项目构建和编译技术，windows和linux下的编译注意

- 公共组件模块化编译为动态库

  - 只有C++源码的动态库
  - C++源码和qml组件的动态库
  - 动态库编译为插件与QML交互

- 封装 RPC 异步请求框架

  - 缓存请求队列
  - 注册响应回调处理
  - 处理服务器主动下发数据
  - 异步执行任务返回多参数
  - 响应超时处理

- 其他C++与QML交互应用

  - C++ 中创建 QML 窗口
  - 根据C++中状态切换QML页面
  - 页面状态、操作与 C++ 联动
  - C++ 中处理 QML 信号 / 槽
  - QML 中操作 C++ 异步返回各类型数据并展示结果
  - C++ 封装对象 / 枚举与 QML 共享使用
  - QAbstractListModel 封装：删除、插入、重置、修改 role、按 role 查找
  - 多 Model 共享数据：用户信息在好友分组、聊天导航、消息列表等多处共享，指针共享数据，一处修改多处同步刷新
  - 消息列表中消息选中 / 空白区域选中 / 取消选中的背景颜色处理
  - 拷贝消息，将消息块生成 HTML 添加到剪贴板
  - 输入框文本图片混合拷贝、粘贴
  - 输入框内容用 C++ 解析，每块后添加空行，与发送消息解析一致

#### 3. 后台进程Host 和高性能Server的设计模式

- 大量现代C++的更多应用
- 软件工程的设计模式更多实战
- 准企业级软件架构
- Windows 后台进程 Host 开发
- Windows 后台进程与 UI 程序分离的通信模式
- 后台进程启动检查程序完整性
- Host 与 Server 的 SRP 用户密码检验流出
- 客户端与服务器端protobuf消息通信定义/封装/动态库等
- 服务端 Event Loop 事件响应式高性能网络通信开发
- 服务端 MySQL 异步非阻塞，提高 Server 性能
- Redis / Kafka / MySQL 等操作封装
- 图形验证码 / Email 验证码
- 事件响应 net 组件封装
- 基于 Event Loop 的线程、线程池
- Host 与 Server 通信加密数据封装
- App 与 Host 进程通信 IPC 组件封装
- 可重写秘钥加密算法

---

### 本专栏适合的人群

- 有一定C++和QT开发经验
- 需要学习现代C++的更多应用
- 需要在软件工程的设计模式更多实战
- 掌握更优的企业级软件架构
- 需要掌握QT6 QML和C++联合开发优秀的桌面应用软件架构
- 需要学习QT6 C++开发Debug / Release 编译/和发布流程
- 希望深入学习高性能服务端、后台进程、IPC、网络通信机制等

---

<a id="english-version"></a>

# English Version

## iChat — A QQ-Style Network Chat Application Built with Qt 6 QML and C++

> Project: **iChat** — a network chat application developed with **Qt 6 QML + C++20**.  
> Last updated: 2026-11-22  
> Author: Ruifeng

---

### 1. Project Overview

**iChat** is a network chat application built with **Qt 6 QML + C++20**, using **CMake** for build configuration and **vcpkg** for third-party dependency management. It covers the client UI, background process, server, and shared component libraries.

It is suitable for developers with some QML and C++ experience who want to go deeper into **QML/C++ integrated development, RPC asynchronous request/response/notification, network communication, background process development, and high-performance server development**, and improve their enterprise-level software architecture design skills.

The project includes:

- **App UI**: QML client UI process
- **Host**: client background process
- **AuthServer**: server
- **Lib shared libraries**: Auth, Core, model, proto, net, ipc, rpc, QianControl, RelaxControl, QuickFuture, and other components

Free trial of the iChat network chat application:  
[iChat app trial](https://ichat.relaxwalk.com/downloads/ichat-release-20261122-1.0.0.7z)

This series explains the key technologies in detail and provides full source code references for each key topic.

---

### 2. Tech Stack and Development Environment

| Item                              | Description                            |
| --------------------------------- | -------------------------------------- |
| Language                          | Qt 6 QML (UI) + C++20 (business logic) |
| Build system                      | CMake                                  |
| Third-party dependency management | vcpkg                                  |
| Windows build environment         | Windows 11: VS2026 / Qt Creator        |
| Linux build environment           | GCC 13                                 |

**Main third-party dependencies**: plog logging, asio message loop, protobuf serialization, openssl encryption, sqlite3 client database, libmariadb, libpng image captcha, librdkafka message queue, drogon HTTP/WebSocket, curl email sending, hiredis cache, jsoncpp / nlohmann-json, brotli, c-ares, ffmpeg for voice messages and recording conversion/storage, etc.

---

### 3. Project Highlights

#### 3.1 Qt 6 QML UI Development — Fast and Flexible

Tired of setting all kinds of styles in C++ source code? Moving UI development to QML brings many benefits, such as separating UI development from business logic and making UI development much easier thanks to QML's power.

Examples include:

- Frameless window with custom minimize / maximize / close buttons
- Drag the window from the top and left areas
- Three-pane layout: fixed left pane, adjustable middle pane width, and infinitely expanding right pane
- Left navigation synchronized with the middle and right panes
- Tree view for friend groups and group member lists, with expand / collapse support
- Custom draggable dialogs
- Custom QML buttons, icons, and placeholder avatars
- ListView-based display for various message types: files, text, voice, video, and images
- Further optimized QML + C++ development model based on the pure UI version of ichat-ui

#### 3.2 QML + C++ Integrated Development Made Easy

Beginners often find it difficult to understand and apply how QML UI interacts with C++ data models, function calls, state updates, and data structure sharing. This series provides source code examples for these key features.

Highlights include:

- Complete CMake project build and compilation setup, including Windows and Linux build notes
- Modular compilation of shared components into dynamic libraries:
  - C++-only dynamic libraries
  - Dynamic libraries containing both C++ source code and QML components
  - Dynamic libraries compiled as plugins that interact with QML
- Wrapped RPC asynchronous request framework:
  - Cached request queue
  - Registered response callback handling
  - Handling of server-initiated push data
  - Asynchronous task execution with multiple return parameters
  - Response timeout handling
- Other C++ and QML interaction applications:
  - Creating QML windows from C++
  - Switching QML pages based on C++ state
  - Linking page state and actions with C++
  - Handling QML signals / slots in C++
  - Operating on asynchronous C++ return data of various types in QML and displaying results
  - Exposing C++ objects / enums for shared use with QML
  - QAbstractListModel wrapper: delete, insert, reset, modify roles, and find by role
  - Multi-model data sharing: user information is shared across friend groups, chat navigation, message lists, etc., using shared pointers so that one modification refreshes all related views
  - Background color handling for selected messages, blank-area selection, and deselection in the message list
  - Copying messages and generating HTML message blocks for the clipboard
  - Mixed text and image copy/paste in the input box
  - Parsing input box content in C++ and adding a blank line after each block, consistent with sent message parsing

#### 3.3 Design Patterns for the Host Background Process and High-Performance Server

- Extensive use of modern C++
- More practical applications of software engineering design patterns
- Near-enterprise-grade software architecture
- Windows background process Host development
- Communication model separating the Windows background process from the UI application
- Startup integrity check for the background process
- SRP user password verification flow between Host and Server
- Protobuf message communication definition / wrapping / dynamic libraries between client and server
- Event-loop-based high-performance network communication on the server
- Asynchronous non-blocking MySQL access to improve server performance
- Wrappers for Redis / Kafka / MySQL operations
- Image captcha / Email captcha
- Event-driven net component wrapper
- Event-loop-based threads and thread pool
- Encrypted data wrapper for Host-Server communication
- IPC component wrapper for App-Host process communication
- Overridable key encryption algorithm

---

### 4. Who Is This For?

- Developers with some C++ and Qt development experience
- Developers who want to learn more modern C++ applications
- Developers who want more practical experience with software engineering design patterns
- Developers who want to master better enterprise-level software architecture
- Developers who want to master excellent desktop application architecture using Qt 6 QML and C++ integration
- Developers who want to learn Qt 6 C++ Debug / Release build and release workflows
- Developers who want to dive deeper into high-performance servers, background processes, IPC, and network communication mechanisms
