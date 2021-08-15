# 握手

RFB 协议有四个阶段：

```mermaid
graph LR
    subgraph 握手
        协议握手 --> 认证 --> 初始化
    end    
    初始化 --> transfer(数据交互)
    transfer --> transfer
```