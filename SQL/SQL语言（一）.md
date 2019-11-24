---
type: blog
title: SQL语言进阶（一）
categories: SQL
tags: SQL
---
# SQL语言
简单来说，你需要在数据库上执行的操作大部分都要由SQL语句完成
```sql
SELECT * FROM websites
```
但是，SQL语句并不对大小写敏感，同时我们在本例教程中，每个语句都加上分号
```sql
mysql> use RUNOOB;
Database changed

mysql> set names utf8;
Query OK, 0 rows affected (0.00 sec)

mysql> SELECT * FROM Websites;
+----+--------------+---------------------------+-------+---------+
| id | name         | url                       | alexa | country |
+----+--------------+---------------------------+-------+---------+
| 1  | Google       | https://www.google.cm/    | 1     | USA     |
| 2  | 淘宝          | https://www.taobao.com/   | 13    | CN      |
| 3  | 菜鸟教程      | http://www.runoob.com/    | 4689  | CN      |
| 4  | 微博          | http://weibo.com/         | 20    | CN      |
| 5  | Facebook     | https://www.facebook.com/ | 3     | USA     |
+----+--------------+---------------------------+-------+---------+
5 rows in set (0.01 sec)
```
下面的大部分都是基于这个表格的
## SQL SELECT 语句
SELECT语句用于从数据库中选取数据，结果被存在一个结果表中，称为结果集
### SELECT 语法
```sql
SELECT column_name,column_name FROM table_name;  # 选出指定列

SELECT * FROM table_name;  # 选出所有的列
```
## SQL SELECT DISTINCT 语句
在表中，一个列可能会包含多个重复值，DISTINCT关键词用于返回唯一不同的值,就是会删掉重复的值
### SQL SELECT DISTINCT 语法
```sql
SELECT DISTINCT column_name, column_name FROM table_name;
```
## SELECT WHERE子句
WHERE子句用于提取那些阿玛尼组指定条件的记录
### SQL WHERE 语法
```sql
SELECT column_name,column_name FROM table_name WHERE column_name operator value;
```
### 文本字段 vs 数值字段
SQL中使用**单引号**来环绕文本数值，但是如果是数值就不用使用单引号了，如：
```sql
SELECT * FROM websites WHERE id = 1;
SELECT * FROM websites WHERE country = 'CN';
```
### WHERE子句的运算符
| 运算符 | 描述 |
| ------ | ------ | 
| <>或者!= | 不等于 | 
| BETWEEN | 在某个范围内 | 
| LIKE | 搜索某种模式 |
| IN | 指定针对某个列的可能值 |
## SQL AND & OR 运算符
AND & OR 运算符基于一个以上条件对记录进行过滤  
* 如果第一个条件与第二个条件都成立，则ADN运算符显示一条记录
* 如果第一个条件与第二个条件有一个成立，则OR运算符显示一条记录

### SQL AND & OR 语法
```sql
SELECT * FROM Websites WHERE country = 'CN' AND alexa > 50;
SELECT * FROM websites WHERE country = 'USA' OR country = 'CN';
```
### 结合AND 和 OR
用法示例如下：
```sql
SELECT * FROM websites WHERE alexa > 15 
AND (country = 'CN' OR country = 'USA')
```
## SQL ORDER BY 关键词
ORDER BY 关键词用于对于结果集按照一个列或者多个列进行排序
### SQL ORDER BY 的语法
ORDER BY关键词默认按照升序进行排列，如果需要降序，则可以使用DESC关键字
```sql
SELECT column_name, column_name FROM table_name 
ORDER BY column_name, column_name ASC|DESC;
```
### SQL ORDER BY(DESC)实例
```sql
SELECT * FROM websites ORDER BY alexa ;
SELECT * FROM websites ORDER BY alexa DESC;
```
### ORDER BY 多列
当有多列进行排序时，我们优先选择第一列
```sql
SELECT * FROM websites ORDER BY country,alexa;
```
## SQL INSERT INTO语句
INSERT INTO语句向表中插入新纪录
### SQL INSERT INTO语句的语法
INSERT 语句有两种编写形式：
* 第一钟形式无需指定要插入数据的列名，只需要提供被插入的值即可：
```sql
INSERT INTO table_name VALUES (value1,value2,value3);
```
* 第二种形式需要指定列名及被插入的值
```sql
INSERT INTO table_name (column1, column2,column3) VALUES (value1,value2,value3)
```
### INSERT INTO实例
假设我们需要向‘websites'表钟插入一个新行
```sql
INSERT INTO websites(name, url, alexa, country) VALUES('百度’, 'https://www.baidu.com/','4','CN');
```
### 在指定的列插入数据
下面的SQL语句将插入一个新行，但是只在’name'、‘url'、’country‘列插入数据
```sql
INSERT INTO websites(name, url, country) VALUES ('stackoverflow', 'http://stackoverflow.com/', 'IND')
```
## SQL UPDATE 语句
UPDATE语句用于更新表中已经存在的记录

### UPDATE语句的语法
```sql
UPDATE table_name SET column = value1, column2 = value2,... WHERE some_column = some_value;
```
### UPDATE实例
```sql
UPADATE Websites SET alexa = '500', country = 'USA' WHERE name = '菜鸟教程’;
```
## SQL DELETE 
DELET语句用于删除表中的行
### SQL DELETE语法和实例
从表中删除网站名是百度且国家为CN的网站
```sql
DELET FROM websites WHERE name = '百度' AND country = 'CN';
```
### 删除所有数据
```sql
DELETE FROM table_name;
DELETE * FROM table_name;
```

## 最后
非常感谢菜鸟教程，本文借鉴了菜鸟教程的表格和相关代码：[菜鸟教程](https://www.runoob.com/sql/sql-syntax.html): https://www.runoob.com/sql/sql-syntax.html