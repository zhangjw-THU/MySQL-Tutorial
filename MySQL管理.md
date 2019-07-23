# [MySQL管理](<https://www.runoob.com/mysql/mysql-administration.html>)

#### [张嘉玮](<https://github.com/zhangjw-THU>)

2019年7月22日09:23:15

***

### 启动及关闭 MySQL 服务器

#### Windows 系统下

在 Windows 系统下，打开命令窗口(cmd)，进入 MySQL 安装目录的 bin 目录。

本地打开：

```shell
net start mysql
mysql -u root
```

启动：

```shell
cd c:/mysql/bin
mysqld --console
```

关闭：

```shell
cd c:/mysql/bin
mysqldmin -uroot shutdown
```

***

###  管理MySQL的命令

以下列出了使用Mysql数据库过程中常用的命令：

* **USE 数据库名** :
  选择要操作的Mysql数据库，使用该命令后所有Mysql命令都只针对该数据库

  ```powershell
  mysql> use RUNOOB;
  Database changed
  ```

* **SHOW DATABASES:** 
  列出 MySQL 数据库管理系统的数据库列表。

  ```powershell
  mysql> SHOW DATABASES;
  +--------------------+
  | Database           |
  +--------------------+
  | information_schema |
  | RUNOOB             |
  | cdcol              |
  | mysql              |
  | onethink           |
  | performance_schema |
  | phpmyadmin         |
  | test               |
  | wecenter           |
  | wordpress          |
  +--------------------+
  10 rows in set (0.02 sec)
  ```

* **SHOW TABLES:**
  显示指定数据库的所有表，使用该命令前需要使用 use 命令来选择要操作的数据库。

  ```powershell
  mysql> use RUNOOB;
  Database changed
  mysql> SHOW TABLES;
  +------------------+
  | Tables_in_runoob |
  +------------------+
  | employee_tbl     |
  | runoob_tbl       |
  | tcount_tbl       |
  +------------------+
  3 rows in set (0.00 sec)
  ```

* **SHOW COLUMNS FROM 数据表:**
  显示数据表的属性，属性类型，主键信息 ，是否为 NULL，默认值等其他信息。

  ```shell
  mysql> SHOW COLUMNS FROM runoob_tbl;
  +-----------------+--------------+------+-----+---------+-------+
  | Field           | Type         | Null | Key | Default | Extra |
  +-----------------+--------------+------+-----+---------+-------+
  | runoob_id       | int(11)      | NO   | PRI | NULL    |       |
  | runoob_title    | varchar(255) | YES  |     | NULL    |       |
  | runoob_author   | varchar(255) | YES  |     | NULL    |       |
  | submission_date | date         | YES  |     | NULL    |       |
  +-----------------+--------------+------+-----+---------+-------+
  4 rows in set (0.01 sec)
  ```

* **SHOW INDEX FROM 数据表:**
  显示数据表的详细索引信息，包括PRIMARY KEY（主键）。

  ```
  mysql> SHOW INDEX FROM runoob_tbl;
  +------------+------------+----------+--------------+-------------+-----------+-------------+----------+--------+------+------------+---------+---------------+
  | Table      | Non_unique | Key_name | Seq_in_index | Column_name | Collation | Cardinality | Sub_part | Packed | Null | Index_type | Comment | Index_comment |
  +------------+------------+----------+--------------+-------------+-----------+-------------+----------+--------+------+------------+---------+---------------+
  | runoob_tbl |          0 | PRIMARY  |            1 | runoob_id   | A         |           2 |     NULL | NULL   |      | BTREE      |         |               |
  +------------+------------+----------+--------------+-------------+-----------+-------------+----------+--------+------+------------+---------+---------------+
  1 row in set (0.00 sec)
  ```

* **SHOW TABLE STATUS LIKE [FROM db_name] [LIKE 'pattern'] \G:** 
  该命令将输出Mysql数据库管理系统的性能及统计信息。

  ```
  mysql> SHOW TABLE STATUS  FROM RUNOOB;   # 显示数据库 RUNOOB 中所有表的信息
  
  mysql> SHOW TABLE STATUS from RUNOOB LIKE 'runoob%';     # 表名以runoob开头的表的信息
  mysql> SHOW TABLE STATUS from RUNOOB LIKE 'runoob%'\G;   # 加上 \G，查询结果按列打印
  ```

  