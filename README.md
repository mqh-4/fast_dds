# fast_dds

##fast dds 基础

### dds 协议概述 ： dds（data distribution service）是omg组织定义的以数据为中心的发布-订阅工业级通信标准，核心标准是去中心化，无broker，节点自动发现，支持精细化Qos控制。

核心实体层级：

domainparticipant：   域参与者  同域内节点才能通信
topic ：   绑定话题名称和数据类型 是发布订阅的桥梁
publisher/subsciber：发布者 订阅者容器  管理一组datawrite datareader
datawrite/datareader：真正负责数据读写的端点

### 发现机制
自动发现是dds的核心能力   ：
     简单发现：
             参与者发现  ：  通过udp组播交换节点信息
             端点发现：  互相通告 datawrite/datareader的topic，类型，qos，匹配成功后建立链路
    静态发现：
             提前通过xml配置文件定义所有端点信息，节点启动直接加载，无需组播

### QoS策略  用于精准控制通信行为
            reliability可靠性 ：控制是否保证消息送达
            durability持久性 ： 新订阅者加入是否能收到历史数据
            history历史缓存  ：  端点缓存的历史数据条数
     
## fast dds 进阶

### 分区 ： 分区是publisher/subscriber级别的qos
