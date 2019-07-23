# [MySQL插入数据](<https://www.runoob.com/mysql/mysql-insert-query.html>)

#### 张嘉玮

2019年7月23日10:38:13

***

MySQL 表中使用 **INSERT INTO** SQL语句来插入数据。

你可以通过 mysql> 命令提示窗口中向数据表中插入数据，或者通过PHP脚本来插入数据。

### 语法

以下为向MySQL数据表插入数据通用的 **INSERT INTO** SQL语法：

```
INSERT INTO table_name ( field1, field2,...fieldN )
                       VALUES
                       ( value1, value2,...valueN );
```

如果数据是字符型，必须使用单引号或者双引号，如："value"。

```mysql
mysql> show tables
    -> ;
+--------------------+
| Tables_in_data0722 |
+--------------------+
| da61_students      |
| tb1                |
+--------------------+
2 rows in set (0.00 sec)

mysql> insert into da61_students
    -> (student_ID, student_adress, major_in)
    -> VALUES
    -> (528, "ZJ Apartment", "ITC");
Query OK, 1 row affected (0.18 sec)

mysql> insert into da61_students
    -> (student_ID, student_adress, major_in)
    -> VALUES
    -> (521, "ZJ Apartment", "ML AI");
Query OK, 1 row affected (0.04 sec)

mysql> insert into da61_students
    -> (student_ID, student_adress, major_in)
    -> VALUES
    -> (556, "W14 Apartment", "多媒体");
Query OK, 1 row affected (0.07 sec)

mysql> insert into da61_students
    -> (student_ID, student_adress, major_in)
    -> VALUES
    -> (521, "ZJ Apartment", "ML AI");
ERROR 1062 (23000): Duplicate entry '521' for key 'PRIMARY'
mysql> insert into da61_students
    -> (student_ID, student_adress, major_in)
    -> VALUES
    -> (564, "Tsinghua InteNet", "EE CS");
Query OK, 1 row affected (0.05 sec)

mysql> insert into da61_students
    -> (student_ID, student_adress, major_in)
    -> VALUES
    -> (520, "Tsinghua InteNet", "EE CS");
Query OK, 1 row affected (0.14 sec)
```
自增（最大的+1，不是上一个+1）：
```mysql
mysql> insert into da61_students
    -> (student_adress, major_in)
    -> VALUES
    -> ("Main Building", "EE CS");
Query OK, 1 row affected (0.14 sec)
```
查询：
```mysql
mysql> select * from da61_students
    -> ;
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
6 rows in set (0.11 sec)
```

