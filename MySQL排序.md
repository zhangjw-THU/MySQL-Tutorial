

# [MySQL排序](<https://www.runoob.com/mysql/mysql-order-by.html>)

#### 张嘉玮

2019年7月23日14:15:05

***

我们知道从 MySQL 表中使用 SQL SELECT 语句来读取数据。

如果我们需要对读取的数据进行排序，我们就可以使用 MySQL 的 **ORDER BY** 子句来设定你想按哪个字段哪种方式来进行排序，再返回搜索结果。

### 语法

以下是 SQL SELECT 语句使用 ORDER BY 子句将查询数据排序后再返回数据：

```mysql
SELECT field1, field2,...fieldN FROM table_name1, table_name2...
ORDER BY field1 [ASC [DESC][默认 ASC]], [field2...] [ASC [DESC][默认 ASC]]
```

- 你可以使用任何字段来作为排序的条件，从而返回排序后的查询结果。
- 你可以设定多个字段来排序。
- 你可以使用 ASC (升序）或 DESC（降序） 关键字来设置查询结果是按升序或降序排列。 默认情况下，它是按升序排列。
- 你可以添加 WHERE...LIKE 子句来设置条件。

---

## 在命令提示符中使用 ORDER BY 子句

以下将在 SQL SELECT 语句中使用 ORDER BY 子句来读取MySQL 数据表 da61_stuedents 中的数据：

### 实例

尝试以下实例，结果将按升序及降序排列

```mysql

mysql> select * from da61_students order by major_in;
+------------+------------------+--------------+
| student_ID | student_adress   | major_in     |
+------------+------------------+--------------+
|        528 | ZJ Apartment     | BigData      |
|        564 | Tsinghua InteNet | BigData      |
|        599 | ZJ #2            | Computer SCI |
|        520 | Tsinghua InteNet | EE CS        |
|        565 | Main Building    | EE CS        |
|        534 | ZJ #1            | Mchaine      |
|        521 | ZJ Apartment     | ML AI        |
+------------+------------------+--------------+
7 rows in set (0.05 sec)

mysql> select * from da61_students order by major_in ASC;
+------------+------------------+--------------+
| student_ID | student_adress   | major_in     |
+------------+------------------+--------------+
|        528 | ZJ Apartment     | BigData      |
|        564 | Tsinghua InteNet | BigData      |
|        599 | ZJ #2            | Computer SCI |
|        520 | Tsinghua InteNet | EE CS        |
|        565 | Main Building    | EE CS        |
|        534 | ZJ #1            | Mchaine      |
|        521 | ZJ Apartment     | ML AI        |
+------------+------------------+--------------+
7 rows in set (0.00 sec)

mysql> select * from da61_students order by major_in DESC;
+------------+------------------+--------------+
| student_ID | student_adress   | major_in     |
+------------+------------------+--------------+
|        521 | ZJ Apartment     | ML AI        |
|        534 | ZJ #1            | Mchaine      |
|        520 | Tsinghua InteNet | EE CS        |
|        565 | Main Building    | EE CS        |
|        599 | ZJ #2            | Computer SCI |
|        528 | ZJ Apartment     | BigData      |
|        564 | Tsinghua InteNet | BigData      |
+------------+------------------+--------------+
7 rows in set (0.00 sec)

```

