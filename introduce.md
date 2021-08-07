# 协议介绍

## 什么是 RFB

RFB(Remote Framebuffer Protocol) 远程帧缓冲协议，是一种允许用户通过网络连接控制远端计算机的七层网络协议。在 RFB 协议中，用户通过本地鼠标、键盘输入，经由远端计算机计算后，将图形用户界面（GUI）回传本地进行输出。

![RFB示意图](http://babeler-1251731700.cos.ap-shanghai.myqcloud.com/2021-08-07-085929.png)

### 什么是 VNC

VNC (Vitual Network Computing) 是通过 RFB 协议实现屏幕画面分享和远程操作的应用软件，是 RFB 协议的具体应用，是远程桌面软件的一种。VNC 和 RFB 的关系类似 Chrome 和 HTTP，RFB 和 HTTP 是协议，VNC 和 Chrome 是具体实现。

~~为了保证协议的兼容性和性能，RFB 协议在设计时向上屏蔽操作系统差异（兼容绝大部分操作系统），面向弱网络环境进行设计。~~

### 远程控制协议

> TODO: 插图

### 面临的问题

- 控制流传输：鼠标、键盘
- 操作结果传输：图形界面
- 弱网络环境

### 解决方案和思考

## RFB 版本

RFB 协议有三个公开版本，分别是 3.3、3.7和3.8，3.8 是终版。

版本 | 发布时间 | 协议差异
:---: | :---: | :---:
Version 3.3 | 1998-01 | 服务器单向认证
Version 3.7 | 2003-8-12 | 关闭连接时返回原因
Version 3.8 (Final) | 2010-11-26 | -

三个版本只在协议的握手阶段和初始化阶段存在差异。

### RFB 协议的拓展

第三方 VNC 服务端和客户端拓展了 3.8 版本协议，提供更多的认证方式，优化传输效率。

- Tight
- RealVNC
- Ultra
- VMWare

## RFB 的发展历史

- 2002 年，AT&T 关闭其位于英国剑桥的 Olivetti 研究实验室。

- 2002 年，VNC 技术的原始发明者 Tristan Richardson 合伙成立 RealVNC 公司，向商业公司提供企业级远程访问软件。

- 2003年8月12日，Richardson 公开 RFB 协议的 3.7 版本。

> 协议 3.8 版本由 RealVNC 公司的 Tristan Richardson 和 John Levine 起草，RFB® 和 VNC® 是 RealVNC 公司的注册商标。