# 像素格式

帧缓冲由二维像素点组成，帧缓冲的长和宽的成绩代表像素点总数，也叫**分辨率**。

## PixelFormat

在 RFB 协议中，使用 16 字节结构体 PIXEL_FORMAT 描述像素格式。

```
 +--------------+--------------+-----------------+
 | No. of bytes | Type [Value] | Description     |
 +--------------+--------------+-----------------+
 | 1            | U8           | bits-per-pixel  |
 | 1            | U8           | depth           |
 | 1            | U8           | big-endian-flag |
 | 1            | U8           | true-color-flag |
 | 2            | U16          | red-max         |
 | 2            | U16          | green-max       |
 | 2            | U16          | blue-max        |
 | 1            | U8           | red-shift       |
 | 1            | U8           | green-shift     |
 | 1            | U8           | blue-shift      |
 | 3            |              | padding         |
 +--------------+--------------+-----------------+
```

- bits-per-pixel: 描述单个像素的位数，位数越大，色彩越丰富。只支持[8|16|32]
- depth: 色深，像素中表示色彩的位数
- big-endian-flag: 多字节像素的字节序，非零即打断
- true-color-flag: 1 表示真彩色，pixel 表示颜色；0 表示调色板，pexel 表示颜色颜色表中的位置
- -max/-shift: 获取红蓝绿三色的位移量和长度，max=2^N-1,N是颜色的位数

```
 BigEndian:    Blue Shift       Green Shift         Red Shift
                   │                 │                 │
                   ▼                 ▼                 ▼
┌──────────────────┬─────────────────┬─────────────────┐
│     BLUE MAX     │    GREEN MAX    │     RED MAX     │
└──────────────────┴─────────────────┴─────────────────┘
```

> bits-per-pixel 必须大于或等于 depth