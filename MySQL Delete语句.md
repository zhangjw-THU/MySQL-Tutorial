# [MySQL Delete语句](<https://www.runoob.com/mysql/mysql-delete-query.html>)

#### 张嘉玮

2019年7月23日11:28:07

***

你可以使用 SQL 的 DELETE FROM 命令来删除 MySQL 数据表中的记录。

你可以在 **mysql>** 命令提示符或 PHP 脚本中执行该命令。

### 语法

以下是 SQL DELETE 语句从 MySQL 数据表中删除数据的通用语法：

```mysql
DELETE FROM table_name [WHERE Clause]
```

- 如果没有指定 WHERE 子句，MySQL 表中的所有记录将被删除。
- 你可以在 WHERE 子句中指定任何条件
- 您可以在单个表中一次性删除记录。

当你想删除数据表中指定的记录时 WHERE 子句是非常有用的。

## 从命令行中删除数据

这里我们将在 SQL DELETE 命令中使用 WHERE 子句来删除 MySQL 数据表 runoob_tbl 所选的数据。

### 实例:

```mysql
mysql> select * from da61_students;
+------------+------------------+----------+
| student_ID | student_adress   | major_in |
+------------+------------------+----------+
|        520 | Tsinghua InteNet | EE CS    |
|        521 | ZJ Apartment     | ML AI    |
|        528 | ZJ Apartment     | BigData  |
|        556 | W14 Apartment    | BigData  |
|        564 | Tsinghua InteNet | BigData  |
|        565 | Main Building    | EE CS    |
+------------+------------------+----------+
6 rows in set (0.00 sec)

mysql> delete from da61_students where student_ID=556;
Query OK, 1 row affected (0.13 sec)

mysql> select * from da61_students;
+------------+------------------+----------+
| student_ID | student_adress   | major_in |
+------------+------------------+----------+
|        520 | Tsinghua InteNet | EE CS    |
|        521 | ZJ Apartment     | ML AI    |
|        528 | ZJ Apartment     | BigData  |
|        564 | Tsinghua InteNet | BigData  |
|        565 | Main Building    | EE CS    |
+------------+------------------+----------+
5 rows in set (0.00 sec)

mysql>
```

