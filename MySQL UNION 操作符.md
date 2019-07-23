# [MySQL UNION操作符](<https://www.runoob.com/mysql/mysql-union-operation.html>)

### 张嘉玮

2019年7月23日

***

本教程为大家介绍 MySQL UNION 操作符的语法和实例。

### 描述

MySQL UNION 操作符用于连接两个以上的 SELECT 语句的结果组合到一个结果集合中。多个 SELECT 语句会删除重复的数据。

### 语法

MySQL UNION 操作符语法格式：

```mysql
SELECT expression1, expression2, ... expression_n
FROM tables
[WHERE conditions]
UNION [ALL | DISTINCT]
SELECT expression1, expression2, ... expression_n
FROM tables
[WHERE conditions];
```

### 参数

- **expression1, expression2, ... expression_n**: 要检索的列。
- **tables:** 要检索的数据表。
- **WHERE conditions:** 可选， 检索条件。
- **DISTINCT:** 可选，删除结果集中重复的数据。默认情况下 UNION 操作符已经删除了重复数据，所以 DISTINCT 修饰符对结果没啥影响。
- **ALL:** 可选，返回所有结果集，包含重复数据。

------

## 演示数据库

```mysql
mysql> select * from da61_students;
+------------+------------------+--------------+
| student_ID | student_adress   | major_in     |
+------------+------------------+--------------+
|        520 | Tsinghua InteNet | EE CS        |
|        521 | ZJ Apartment     | ML AI        |
|        528 | ZJ Apartment     | BigData      |
|        534 | ZJ #1            | Mchaine      |
|        564 | Tsinghua InteNet | BigData      |
|        565 | Main Building    | EE CS        |
|        599 | ZJ #2            | Computer SCI |
+------------+------------------+--------------+
7 rows in set (0.00 sec)

mysql> select * from tb1;
+-------+---------+
| ZJWID | TTITLE  |
+-------+---------+
|     1 | BigData |
|     2 | ML AI   |
|     3 | EE CS   |
|     4 | Machine |
+-------+---------+
4 rows in set (0.00 sec)
```
选出不同的方向：
```mysql
mysql> select major_in from da61_student
    -> union
    -> select TTITLE from tb1
    -> ;
ERROR 1146 (42S02): Table 'data0722.da61_student' doesn't exist
mysql> select major_in from da61_students
    -> union
    -> select TTITLE from tb1
    -> ;
+--------------+
| major_in     |
+--------------+
| EE CS        |
| ML AI        |
| BigData      |
| Mchaine      |
| Computer SCI |
| Machine      |
+--------------+
6 rows in set (0.07 sec)
```

重复的也要输出：

```mysql
mysql> select major_in from da61_students
    -> union all
    -> select TTITLE from tb1
    -> ;
+--------------+
| major_in     |
+--------------+
| EE CS        |
| ML AI        |
| BigData      |
| Mchaine      |
| BigData      |
| EE CS        |
| Computer SCI |
| BigData      |
| ML AI        |
| EE CS        |
| Machine      |
+--------------+
11 rows in set (0.00 sec)

mysql>

```

