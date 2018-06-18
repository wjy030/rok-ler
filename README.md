# rok-ler
## 简介
* 分布式、队列模型消息中间件
* 实现业务消峰，分布式事务
* 底层通信由Netty NIO实现
* 3.X版本以后使用NameServer进行网络路由，支持消息失败重试机制
* 零拷贝，顺序写盘，支持亿级消息堆积能力
* 顺序消息，事务消息
## 核心概念
* Push Consumer：Consumer的一种，注册一个Listener接口，一旦收到消息，Consumer对象立刻回调Listener接口方法。
* Pull Consumer：Consumer的一种，通常主动调用Consumer的拉消息方法从Broker拉消息，主动权由应用控制。
* Producer Group：一类Producer的集合名称，这类Producer通常发送一类消息，且发送逻辑一致。
* Consumer Group：一类Consumer的集合名称，这类Consumer通常消费一类消息，且消费逻辑一致。
* Broker：消息跳转角色，负责存储消息，转发消息，（即mq本身），一般也称为Server,在JMS规范中称为Provider。
* 广播消费：publish/subscribe，每个订阅的consumer都会消费
* 集群消费：一个group中的consumer平均分摊消费消息
## 集群构建模型
* 单master模式 风险较大，一旦宕机整个服务不可用
* 多master模式 一个集群无slave，全是Master

> 优点：配置简单，宕机或重启维护对应用无影响

> 缺点：宕机期间，这台机器上
