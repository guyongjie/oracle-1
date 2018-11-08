实验3：创建分区表
实验目的：
掌握分区表的创建方法，掌握各种分区方式的使用场景。

实验内容：
本实验使用3个表空间：USERS,USERS02,USERS03。在表空间中创建两张表：订单表(orders)与订单详表(order_details)。
使用你自己的账号创建本实验的表，表创建在上述3个分区，自定义分区策略。
你需要使用system用户给你自己的账号分配上述分区的使用权限。你需要使用system用户给你的用户分配可以查询执行计划的权限。
表创建成功后，插入数据，数据能并平均分布到各个分区。每个表的数据都应该大于1万行，对表进行联合查询。
写出插入数据的语句和查询数据的语句，并分析语句的执行计划。
进行分区与不分区的对比实验。

1.创建主表和从表

用户名：NEW_USER_LMQ; 设置主表主键 order_id, 从表外键 order_id; 主表的分区策略是按照日期范围--2016，2017，2018，分别对应分区USERS, USERS02,USERS03。 在主表orders和从表order_details之间建立引用分区 在NEW_USER_WTS用户中创建两个表：orders（订单表）和order_details（订单详表），两个表通过列order_id建立主外键关联。orders表按范围分区进行存储，order_details使用引用分区进行存储。

![运行结果](https://github.com/liumengqi77/oracle/blob/master/text3/1.png)
![运行结果](https://github.com/liumengqi77/oracle/blob/master/text3/2.png)

2.插入一万条数据
![运行结果](https://github.com/liumengqi77/oracle/blob/master/text3/3.png)
