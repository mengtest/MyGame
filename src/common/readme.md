# 服务器和客户端通信协议

网络包LV格式：Length(长度) + Value(数据);长度（用两个字节表示）表示Value的长度。
即如果Value长度为10，则Len的值为10，整个网络包长度是12。  

## 客户端发送给服务器

2个字节（长度，Big-Endian 编码）+ 1个字节（服务id，即消息目的地）+ 2个字节（消息id，Little-Endian 编码）+ 消息体（protobuf序列化的包）

## 服务器发送给客户端

2个字节（长度，Big-Endian 编码）+ 1个字节（服务id，即消息原地址）+ 2个字节（消息id，Little-Endian 编码）+ 消息体（protobuf序列化的包）

## 目的地即服务模块

整套系统有大量模块组成，每个模块负责自己的事情，各自独立。当客户端发送消息请求时，要向服务器表明该请求是哪个模块。
现将服务ID定义如下（即上述协议中的【1个字节（服务id，即消息目的地）】）：
* 0  ：  未知服务
* 1  ：  登陆服务
* 2  ：  弹窗服务【大厅】
* 3  ：  签到服务【大厅】
* 4  ：  任务服务【大厅】
* 5  ：  活动服务【大厅】
* 6  ：  排行榜服务【大厅】
* 7  ：  商城服务【大厅】
* 8  ：  匹配服务【大厅】
* 9  ：  游戏服务【游戏】

···未完待续


