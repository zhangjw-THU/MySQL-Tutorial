# [MySQL PHP 语法](<https://www.runoob.com/mysql/mysql-php-syntax.html>)

#### [张嘉玮](<https://github.com/zhangjw-THU>)

2019年7月22日10:00:28

***

MySQL 可应用于多种语言，包括 PERL, C, C++, JAVA 和 PHP。 在这些语言中，Mysql在PHP的web开发中是应用最广泛。

在本教程中我们大部分实例都采用了 PHP 语言。如果你想了解 Mysql 在 PHP 中的应用，可以访问作者的 [PHP 中使用 Mysqli 介绍](https://www.runoob.com/php/php-mysql-intro.html)。

PHP提供了多种方式来访问和操作Mysql数据库记录。PHP **Mysqli**函数格式如下：

```php
mysqli_function(value,value,...);
```

以上格式中 function部分描述了mysql函数的功能，如:

```php
mysqli_connect($connect);
mysqli_query($connect,"SQL 语句");
mysqli_fetch_array()
mysqli_close()
```

以下实例展示了PHP调用mysql函数的语法：

```php
<?php
$retval = mysqli_function(value, [value,...]);
if( !$retval )
{
   die ( "相关错误信息" );
}
// 其他 MySQL 或 PHP 语句
?>
```

