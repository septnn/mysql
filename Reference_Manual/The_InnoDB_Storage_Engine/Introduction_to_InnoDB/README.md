# 15.1 Introduction to InnoDB

*Update 2020-8-19 , By Dawei*

> 原文地址[MySQL 8.0 Reference Manual](https://dev.mysql.com/doc/refman/8.0/en/innodb-introduction.html)

- [TODO] [15.1.1 Benefits of Using InnoDB Tables](15.1.1 Benefits of Using InnoDB Tables.md)
- [TODO] [15.1.2 Best Practices for InnoDB Tables](15.1.2 Best Practices for InnoDB Tables.md)
- [TODO] [15.1.3 Verifying that InnoDB is the Default Storage Engine](15.1.3 Verifying that InnoDB is the Default Storage Engine.md)
- [TODO] [15.1.4 Testing and Benchmarking with InnoDB](15.1.4 Testing and Benchmarking with InnoDB.md)

InnoDB is a general-purpose storage engine that balances high reliability and high performance. In MySQL 8.0, InnoDB is the default MySQL storage engine. Unless you have configured a different default storage engine, issuing a CREATE TABLE statement without an ENGINE= clause creates an InnoDB table.

InnoDB是一种通用存储引擎，可兼顾高可靠性和高性能。在MySql 8.0，InnoDb是默认MySql存储引擎。除非你有一个不同的默认存储引擎配置，由一个`CREATE TABLE`没有`ENGINE=`条款的声明来创建一个`InnoDb`表。

## Key Advantages of InnoDB

- 其[DML](https://dev.mysql.com/doc/refman/8.0/en/glossary.html#glos_dml)操作遵循[ACID](https://dev.mysql.com/doc/refman/8.0/en/glossary.html#glos_acid)模型，并具有具有提交，回滚和崩溃恢复功能的事务，以保护用户数据。 有关更多信息，请参见[第15.2节“ InnoDB和ACID模型”](https://dev.mysql.com/doc/refman/8.0/en/mysql-acid.html)。

- 行级锁定和Oracle风格的一致读取可提高多用户并发性和性能。 有关更多信息，请参见[第15.7节“ InnoDB锁定和事务模型”](https://dev.mysql.com/doc/refman/8.0/en/innodb-locking-transaction-model.html)。

- InnoDB表将数据安排在磁盘上，以基于主键优化查询。 每个InnoDB表都有一个称为聚集索引的主键索引，该索引组织数据以最小化主键查找的I / O。 有关更多信息，请参见[第15.6.2.1节“聚集索引和二级索引”](https://dev.mysql.com/doc/refman/8.0/en/innodb-locking-transaction-model.html)。

- 为了保持数据完整性，InnoDB支持FOREIGN KEY约束。 使用外键检查插入，更新和删除操作，以确保它们不会导致不同表之间的不一致。 有关更多信息，请参见[第13.1.20.5节“外键约束”](https://dev.mysql.com/doc/refman/8.0/en/create-table-foreign-keys.html)。

### Table 15.1 InnoDB Storage Engine Features

|特性|支持|
|----|----|
| B-tree 索引|	Yes|
| 备份/时间点 恢复 (在服务器中实现，而不是在存储引擎中实现。)|	Yes|
| 集群数据库支持|	No|
| 聚簇索引|	Yes|
| 压缩数据|	Yes|
| 数据缓存|	Yes|
| 加密数据|	Yes (Implemented in the server via encryption functions; In MySQL 5.7 and later, data-at-rest| tablespace encryption is supported.)
| 外键支持|	Yes|
| 全文搜素索引|	Yes (InnoDB support for FULLTEXT indexes is available in MySQL 5.6 and later.)|
| 地理数据类型支持|	Yes|
| 地理索引支持|	Yes (InnoDB support for geospatial indexing is available in MySQL 5.7 and later.)|
| Hash 索引|	No (InnoDB utilizes hash indexes internally for its Adaptive Hash Index feature.)|
| 索引缓存|	Yes|
| 锁粒度|	Row|
| MVCC|	Yes|
| 副本支持 (Implemented in the server, rather than in the storage engine.)|	Yes|
| 存储限制|	64TB|
| T-tree 索引|	No|
| 事务|	Yes|
| 数据字典的统计|	Yes|

要将InnoDB的功能与MySQL随附的其他存储引擎进行比较，请参阅[第16章，备用存储引擎中的存储引擎功能表](https://dev.mysql.com/doc/refman/8.0/en/storage-engines.html)。

### Additional InnoDB Information and Resources

- 有关与InnoDB相关的术语和定义，请参见[MySQL词汇表](https://dev.mysql.com/doc/refman/8.0/en/glossary.html)。
- 有关InnoDB存储引擎的论坛，请参见[MySQL Forums :: InnoDB](http://forums.mysql.com/list.php?22)。
- InnoDB的发布与MySQL在相同的GNU GPL许可证版本2（1991年6月）下发布。 有关MySQL许可的更多信息，请参见http://www.mysql.com/company/legal/licensing/。

## 注

- [存储引擎](https://dev.mysql.com/doc/refman/8.0/en/storage-engines.html)