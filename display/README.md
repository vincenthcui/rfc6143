# 显示

RFB 协议通过网络向用户展示界面。

## 帧缓冲

像名字 Remote Framebuffer 说明的那样，RFB 工作在帧缓冲（Framebuffer）层，模拟计算机视频输出设备。
帧缓冲区域像像图片文件中的位图，通过像素矩阵说明连续区域的色彩。

> 帧缓冲 = 色彩 * 分辨率矩阵

常见的，分辨率等于像素宽度 * 像素高度，总量为像素总数
对于单个像素的色彩来说，色彩值常以8位、16位、32位真彩色格式存储，位数越多，色彩对比度越大，图像也就越”真实”。