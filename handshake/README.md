# 握手

RFB 协议有四个阶段：

```mermaid
graph LR
    subgraph 握手
        protocol[协议握手] --> auth[认证] --> initial[初始化]
    end    
    initial --> transfer(数据交互)
    transfer --> transfer
```