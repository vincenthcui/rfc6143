# 镜像编码 Copy Rect

CopyRect 指示客户端，从已有帧缓冲区域复制到新区域。这种编码常用于窗口拖动、页面滚动等场景。

报文只说明起始坐标，区域的长度和宽度由客户端发送的 FramebufferUpdateRequest 报文隐式定义。

```
+--------------+--------------+----------------+
| No. of bytes | Type [Value] | Description    |
+--------------+--------------+----------------+
| 2            | U16          | src-x-position |
| 2            | U16          | src-y-position |
+--------------+--------------+----------------+
```

- src-x-position/src-y-position: 源图像的起点坐标

> TODO: 多 FUR 时如何处理？