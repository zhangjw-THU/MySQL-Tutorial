# [MySQL Update更新](<https://www.runoob.com/mysql/mysql-update-query.html>)

#### 张嘉玮

2019年7月23日11:16:56

***

如果我们需要修改或更新 MySQL 中的数据，我们可以使用 SQL UPDATE 命令来操作。

### 语法

以下是 UPDATE 命令修改 MySQL 数据表数据的通用 SQL 语法：

```mysql
UPDATE table_name SET field1=new-value1, field2=new-value2
[WHERE Clause]
```

- 你可以同时更新一个或多个字段。
- 你可以在 WHERE 子句中指定任何条件。
- 你可以在一个单独表中同时更新数据。

当你需要更新数据表中指定行的数据时 WHERE 子句是非常有用的。

------

通过命令提示符更新数据

以下我们将在 SQL UPDATE 命令使用 WHERE 子句来更新 da61_student 表中指定的数据：

```mysql
mysql> select * from da61_student
    -> ;
ERROR 1146 (42S02): Table 'data0722.da61_student' doesn't exist
mysql> select * from da61_students;
+------------+------------------+----------+
| student_ID | student_adress   | major_in |
+------------+------------------+----------+
|        520 | Tsinghua InteNet | EE CS    |
|        521 | ZJ Apartment     | ML AI    |
|        528 | ZJ Apartment     | ITC      |
|        556 | W14 Apartment    | 多媒体   |
|        564 | Tsinghua InteNet | EE CS    |
|        565 | Main Building    | EE CS    |
+------------+------------------+----------+
6 rows in set (0.00 sec)

mysql> update da61_students set major_in="BigData" where student_ID>=528 and student_ID<=564;
Query OK, 3 rows affected (0.16 sec)
Rows matched: 3  Changed: 3  Warnings: 0

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

mysql>
```

