# 简介

## 什么是 RFB

RFB(Remote Framebuffer Protocol) 远程帧缓冲协议，是一种允许用户通过网络连接控制远端计算机的七层网络协议。在 RFB 协议中，用户通过本地鼠标、键盘输入，经由远端计算机计算后，将图形用户界面（GUI）回传本地进行输出。

![RFB示意图](http://babeler-1251731700.cos.ap-shanghai.myqcloud.com/2021-08-07-085929.png)

### VNC 软件

VNC (Vitual Network Computing) 是通过 RFB 协议实现屏幕画面分享和远程操作的应用软件，是 RFB 协议的具体应用，是远程桌面软件的一种。VNC 和 RFB 的关系类似 Chrome 和 HTTP，RFB 和 HTTP 是协议，VNC 和 Chrome 是具体实现。

### 面临的问题

根据 RFB 协议的定义，我们不难看出，RFB 协议主要解决三类问题

1. 传输鼠标、键盘输入的控制信号
2. 传输用户图形界面
3. 弱网络环境条件下的稳定传输

## RFB 协议版本

RFB 协议有三个公开版本，分别是 3.3、3.7和3.8，3.8 是稳定版本。

版本 | 发布时间 | 协议差异
:---: | :---: | :---:
Version 3.3 | 1998-01 | 服务器单向认证
Version 3.7 | 2003-8-12 | 关闭连接时返回原因
Version 3.8 (Final) | 2010-11-26 | -

三个版本只在协议的握手阶段和初始化阶段存在差异，在数据流交换阶段保持一致。

### RFB 协议的拓展

第三方 VNC 服务端和客户端拓展了 3.8 版本协议，提供更多的认证方式，优化传输效率。

- Tight
- RealVNC
- Ultra
- VMWare

## RFB 的发展历史

- 2002 年，AT&T 关闭其位于英国剑桥的 Olivetti 研究实验室。

- 2002 年，VNC 技术发明者 Tristan Richardson 合伙成立 RealVNC 公司，向商业公司提供企业级远程访问软件。

- 2003年8月12日，Richardson 公开 RFB 协议的 3.7 版本。

- 2010年11月26日，发布稳定协议版本 v3.8。

> RFB 是 IEEE 公开的开源通信协议，但 RFB® 和 VNC® 是 RealVNC 公司的注册商标。