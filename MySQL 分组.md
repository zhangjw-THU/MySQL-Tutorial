# [MySQL GROUP BY 语句](<https://www.runoob.com/mysql/mysql-group-by-statement.html>)

#### 张嘉玮

2019年7月23日14:28:36

---

GROUP BY 语句根据一个或多个列对结果集进行分组。

在分组的列上我们可以使用 COUNT, SUM, AVG,等函数。

### GROUP BY 语法

```mysql
SELECT column_name, function(column_name)
FROM table_name
WHERE column_name operator value
GROUP BY column_name;
```

---

## 实例演示

本章节实例使用到了以下表结构及数据，使用前我们可以先将以下数据导入数据库中。

```mysql
mysql> select * from employee_tbl;
+----+--------+---------------------+--------+
| id | name   | date                | singin |
+----+--------+---------------------+--------+
|  1 | 灏忔槑 | 2016-04-22 15:25:33 |      1 |
|  2 | 灏忕帇 | 2016-04-20 15:25:47 |      3 |
|  3 | 灏忎附 | 2016-04-19 15:26:02 |      2 |
|  4 | 灏忕帇 | 2016-04-07 15:26:14 |      4 |
|  5 | 灏忔槑 | 2016-04-11 15:26:40 |      4 |
|  6 | 灏忔槑 | 2016-04-04 15:26:54 |      2 |
|  7 | Bob    | 2019-07-23 14:42:22 |      1 |
+----+--------+---------------------+--------+
7 rows in set (0.00 sec)
```



```mysql
mysql> select name, COUNT(*) FROM employee_tbl GROUP BY name;
+--------+----------+
| name   | COUNT(*) |
+--------+----------+
| Bob    |        1 |
| 灏忎附 |        1 |
| 灏忔槑 |        3 |
| 灏忕帇 |        2 |
+--------+----------+
4 rows in set (0.36 sec)
```



---

### 使用 WITH ROLLUP

WITH ROLLUP 可以实现在分组统计数据基础上再进行相同的统计（SUM,AVG,COUNT…）。

例如我们将以上的数据表按名字进行分组，再统计每个人登录的次数:

```mysql
mysql> select name, SUM(singin) as singin_count FROM employee_tbl GROUP BY name WITH ROLLUP;
+--------+--------------+
| name   | singin_count |
+--------+--------------+
| Bob    |            1 |
| 灏忎附 |            2 |
| 灏忔槑 |            7 |
| 灏忕帇 |            7 |
| NULL   |           17 |
+--------+--------------+
5 rows in set (0.59 sec)

```

其中记录 NULL 表示所有人的登录次数。

我们可以使用 coalesce 来设置一个可以取代 NUll 的名称，coalesce 语法：

```
select coalesce(a,b,c);
```

参数说明：如果a==null,则选择b；如果b==null,则选择c；如果a!=null,则选择a；如果a b c 都为null ，则返回为null（没意义）。

以下实例中如果名字为空我们使用总数代替：

```mysql
mysql> SELECT coalesce(name, '总数'), SUM(singin) as singin_count FROM  employee_tbl GROUP BY name WITH ROLLUP;
+------------------------+--------------+
| coalesce(name, '总数') | singin_count |
+------------------------+--------------+
| Bob                    |            1 |
| 灏忎附                 |            2 |
| 灏忔槑                 |            7 |
| 灏忕帇                 |            7 |
| 总数                   |           17 |
+------------------------+--------------+
5 rows in set, 1 warning (0.03 sec)
```



