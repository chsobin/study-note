# MySQL配置文件

1. 二进制日志文件 log-bin

   用于主从复制

2. 错误日志 log-err

   默认关闭，记录严重的警告和错误信息，每次启动和关闭的详细信息

3. 查询日志

   慢查询日志

4. 数据文件

- frm文件 存放表结构
- myd文件  存放表数据
- myi文件 存放表索引



# MySQL架构

1. 连接层：为请求做连接处理，授权认证，安全等
2. 服务层：主要提供，查询解析、分析、优化、缓存以及内置函数，跨存储引擎功能（存储过程、视图、触发器）
3. 引擎层：存储引擎层，负责数据的存储和提取
4. 存储层：文件系统



# 存储引擎

- **查看所有存储引擎**

```shell
show engines;
```

- **InnoDB与MyISAM对比**

| 对比项 | MyISAM                                                 | InnoDB                                                       |
| ------ | ------------------------------------------------------ | ------------------------------------------------------------ |
| 主外键 | 不支持                                                 | 支持                                                         |
| 事务   | 不支持                                                 | 支持                                                         |
| 行表锁 | 表锁，即使操作一条记录也会锁住整个表，不适合高并发操作 | 行锁，操作时只锁住一行，适合高并发操作                       |
| 缓存   | 只缓存索引，不缓存真实数据                             | 不仅缓存索引还要缓存真实数据，对内存要求高，而且内存大小对性能有决定性影响 |
| 表空间 | 小                                                     | 大                                                           |
| 关注点 | 性能                                                   | 事务                                                         |



