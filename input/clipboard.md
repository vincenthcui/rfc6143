# 剪贴板

复制粘贴是双向事件，可以由客户端向服务端复制，也可以由服务端向客户端复制。

## 协议报文

复制剪贴板的报文如下：

```
  +--------------+--------------+--------------+
  | No. of bytes | Type [Value] | Description  |
  +--------------+--------------+--------------+
  | 1            | U8 [3/6]     | message-type |
  | 3            |              | padding      |
  | 4            | U32          | length       |
  | length       | U8 array     | text         |
  +--------------+--------------+--------------+
```

- message-type: 消息类型，客户端是 `0x6`，服务端是 `0x3`
- length: 文本长度
- text: 复制粘贴的文本，长度由 length 限制

协议有几点限制

- 只支持 ISO 8859-1 (Latin-1) 字符集
- 使用单独换行符 `0x0a`，不应该使用回车符 `0x0d`

## 拓展多字节

RFB 3.8 限制 CutText 消息只能传输 Latin-1 字符，社区通过 `Extended Clipboard Pseudo-Encoding` 伪编码拓展协议。
此协议需要客户端和服务端软件同时支持。报文如下：

```
  +--------------+--------------+--------------+
  | No. of bytes | Type [Value] | Description  |
  +--------------+--------------+--------------+
  | 1            | U8 [3/6]     | message-type |
  | 3            |              | padding      |
  | 4            | S32          | length       |
  | 4            | U32          | text-type    |
  | length-4     | U8 array     | text         |
  +--------------+--------------+--------------+
```

- length: 数据类型由 U32 改为 S32。首bit是标志位，0 表示传递原始 Latin-1 消息，1 表示传递 unicode。abs(length) 表示消息长度。
- text-type: 消息类型，支持文本、富文本、html 等消息类型
- text: 消息头部增加4字节，表示复制的消息类型

text-type 值的含义如下

| Bit	| Name | Description |
|-|-|---|
| 0	| text | UTF-8 编码，以 `\r\n` 为换行 |
| 1| rtf | 微软富文本格式 |
| 2	| html | 微软 HTML 格式 |
| 3	| dib | Microsoft Device Independent Bitmap |
| 4	| files | 文件，未实现 |
| 5-15| Reserved for future formats |
| 16-23	| Reserved |
| 24	| caps | 指示 text-type 的最大长度 |
| 25	| request | 强制对端传递剪贴板内容 |
| 26	| peek | 强制对端更新支持的 text-type |
| 27	| notify | peek 回包，返回支持的 text-type |
| 28	| provide | request 回包，返回粘贴板内容 |
| 29-31	| Reserved for future actions |