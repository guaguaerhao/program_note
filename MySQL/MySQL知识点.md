<h1 style="color: lightpink">数据库</h1>

```mysql
# 创建数据库
语法：
CREATE DATABASE db_name CHARACTER SET character_name;
例子：
CREATE DATABASE `student` CHARACTER SET utf8mb4;

# 删除数据库
语法：
DROP DATABASE db_name;
例子：
DROP DATABASE `student`;

# 修改数据库
语法：
ALTER DATABASE db_name CHARACTER SET character_name;

# 查看数据库
语法：
SHOW DATABASES;

```

<h1 style="color: lightgreen">数据表</h1>

```mysql
# 创建数据表
语法：
CREATE DATABASE table_name (
	column_name1 datatype [列级别约束条件],
  column_name2 datatype [列级别约束条件],
  ...
  [表级别约束条件]
);
例子：
CREATE DATABASE student(
	id int not null auto_increment comment "主键 id",
  parent_id int default 0 comment "该学生的父母id",
  name varchar(32) not null,
  primary key (`id`),
  unique key (`parent_id`)
) auto_incremmet= 2 CHARACTER SET utf8mb4;

# 删除数据表
语法：
DROP TABLE table_name;
例子：
DROP TABLE `student`;

# 修改数据表
语法：
ALTER TALBE table_name
ADD [COLUMN] create_definition [First|AFTER col_name]					// 添加新字段
|		ADD INDEX [index_name] (index_col_name, ...) 							// 添加索引名称
|		ADD PRIMARY KEY (index_col_name, ...)											// 添加主键名称
|		ADD UNIQUE [index_name] (index_col_name, ...) 						// 添加唯一索引
|		ALTER [COLUMN] col_name {SET DEFAULT literal | DROP DEFAULT} // 修改默认值
|		CHANGE [COLUMN] old_col_name create_definition						// 修改字段名称以及类型
|		MODIFY [COLUMN] create_definition													// 修改字段类型
|		DROP [COLUMN] col_name																		// 删除字段名称
|		DROP PRIMARY KEY																					// 删除主键
|		DROP INDEX index_name																			// 删除索引名称
|		RENAME [AS] new_tb_name																		// 修改数据表名
|		talbe_options

# 查看数据表
语法：
SHOW TABLES;
```

<h1 style="color: #9D85EB">数据表数据操作(增加、删除、修改)</h1>

```mysql
# 插入记录
语法：
INSERT [INTO] table_name (column1, column2, ...) VALUES (value1, value2, ...); # 单条
INSERT [INTO] table_name (column1, column2, ...) VALUES (value1, value2, ...), (value1, value2, ...); # 多条
例子：
INSERT `student` (name, parent_id) values ("小明", 2);

# 删除记录
语法：
DELETE FROM table_name [WHERE where_definition];
例子：
DELETE FROM `student`; // 清空了数据表
DELETE FROM `student` WHERE id=3; // 删除符合 WHERE 条件的记录

# 修改记录
语法：
UPDATE table_name SET col_name1=value1, col_name2=value2, ... [WHERE where_definition];
例子：
UPDATE `student` SET name="小芳" WHERE id=1;
```

<h1 style="color: #0BC49F">运算符与函数</h1>

```mysql
# 算术运算符 (加、减、乘、除、求余)
+、-、*、/(DIV)、%(MOD) 

# 比较运算符
<、=、>、!=、<=、>=、<>、IS NULL、BETWEEN AND、IN、LIKE、REGEXP

# 逻辑运算符
&& AND 、 || OR 、 ! NOT 、 XOR

# 位运算符
& 、 | 、 ~ 、^ 、<< 、>>
```



<h1 style="color: #EB4390">系统内置函数</h1>

```mysql
# 数学函数（主观常用）
ABS(x)  绝对值
CEILING(x)	向上取整
FLOOR(x)	向下取整
GREATEST(x1,x2,...xn) 返回集合最大值
LEASTEST(x1,x2,...xn) 返回集合最小值
MOD(x,y)	求x/y的模（余数）可用 % 取代
PI() PI的值（圆周率）
RAND()  0~1的随机数
ROUND(x)  x四舍五入的值

# 字符串函数
PS：以下函数括号中的 s 都作为字符串

LENGTH(s) s的长度
CONCAT(s1,s2,...sn) 拼接字符串
CONCAT_WS(sep,s1,s2,...sn)	sep作为拼接符来拼接字符串，类似于前端的join
UPPER(s)	转大写
LOWER(s)	转小写
LEFT(s,n)	返回s左边数起前n个字符
RIGHT(s,n)	返回s右边数起前n个字符
LTRIM(s) 去左边空格
LTRIM(s) 去右边空格
TRIM(s) 去两边空格
REVERSE(s) 字符反转
REPLACE(s,s1,s2) 字符串s中，s2替换s1
LPAD(s,len,s1) 字符串s左边，加 len 个s1
RPAD(s,len,s1) 字符串s右边，加 len 个s1

# 日期和时间函数
PS：注意参数d和t的区别
CURDATE() | CURRENT_DATE()  // 当前日期		PS：我喜欢第二个
CURTIME() | CURRENT_TIME()  // 当前时间		PS：我喜欢第二个
DAYOFWEEK(d)	一周之几	1~7
DAYOFMONTH(d)	一月之几	1~31
DAYOFYEAR(d)		一年之几	1~366
NOW()	日期时间
HOUR(t)	0~23
MINUTE(t)	0~59
SECOND(t)	0~59
MONTH(d)	1~12
MONTHNAME(d)	d的月份名
WEEK(d)	一年之几周	0~53
YEAR(d)	1000~9999
TIME_FORMAT(t,fmt) 根据fmt格式化时间t
DATE_FORMAT(d,fmt) 根据fmt格式化日期d

# 系统信息函数
DATABASE()	当前数据库名
CONNECTION_ID()		服务器的连接数
USER()、SYSTEM_USER()、SESSION_USER()		当前登录用户名
VERSION()		数据库的版本号


# 其他函数
MD5(str)	加密

```

<h1 style="color: #C0523D">索引和完整性约束</h1>

```mysql
索引的作用：通过索引查询数据，不但可以提供查询速度，还可以降低服务器的负载
分类：普通索引（INDEX|KEY）、唯一索引（UNIQUE)、主键索引（PRIMARY KEY）、全文索引（FULLTEXT)
# 创建索引
CREATE TABLE tb_name(
	col_name1 data_type,
  ...
  [UNIQUE | FULLTEXT | SPATIAL] [INDEX | KEY] [index_name] (col_name [length]) [ASC | DESC]
);
```

解析：

其中

	- UNIQUE、FULLTEXT和SPATIAL为可选参数，分别为唯一索引、全文索引和空间索引
	- INDEX和KEY为同义词，两者作用相同，用来指定创建索引
	- col_name为需要索引的字段列
	- index_name指定索引的名称，为可选参数。如果不指定，MySQL默认col_name为索引值
	- length为可选参数，表示索引的长度，只有字符串类型的字段才能指定索引长度
	- ASC或DESC参数用于指定数据表的排序顺序



<h1 style="color: #EBD416">数据表数据查询（重点）</h1>

```mysql

```













#### 插入默认值

```mysql
//前提，COLUMN1列有设置默认值
INSERT `TABLE` (COLUMN1) VALUES(DEFAULT);
```

 

#### change和modify的区别

modify可以修改字段属性，change可以修改字段名称







