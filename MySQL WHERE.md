# [MySQL WHERE子句](<https://www.runoob.com/mysql/mysql-where-clause.html>)

### 张嘉玮

2019年7月23日10:59:50

***

我们知道从 MySQL 表中使用 SQL SELECT 语句来读取数据。

如需有条件地从表中选取数据，可将 WHERE 子句添加到 SELECT 语句中。

### 语法

以下是 SQL SELECT 语句使用 WHERE 子句从数据表中读取数据的通用语法：

```mysql
SELECT field1, field2,...fieldN FROM table_name1, table_name2...
[WHERE condition1 [AND [OR]] condition2.....
```

- 查询语句中你可以使用一个或者多个表，表之间使用逗号**,** 分割，并使用WHERE语句来设定查询条件。
- 你可以在 WHERE 子句中指定任何条件。
- 你可以使用 AND 或者 OR 指定一个或多个条件。
- WHERE 子句也可以运用于 SQL 的 DELETE 或者 UPDATE 命令。
- WHERE 子句类似于程序语言中的 if 条件，根据 MySQL 表中的字段值来读取指定的数据。

以下为操作符列表，可用于 WHERE 子句中。

下表中实例假定 A 为 10, B 为 20

| 操作符 | 描述                                                         | 实例                 |
| :----- | :----------------------------------------------------------- | :------------------- |
| =      | 等号，检测两个值是否相等，如果相等返回true                   | (A = B) 返回false。  |
| <>, != | 不等于，检测两个值是否相等，如果不相等返回true               | (A != B) 返回 true。 |
| >      | 大于号，检测左边的值是否大于右边的值, 如果左边的值大于右边的值返回true | (A > B) 返回false。  |
| <      | 小于号，检测左边的值是否小于右边的值, 如果左边的值小于右边的值返回true | (A < B) 返回 true。  |
| >=     | 大于等于号，检测左边的值是否大于或等于右边的值, 如果左边的值大于或等于右边的值返回true | (A >= B) 返回false。 |
| <=     | 小于等于号，检测左边的值是否小于于或等于右边的值, 如果左边的值小于或等于右边的值返回true | (A <= B) 返回 true。 |

如果我们想在 MySQL 数据表中读取指定的数据，WHERE 子句是非常有用的。

使用主键来作为 WHERE 子句的条件查询是非常快速的。

如果给定的条件在表中没有任何匹配的记录，那么查询不会返回任何数据。

***

## 从命令提示符中读取数据

我们将在SQL SELECT语句使用WHERE子句来读取MySQL数据表 runoob_tbl 中的数据：

实例

以下实例将读取 runoob_tbl 表中 runoob_author 字段值为 Sanjay 的所有记录：

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

mysql> select * from da61_students
    -> where student_ID>=521 and student_ID<556
    -> ;
+------------+----------------+----------+
| student_ID | student_adress | major_in |
+------------+----------------+----------+
|        521 | ZJ Apartment   | ML AI    |
|        528 | ZJ Apartment   | ITC      |
+------------+----------------+----------+
2 rows in set (0.10 sec)

```

MySQL 的 WHERE 子句的字符串比较是不区分大小写的。 你可以使用 BINARY 关键字来设定 WHERE 子句的字符串比较是区分大小写的。

```mysql
mysql> select * from da61_students
    -> where student_ID>=521 and student_ID<556
    -> ;
+------------+----------------+----------+
| student_ID | student_adress | major_in |
+------------+----------------+----------+
|        521 | ZJ Apartment   | ML AI    |
|        528 | ZJ Apartment   | ITC      |
+------------+----------------+----------+
2 rows in set (0.10 sec)

mysql> MySQL 的 WHERE 子句的字符串比较是不区分大小写的。 你可以使用 BINARY 关键字来设定 WHERE 子句的字符串比较是区分大小写的。^Z
    -> ;
ERROR 1064 (42000): You have an error in your SQL syntax; check the manual that corresponds to your MySQL server version for the right syntax to use near 'MySQL 的 WHERE 子句的字符串比较是不区分大小写的。 你可以使' at line 1
mysql> select * from da61_students
    -> where student_adress="zj Apartment";
+------------+----------------+----------+
| student_ID | student_adress | major_in |
+------------+----------------+----------+
|        521 | ZJ Apartment   | ML AI    |
|        528 | ZJ Apartment   | ITC      |
+------------+----------------+----------+
2 rows in set (0.10 sec)

mysql> select * from da61_students
    -> where binary student_adress="zj Apartment";
Empty set (0.14 sec)

mysql> select * from da61_students
    -> where binary student_adress="ZJ Apartment";
+------------+----------------+----------+
| student_ID | student_adress | major_in |
+------------+----------------+----------+
|        521 | ZJ Apartment   | ML AI    |
|        528 | ZJ Apartment   | ITC      |
+------------+----------------+----------+
2 rows in set (0.00 sec)

mysql>
```

