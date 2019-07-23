# [MySQL LIKE子句](<https://www.runoob.com/mysql/mysql-like-clause.html>)

#### 张嘉玮

2019年7月23日11:32:59

+++

我们知道在 MySQL 中使用 SQL SELECT 命令来读取数据， 同时我们可以在 SELECT 语句中使用 WHERE 子句来获取指定的记录。

WHERE 子句中可以使用等号 **=** 来设定获取数据的条件，如 "runoob_author = 'RUNOOB.COM'"。

但是有时候我们需要获取 runoob_author 字段含有 "COM" 字符的所有记录，这时我们就需要在 WHERE 子句中使用 SQL LIKE 子句。

SQL LIKE 子句中使用百分号 **%**字符来表示任意字符，类似于UNIX或正则表达式中的星号 *****。

如果没有使用百分号 **%**, LIKE 子句与等号 **=** 的效果是一样的。

### 语法

以下是 SQL SELECT 语句使用 LIKE 子句从数据表中读取数据的通用语法：

```mysql
SELECT field1, field2,...fieldN 
FROM table_name
WHERE field1 LIKE condition1 [AND [OR]] filed2 = 'somevalue'
```

- 你可以在 WHERE 子句中指定任何条件。
- 你可以在 WHERE 子句中使用LIKE子句。
- 你可以使用LIKE子句代替等号 **=**。
- LIKE 通常与 **%** 一同使用，类似于一个元字符的搜索。
- 你可以使用 AND 或者 OR 指定一个或多个条件。
- 你可以在 DELETE 或 UPDATE 命令中使用 WHERE...LIKE 子句来指定条件。

------

## 在命令提示符中使用 LIKE 子句

以下我们将在 SQL SELECT 命令中使用 WHERE...LIKE 子句来从MySQL数据表 runoob_tbl 中读取数据。

```mysql
mysql> select * from da61_students
    -> ;
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

mysql> select * from da61_students where student_adress link "ZJ%";
ERROR 1064 (42000): You have an error in your SQL syntax; check the manual that corresponds to your MySQL server version for the right syntax to use near 'link "ZJ%"' at line 1
mysql> select * from da61_students where student_adress like "ZJ%";
+------------+----------------+--------------+
| student_ID | student_adress | major_in     |
+------------+----------------+--------------+
|        521 | ZJ Apartment   | ML AI        |
|        528 | ZJ Apartment   | BigData      |
|        534 | ZJ #1          | Mchaine      |
|        599 | ZJ #2          | Computer SCI |
+------------+----------------+--------------+
4 rows in set (0.00 sec)

mysql> select * from da61_students where major_in like "M%"
    -> ;
+------------+----------------+----------+
| student_ID | student_adress | major_in |
+------------+----------------+----------+
|        521 | ZJ Apartment   | ML AI    |
|        534 | ZJ #1          | Mchaine  |
+------------+----------------+----------+
2 rows in set (0.00 sec)

mysql>
```

