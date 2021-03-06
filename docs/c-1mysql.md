1、初识MySQL

JavaEE：企业级Java开发 Web

前端（页面：展示：数据）

后台 （连接点：连接数据库JDBC,连接前端（控制视图跳转，给前端传递数据））

数据库（存数据，Txt,Excel,Word）

> 只会写代码，学好数据库，基本混饭吃：
> 
> 操作系统，数据结构与算法！当一个不错的程序猿！
> 
> 离散数学，数字电路，体系结构，编译原理。+实战经验，优秀程序猿

### 1.1为什么学数据库

1、岗位需求

2、现在的世界，大数据时代，得数据者得天下

3、被迫需求：存数据

`4、数据库是所有软件体系中最核心的存在` DBA

### 1.2 什么是数据库

数据库：(DB,DataBase)

概念:数据仓库，软件，安装在操作系统之（windows,Linux。mac）上的！SQL,可以存储大量的数据，500万!

作用:存储数据，管理数据 Excel

### 1.3 数据库分类

关系型数据库：(SQL)

*   MySQL, Oracle, sql Server, DB2, SQLite
*   通过表和表之间，行和列之间的关系进行数据的存储

非关系型数据库：(NoSQL) Not Only SQL

*   Redis, MongDB
*   非关系型数据库，对象存储，通过对象自身的属性来决定。

\*\*DBMS(数据库管理系统) \*\*

*   数据库的管理软件，科学有效的管理我们的数据，维护和获取
*   MySQL ，数据管理系统！

### 1.4 MySQL简介

MySQL是一个\*\*[关系型数据库管理系统](https://baike.baidu.com/item/%E5%85%B3%E7%B3%BB%E5%9E%8B%E6%95%B0%E6%8D%AE%E5%BA%93%E7%AE%A1%E7%90%86%E7%B3%BB%E7%BB%9F/696511)\*\*

前世： 瑞典MySQL AB 公司

今身： 属于 [Oracle](https://baike.baidu.com/item/Oracle) 旗下产品

MySQL是最好的 [RDBMS](https://baike.baidu.com/item/RDBMS/1048260) (Relational Database Management System，关系数据库管理系统) 应用软件之一。

开源的数据库软件

体积小，速度快，总体拥有成本低，招人成本比较低。

中小型网站，或者大型网站，集群

官网： https://www.mysql.com/

### 1.5连接数据库

命令行连接！

```sql
mysql -u root -p123456 --连接数据库

update mysql.user set authentication_string=password('123456') where user='root' and Host='localhost';  --修改密码

flush privileges;--刷新权限
--------------------------------------------------
--所有语句使用;结尾--

show databases;--查看所有的数据库

mysql> use school--切换数据库， use 数据库名
Database changed

--

show tables;--查看数据库中所有的表
describe student;--显示数据库中所有的表的信息
create database westos;--创建一个数据库

exit;--退出连接

--单行注释（sql本来注释）
/*
多行注释
*/

```

2、操作数据库
=======

操作数据库》操作数据库中的表》操作数据库中表的数据

**MySQL不区分大小写**

### 2.1操作数据库

1.创建数据库

```sql
CREATE DATABASE IF NOT EXISTS westos;

```

2.删除数据库

```sql
DROP DATABASE IF EXISTS westos

```

3.使用数据库

```sql
-- ``,如果你的表名或者字段名是一个特殊字符，需要带``

USE 'school'

```

4.产看数据库

```sql
SHOW DATABASES--查看所有数据库

```

### 2.2数据库的列类型

[MySQL中tinytext、text、mediumtext和longtext等各个类型详解](https://blog.csdn.net/youcijibi/article/details/80673811)

> 数值

*   tinyint 十分小的数据 1个字节
*   smallint 较小的数据 2个字节
*   mediumint 中等大小 3个字节
*   int 标准的整数 4个字节（常用）
*   bigint 较大的数据 8个字节
*   float 浮点数 4个字节
*   double 浮点数 8个字节 （精度问题）
*   decimal 字符串形式的浮点数,金融计算的时候，一般用

> 字符串

*   char 字符串固定大小 0-255
*   **varchar 可变字符串 0-65535**（常用）
*   tinytext 微型文本 2^8-1
*   **text 文本串 2^16-1** (保存大文本)

> 时间日期

java.util.Date

*   date YYYY-MM-DD，日期
*   time HH:mm:ss 时间格式
*   **datetime YYYY-MM-DD HH:mm:ss 最常用的时间格式**
*   timestamp 时间戳 1970.1.1到现在的毫秒数
*   year 年份表示

> null

*   没有值，未知
*   **注意，不要使用null进行运算**，结果为null

### 2.3数据库的字段类型（重点）

unsigened:

*   无符号的整数
  
*   声明该列不能声明负数

zerofill:

*   0填充的
*   10的长度 1 – 0000000001 不足位数用0 填充

自增：

*   通常理解为自增，自动在上一条记录的基础上+1
*   通常用来设计唯一的主键 index,必须是整数类似
*   可以自定义设置主键自增的起始值和步长

非空 NULL not Null

*   假设设置为 not null，如何不给他赋值，就会报错
  
*   NULL 如果不填写，默认为NULL

默认：

*   设置默认的值！

### 2.4 创建数据库表

```sql
--目标:创建一个schoo1数据库

--创建学生表(列,字段)使用SQL 创建

--学号int 登录密码varchar(20)姓名,性别varchar(2),出生日期(datatime)，家庭住址，emai1--注意点，使用英文()，表的名称和字段尽量使用括起来

-- AUTO_ INCREMENT 自增

--字符串使用单引号括起来!

--所有的语句后面加，(英文的)，最后一个不用加

-- PRIMARY KEY 主键，一般- 一个表只有一个唯一 -的主键!
CREATE DATABASE school
CREATE TABLE IF NOT EXISTS `student` (
`id` INT(4) NOT NULL AUTO_INCREMENT COMMENT '学号',
`name` VARCHAR(30) NOT NULL DEFAULT '匿名' COMMENT '姓名',
`pwd` VARCHAR(20) NOT NULL DEFAULT '123456' COMMENT '密码',
`sex` VARCHAR(2) NOT NULL DEFAULT '男' COMMENT '性别',
`birthday` DATETIME DEFAULT NULL COMMENT '出生日期',
`address` VARCHAR(100) DEFAULT NULL COMMENT '家庭住址',
`email` VARCHAR(50) DEFAULT NULL COMMENT '邮箱',
PRIMARY KEY (`id`)
)ENGINE=INNODB DEFAULT CHARSET=utf8

```

格式

```sql
CREATE TABLE [IF NOT EXISTS] `表名`（
`字段名` 列类型[属性][索引][注释],
`字段名` 列类型[属性][索引][注释],
...
`字段名` 列类型[属性][索引][注释]
）[表类型][表的字符集设置][注释]

```

常用命令

```sql
SHOW CREATE DATABASE school -- 查看创建数据库的语句
SHOW CREATE TABLE student -- 查看student数据表的定义语句
DESC student -- 显示表的结构

```

### 2.5数据表的类型

```sql
-- 关于数据库引擎
/*
INNODB 默认使用
MYISAM 早些年使用


*/

```

|  | MYISAM | INNODB |
| --- | --- | --- |
| 事务支持 | 不支持 | 支持 |
| 数据行锁定 | 不支持 | 支持 |
| 外键约束 | 不支持 | 支持 |
| 全文索引 | 支持 | 不支持 |
| 表空间的大小 | 较小 | 较大，约为MYISAM的两倍 |

常规使用操作：

*   MYISAM 节约空间，速度较快，
*   INNODB 安全性高，事务处理，多表多用户操作

> 在物理空间存在的位置

所有的数据库文件都存在data目录下，一个文件夹就对应一个数据库

本质还是文件的存储

MySQL 引擎在物理文件上的区别

*   innoDB 在数据库表中，只有一个\*.frm文件，以及上级目录下的ibdata1文件
*   MYISAM 对应的文件
    *   \*.frm - 表结构的定义文件
    *   \*. MYD -数据文件
    *   \*.MYI 索引文件

> 设置数据库字符集编码

```sql
CHARTSET=UTF8


```

不设置的话，会是mysql默认的字符集编码-（不支持中文）

可以在my.ini中配置默认的编码

```sql
character-set-server=utf8


```

### 2.6修改删除表

> 修改

```sql
-- 修改表名 ALTER TABLE 旧表面 AS 新表名
ALTER TABLE student RENAME  AS student1
-- 增加表的字段 ALTER TABLE 表名 ADD 字段名 列属性
ALTER TABLE student1 ADD age INT(11)
-- 修改表的字段（重命名，修改约束）
ALTER TABLE student1 MODIFY age VARCHAR(11)  -- 修改约束
ALTER TABLE student1 CHANGE age age1 INT(1)  -- 字段重命名

-- 删除表的字段
ALTER TABLE student1 DROP age1


```

> 删除

```sql
-- 删除表
DROP TABLE IF EXISTS student1


```

**所有的创建和删除操作尽量加上判断，以免报错**

注意点：

*   \`\` 字段名，使用这个包裹
*   注释 – /\*\*/
*   sql 关键字大小写不敏感，建议写小写
*   所有的符号全部用英文

3、MySQL数据管理
===========

### 3.1外键（了解）

> 方式一：在创建表的时候，增加约束（麻烦，比较复杂）
> 
> ```sql
> CREATE TABLE `grade`(
> `gradeid` INT(10) NOT NULL AUTO_INCREMENT COMMENT '年级id',
> `gradename` VARCHAR(50) NOT NULL COMMENT '年级名称',
> PRIMARY KEY (`gradeid`)
> )ENGINE=INNODB DEFAULT CHARSET=utf8
> 
> -- 学生表的 gradeid 字段 要去引用年级表的gradeid
> -- 定义外键KEY
> -- 给这个外键添加约束（执行引用） references 引用
> CREATE TABLE IF NOT EXISTS `student` (
> `id` INT(4) NOT NULL AUTO_INCREMENT COMMENT '学号',
> `name` VARCHAR(30) NOT NULL DEFAULT '匿名' COMMENT '姓名',
> `pwd` VARCHAR(20) NOT NULL DEFAULT '123456' COMMENT '密码',
> `sex` VARCHAR(2) NOT NULL DEFAULT '男' COMMENT '性别',
> `birthday` DATETIME DEFAULT NULL COMMENT '出生日期',
> `gradeid` INT(10) NOT NULL COMMENT '学生年级',
> `address` VARCHAR(100) DEFAULT NULL COMMENT '家庭住址',
> `email` VARCHAR(50) DEFAULT NULL COMMENT '邮箱',
> PRIMARY KEY (`id`),
> KEY `FK_gardeid` (`gradeid`),
> CONSTRAINT `FK_gardeid` FOREIGN KEY (`gradeid`) REFERENCES `grade` (gradeid)
> )ENGINE=INNODB DEFAULT CHARSET=utf8
> 
> ```

删除有外键关系的表的时候，必须先删除引用的表（从表），再删除被引用的表（主表）

> 方式二： 创建表成功后添加外键

```sql
CREATE TABLE `grade`(
`gradeid` INT(10) NOT NULL AUTO_INCREMENT COMMENT '年级id',
`gradename` VARCHAR(50) NOT NULL COMMENT '年级名称',
PRIMARY KEY (`gradeid`)
)ENGINE=INNODB DEFAULT CHARSET=utf8

-- 学生表的 gradeid 字段 要去引用年级表的gradeid
-- 定义外键KEY
-- 给这个外键添加约束（执行引用） references 引用
CREATE TABLE IF NOT EXISTS `student` (
`id` INT(4) NOT NULL AUTO_INCREMENT COMMENT '学号',
`name` VARCHAR(30) NOT NULL DEFAULT '匿名' COMMENT '姓名',
`pwd` VARCHAR(20) NOT NULL DEFAULT '123456' COMMENT '密码',
`sex` VARCHAR(2) NOT NULL DEFAULT '男' COMMENT '性别',
`birthday` DATETIME DEFAULT NULL COMMENT '出生日期',
`gradeid` INT(10) NOT NULL COMMENT '学生年级',
`address` VARCHAR(100) DEFAULT NULL COMMENT '家庭住址',
`email` VARCHAR(50) DEFAULT NULL COMMENT '邮箱',
PRIMARY KEY (`id`)

)ENGINE=INNODB DEFAULT CHARSET=utf8

-- 创建表的时候没有外键关系
ALTER TABLE `student`
ADD CONSTRAINT `FK_gradeid` FOREIGN KEY (`gradeid`) REFERENCES `grade`(`gradeid`);

-- ALTER TABLE`表`  ADD CONSTRAINT 约束名 FOREIGN KEY（作为外键的列） 引用到哪个表的哪个字段

```

以上的操作都是物理外键，数据库级别外键，不建议使用。（避免数据库过多造成困扰）

**最佳实践**

*   数据库就是单纯的表，只用来存数据，只有行（数据）和列（字段）
*   我们想使用多张表的数据，想使用外键（程序去实现）

### 3.2 DML语言（全记住）

数据库意义：数据存储，数据管理

DML语言：数据操作语言

*   Insert
*   update
*   delete

### 3.3添加

> insert

```sql
-- 插入语句（添加）
-- nsert into 表名（[字段一], [字段二]）values('值1'),('值2')

INSERT INTO `grade` (`gradename`) VALUES('大四')

-- 由于主键自增我们可以省略（如何不写表的字段，他会一一匹配）
INSERT INTO `grade` VALUES('大三')
INSERT INTO `grade` (`gradeid`,`gradename`) VALUES ('大三','null')

-- 一般写插入语句，我们一定要数据和字段一一对应。
-- 插入多个字段
INSERT INTO `grade`(`gradename`) VALUES ('大二'),('大一');


INSERT INTO `student`(`name`) VALUES ('张三')

INSERT INTO `student`(`name`,`pwd`,`sex`) VALUES ('张三','aaaaa','男')
INSERT INTO `student`(`name`,`pwd`,`sex`) 
VALUES ('李四','aaaaa','男'),('王五','23232','女')


```

语法：-- insert into 表名（\[字段一\], \[字段二\]）values(‘值1’),(‘值2’)

注意事项：

1.字段和字段之间用逗号分开

2.字段可以省略，但是后面的值必须一一对应

3.可以同时插入多条数据，VALUES后面的值需要使用，隔开即可

```sql
INSERT INTO `student`(`name`,`pwd`,`sex`) 
VALUES ('李四','aaaaa','男'),('王五','23232','女')


```

### 3.4 修改

> update 修改谁（条件） set 原来的值=新值

```sql
-- 修改学员名字

UPDATE `student` SET `name`='囷' WHERE id =1;
-- 不指定条件的情况下，会改动所有表
UPDATE `student` SET `name`='233'

-- 语法；
-- UPDATE 表名 set column_name,[] = value where 条件


```

条件：where 子句 运算符 id 等于 某个值，大于某个值，在某个区间内修改

操作符返回布尔值

| 操作符 | 含义 | 范围 | 结果 |
| --- | --- | --- | --- |
| \= | 等于 | 5=6 | false |
| != <> | 不等于 | 5！=6 | true |
| \> | 大于 |  |  |
| < | 小于 |  |  |
| \>= |  |  |  |
| <= |  |  |  |
| between and | 在某个范围内，闭合区间 |  |  |
| and | && | 5>1and1>2 | false |
| or | || | 5>1or1>2 | true |

注意：

*   column\_name 是数据库的列，带上\`\`
  
*   条件，是筛选的条件，如果没有指定，则会修改所有的列
  
*   value 是一个具体的值，也可以是一个变量
  
*   多个设置的属性之间，使用英文逗号隔开
  
    ```sql
    UPDATE `student` SET `birthday`=CURRENT_TIME where `name`='李四' AND SEX = '男'
    
    
    ```

### 3.5 删除

> delete 命令

语法 `delete from 表名 [where 条件]`

```sql
-- 删除数据 (避免这样写)
DELETE FROM `student`


-- 删除指定
DELETE FROM `student` where id= 1


```

> TRUNCATE 命令

作用：完全清空一个数据库，表的结构和索引不会变

> delete 和 TRUNCATE 区别

*   相同点： 都能删除数据，都不会删除表结构
*   不同：
    *   TRUNCATE 重新设置自增列 计数器会归零
    *   TRUNCATE 不会影响事务

```sql
-- 测试delete 和 truncate 区别

CREATE TABLE `test`(
`id` INT(4) NOT NULL AUTO_INCREMENT,
`coll` VARCHAR(20) NOT NULL,
PRIMARY KEY (`id`)
)ENGINE=INNODB DEFAULT CHARSET=utf8

INSERT INTO `test`(`coll`) VALUES('1'),('2'),('3')

DELETE FROM `test` -- 不会影响自增

TRUNCATE TABLE `test` -- 自增会归零


```

了解即可：`delete删除的问题` 重启数据库，现象

*   innoDB 自增列会从1开始（存在内存当中，断电即失）
*   MyISAM 继续从上一个自增量开始（存在文件中，不会丢失）

4、DQL查询数据（最重点）
==============

### 4.1DQL

(Data Query Language) :数据查询语言

*   所有的查询操作都用它 Select
*   简单的查询，复杂的查询它都能做
*   **数据库中最核心的语言**
*   使用频率最高的语言

### 4.2指定查询字段

```sql
-- 查询  SELECT 字段 FROM 表

-- 查询指定字段  such as
SELECT `StudentNo`,`StudentName` FROM student

-- 别名，给结果起一个名字 AS   可以给字段起别名 也可以给表起别名
SELECT `StudentNo` AS 学号,`StudentName`AS 学生姓名 FROM student AS S

-- 函数 Concat(a,b)
SELECT CONCAT('姓名：',StudentName) AS 新名字 FROM student


```

语法： `SELECT 字段 ... FROM 表`

> 有时候，列名字不是那么见名知意。我们起别名 AS 字段名 AS 别名 表名 AS 别名

> 去重

作用：去除select语句查询出来的结果中重复的语句，重复的语句只显示一条

```sql
-- 查询一下有哪些同学参加了考试，成绩
SELECT * FROM result -- 查询全部的考试成绩
-- 查询有哪些同学参加了考试
SELECT `studentNo` FROM result 
-- 发现重复数据，去重
SELECT DISTINCT `studentNo` FROM result 


```

> 数据库的列（表达式）

```sql
SELECT VERSION()  --查询系统版本（函数）
SELECT 100*3-1 AS 计算结果 -- 用来计算（表达式）
SELECT @@auto_increment_increment --查询自增的步长（变量）

-- 学员考试成绩+1 分 查看
SELECT `StudentNo`,`StudentResult`+1 AS '提分后' FROM result



```

数据库中的表达式： 文本值，列，Null , 函数，计算表达式，系统变量…

select `表达式` from 表

### 4.3where 条件子句

作用：检索数据中符合条件的值

> 逻辑运算符

| 运算符 | 语法 | 结果 |
| --- | --- | --- |
| and && | a and b a&&b | 逻辑与 |
| or || | a or b a||b | 逻辑或 |
| Not != | not a !a | 逻辑非 |

**尽量使用英文**

```sql
-- 查询考试成绩在95分到100分之间
SELECT `StduentNo`,`StudentResult` FROM result
WHERE StudentResult >=95 AND StudentResult<=100

-- 模糊查询（区间）
SELECT `StduentNo`,`StudentResult` FROM result
WHERE StudentResult BETWEEN 95 AND 100

-- 除了1000号学生之外的同学成绩
SELECT `StduentNo`,`StudentResult` FROM result
WHERE NOT StudentNo = 1000

```

> 模糊查询：比较运算符

| 运算符 | 语法 | 描述 |
| --- | --- | --- |
| I S NULL | a is null | 如果操作符为null 结果为真 |
| IS NOT NULL | a is not null | 如果操作符为not null 结果为真 |
| BETWEEN | a between b and c | 若a在b 和c之间则为真 |
| **LIKE** | a like b | SQL匹配，如果a 匹配到b 则为真 |
| **IN** | a in (a1,a2,a3…) | 假设a 在 a1,a2,a3其中的某一个中，为真 |

```sql
--  查询姓刘的同学
-- like结合 %（代表0到任意字符）  _(一个字符)
SELECT `StudentNo`,`StudentName` FROM `student`
WHERE StudentName LIKE '刘%';

-- 查询姓刘的同学，名字后只有一个字
SELECT `StudentNo`,`StudentName` FROM `student`
WHERE StudentName LIKE '刘_';

-- 查询姓刘的同学，名字后只有两个字
SELECT `StudentNo`,`StudentName` FROM `student`
WHERE StudentName LIKE '刘__';

-- 查询名字中间有嘉字的同学 %嘉%
SELECT `StudentNo`,`StudentName` FROM `student`
WHERE StudentName LIKE '%嘉%';



===================IN(具体的一个或者多个值)===========================
-- 查询1001 1002 1003 学员信息
SELECT `StudentNo`,`StudentName` FROM `student`
WHERE StudentNo = 1001
SELECT `StudentNo`,`StudentName` FROM `student`
WHERE StudentNo = 1002
SELECT `StudentNo`,`StudentName` FROM `student`
WHERE StudentNo = 1003

SELECT `StudentNo`,`StudentName` FROM `student`
WHERE StudentNo IN (1001,1002,1003);

-- 查询在北京的学生
SELECT `StudentNo`,`StudentName` FROM `student`
WHERE `Address` IN('安徽','河南洛阳');


===================NULL NOT NULL===================================
-- 查询地址为空的学生 null ''
SELECT `StudentNo`,`StudentName` FROM `student`
WHERE address=''OR address IS NULL

-- 查询有出生日期的同学  不为空
SELECT `StudentNo`,`StudentName` FROM `student`
WHERE `BornDate` IS NOT NULL;




```

### 4.4 联表查询

> JOIN 对比

![](https://img-blog.csdnimg.cn/20200708013553742.png?x-oss-process=image/watermark,type_ZmFuZ3poZW5naGVpdGk,shadow_10,text_aHR0cHM6Ly9ibG9nLmNzZG4ubmV0L3FxXzMzOTU2NTM2,size_16,color_FFFFFF,t_70)

![](https://img-blog.csdnimg.cn/20200708013558863.png?x-oss-process=image/watermark,type_ZmFuZ3poZW5naGVpdGk,shadow_10,text_aHR0cHM6Ly9ibG9nLmNzZG4ubmV0L3FxXzMzOTU2NTM2,size_16,color_FFFFFF,t_70)

```sql
======================联表查询 join ==============================
-- 查询参加考试的同学 （学号，姓名，考试编号，分数）

SELECT * FROM student 
SELECT * FROM result

/*
1. 分析需求，分析查询的字段来自哪些表
2.确定使用哪种连接查询？7种
确定交叉点（这两个表中哪个数据是相同的）
判断的条件： 学生表中 studentNo = 成绩表中 studentNo 

*/

-- JION（表） ON （判断的条件）连接查询
-- where 等值查询
SELECT studentNo,studentName,SubjectNo,StudentResult
FROM student AS s
INNER JOIN result AS r
WHERE s.studentNo=r.studentNo

--Right Join
SELECT s.studentNo,studentName,SubjectNo,StudentResult
FROM student AS s
RIGHT JOIN result AS r
ON s.studentNo = r.studentNo

--LEFT Join
SELECT s.studentNo,studentName,SubjectNo,StudentResult
FROM student AS s
LEFT JOIN result AS r
ON s.studentNo = r.studentNo



```

| 操作 | 描述 |
| --- | --- |
| Inner join | 如果表中至少有一个匹配，就返回行 |
| left join | 即使左表中没有匹配，也会从左表中返回所有的值 |
| right jion | 即使右表中没有匹配，也会从右表中返回所有的值 |

```sql
-- 查询考的同学
SELECT s.studentNo,studentName,SubjectNo,StudentResult
FROM student AS s
LEFT JOIN result AS r
ON s.studentNo = r.studentNo
WHERE StudentResult IS NULL

-- 查询了参加考试同学的信息：学号：学生姓名：科目名：分数
SELECT s.`studentNo`,`studentName`,`SubjectName`,`studentResult`
FROM student s
RIGHT JOIN result r
ON r.studentNo=s.studentNo
INNER JOIN `subject` sub
ON r.SubjectNo=sub.SubjectNo

-- 我要查询哪些数据 SELECT ....
-- 从哪几个表中查 FROM 表 xxx JOIN 连接的表 ON 交叉条件
-- 假设存在一中多张表查询，先查询两章表，然后再慢慢增加

--FROM a LEFT JOIN b   左为准
--FROM a RIGHT JOIN b	右为准



```

> 自连接

自己的表跟自己的表连接，核心：**一张表拆为两张一样的表**

父类

| categoryid | categoryName |
| --- | --- |
| 2 | 信息技术 |
| 3 | 软件开发 |
| 5 | 美术设计 |

子类

| pid | categoryid | categoryName |
| --- | --- | --- |
| 3 | 4 | 数据库 |
| 2 | 8 | 办公信息 |
| 3 | 6 | web开发 |
| 5 | 7 | ps技术 |

操作：查询父类对应子类关系

| 父类 | 子类 |
| --- | --- |
| 信息技术 | 办公信息 |
| 软件开发 | 数据库 |
| 软件开发 | web开发 |
| 美术设计 | ps技术 |

```sql
-- 查询父子信息

SELECT a.`categroryName` AS `父栏目`,b.`categroryName` AS `子栏目`
FROM `catgroy` AS a,`catgroy` AS b
WHERE a.`categoryid`=b.`pid`

```

```sql
-- 查询学员所属的年级（学号，学生的姓名，年级）
SELECT 	studentNo,studentName,gradeName
FROM student s
INNER JOIN `grade` g
ON s.`GradeId`=g.`GradeId`

```

### 4.5分页和排序

```sql
============================分页 limit 和排序order by=================


-- 排序：  升序ASC  降序  DESC
SELECT  xx
FROM xx
JOIN xx
WHERE  xx
ORDER BY  xx
ASC   ||  DESC


```

> 分页

```sql
-- 为什么要分页
-- 缓解数据库压力，给人的体验更好


-- 分页，每页显示五条数据

-- 语法： limit 当前页，页面的大小
-- limit 0,5 1-5
-- limit 1,5 1-5
-- limit 6,5
SELECT s.`StudentNo`,`StudentName`,`SubjectName`,`StudentResult`
FROM student s
INNER JOIN `result` r
ON s.`StudentNo`=r.`StudentNo`
INNER JOIN `subject` sub
ON r.`subjectNo`=sub.`subjectNo`
WHERE subjectName='数据结构-1'
ORDER BY StudentResult ASC
LIMIT 0,5

-- 第一页 limit 0,5
-- 第二页 limit 5,5
-- 第三页 limit 10,5
-- 第N页 limit 5*（n-1）,5



```

语法 `limit(查询起始下标，pagesize)`

### 4.6 子查询

where (这个值是计算出来的)

本质：`在where语句中嵌套一个子查询语句`

```sql
-- ===========================where=========================

-- 1.查询 数据库结构-1的所有考试结构（学号，科目编号，成绩） 降序
-- 方式一： 连接查询
SELECT `StudentNo`,r.`SubjectName`,`StudentResult`
FROM `result` r
INNER JOIN `subject` sub
ON r.SubjectNo = sun.SubjectNo
WHERE subjectName = '数据库结构-1'
ORDER BY StudentResult DESC

-- 方式二：使用子查询(由里及外)
SELECT `StudentNo`,r.`SubjectName`,`StudentResult`
FROM `result`
WHERE StudentNo=(
	SELECT SubjectNo FROM  `subject` 
    WHERE SubjectName = '数据库结构-1'
)
ORDER BY StudentResult DESC


-- 分数不少于80分的学生的学号和姓名
SELECT DISTINCT s.`StudentNo`,`StudentName`
FROM student s
INNER JOIN result r
ON r.StudentNo = s.StudentNo
WHERE StudentResult>=80

-- 在这个基础上 增加一个科目 ，高等数学-2
SELECT DISTINCT s.`StudentNo`,`StudentName`
FROM student s
INNER JOIN result r
ON r.StudentNo = s.StudentNo
WHERE StudentResult>=80 AND `SubjectNo`=(
    SELECT Subject FROM `subject`
    WHERE SubjectName='高等数学-2'
)

-- 查询课程为 高等数学-2 且分数不小于80分的同学的学号和姓名
SELECT s.`StudentNo`,`StudentName`
FROM student s
INNER JOIN result r
ON s.StudentNo = r.StudentNo
INNER JOIN `subject` sub
ON r.`SubjectName`='高等数学-2'
WHERE `SubjectaName`='高等数学-2' AND StudentResult >=80


-- 再改造 (由里即外)
SELECT `StudentNo`,`StudentName` FROM student
WHERE StudentNo IN(
SELECT StudentNo result WHERE StudentResult >80 AND SubjectNo =(
SELECT SubjectNo FROM `subject` WHERE `SubjectaName`='高等数学-2'
)
)


```

### 4.7 分组

```sql
-- 查询不同课程的平均分，最高分，最低分，平均分大于80
-- 核心：（根据不同的课程分组）

SELECT `SubjectName`,AVG(StudentResult),MAX(StudentResult)
FROM result r
INNER JOIN `Subject` sub
ON r.SubjectNo=sub.SubjectNo

GROUP BY r.SubjectNo -- 通过什么字段来分组
HAVING AVG(StudentResult)>80




```

5、MySQL函数
=========

### 5.1 常用函数

```sql
-- 数学运算

SELECT ABS(-8) -- 绝对值
SELECT CEILING(9.4) -- 向上取整
SELECT FLOOR(9.4)  -- 向下取整
SELECT RAND() -- 返回0-1随机数
SELECT SIGN(-10) -- 判断一个数的符号 0-0 负数返回-1 正数返回1

-- 字符串函数
SELECT CHAR_LENGTH('2323232') -- 返回字符串长度
SELECT CONCAT('我','233') -- 拼接字符串
SELECT INSERT('java',1,2,'cccc') -- 从某个位置开始替换某个长度
SELECT UPPER('abc') 
SELECT LOWER('ABC')
SELECT REPLACE('坚持就能成功','坚持','努力')

-- 查询姓 周 的同学 ，改成邹
SELECT REPLACE(studentname,'周','邹') FROM student
WHERE studentname LIKE '周%'

-- 时间跟日期函数（记住）
SELECT CURRENT_DATE() -- 获取当前日期
SELECT CURDATE() -- 获取当前日期
SELECT NOW() -- 获取当前日期
SELECT LOCATIME()  -- 本地时间
SELECT SYSDATE()  -- 系统时间

SELECT YEAR(NOW())
SELECT MONTH(NOW())
SELECT DAY(NOW())
SELECT HOUR(NOW())
SELECT MINUTE(NOW())
SELECT SECOND(NOW())

-- 系统
SELECT SYSTEM_USER()
SELECT USER()
SELECT VERSION()


```

### 5.2 聚合函数（常用）

| 函数名称 | 描述 |
| --- | --- |
| **COUNT()** | 计数 |
| SUM() | 求和 |
| AVG() | 平均值 |
| MAX() | 最大值 |
| MIN() | 最小值 |
| … |  |

### 5.3 数据库级别MD5加密（拓展）

什么是MD5

主要增强算法复杂度不可逆性。

MD5不可逆，具体的MD5是一样的

MD5破解原理，背后有一个字典，MD5加密后的值，加密前的值

```sql
CREATE TABLE `testmd5`(
`id` INT(4) NOT NULL,
`name` VARCHAR(20) NOT NULL,
`pwd` VARCHAR(50) NOT NULL,
PRIMARY KEY (`id`)

)ENGINE=INNODB DEFAULT CHARSET=UTF8


-- 明文密码
INSERT INTO testmd5 VALUES(1,'张三','123456'),(2,'李四','123456'),(3,'王五','123456')

-- 加密
UPDATE testmd5 SET pwd=MD5(pwd) WHERE id =1
UPDATE testmd5 SET pwd=MD5(pwd) WHERE id !=1  -- 加密全部

-- 插入时加密

INSERT INTO testmd5 VALUES(4,'小明',MD5('123456'))
INSERT INTO testmd5 VALUES(5,'红',MD5('123456'))

-- 如何校验，将用户传递过来的密码，进行MD5加密，然后对比加密后的值
SELECT * FROM testmd5 WHERE `name`='红' AND pwd=MD5('123456')

```

6、事务
====

### 6.1 什么是事务

**要么都成功，要么都失败**

* * *

1.  SQL执行， A给B转账 A 1000–> 200 B200
2.  SQL 执行， B收到A的钱 A800 — B400

* * *

将一组SQL放在一个批次中执行

> 事务原则 ： ACID原则 原子性，一致性，隔离性，持久性 （脏读，幻读…）

**原子性**（Atomicity）

要么都成功，要么都失败

**一致性（Consistency）**

事务前后的数据完整性要保持一致

**持久性（Durability）**–事务提交

事务一旦提交就不可逆转，被持久化到数据库中

**隔离性**

事务产生多并发时，互不干扰

> 隔离产生的问题

### 脏读：

指一个事务读取了另外一个事务未提交的数据。

### 不可重复读：

在一个事务内读取表中的某一行数据，多次读取结果不同。（这个不一定是错误，只是某些场合不对）

### 虚读(幻读)

是指在一个事务内读取到了别的事务插入的数据，导致前后读取不一致。  
（一般是行影响，多了一行）

> 执行事务

```sql
-- mysql 自动开启事务提交
SET autocommit=0 -- 关闭
SET autocommit=1 -- 开启（默认的）

-- 手动处理事务
SET autocommit =0 -- 关闭自动提交

-- 事务开启

START TRANSACTION -- 标记一个事务的开始，从这个之后的SQP都在同一个事务内

INSERT XX
INSERT XX

-- 提交 ： 持久化(成功)
COMMIT 
-- 回滚：  回到原来的样子（失败）
ROLLBACK
-- 事务结束
SET autocommit = 1 -- 开启自动提交
-- 了解
SAVEPOINT 保存点名称 -- 设置一个事务的保存点
ROLLBACK TO SAVEPOINT 保存点名 -- 回滚到保存点
RELEASE SAVEPOINT 保存点 -- 删除保存点


```

\[外链图片转存失败,源站可能有防盗链机制,建议将图片保存下来直接上传(img-DfVvNLP7-1594142971424)(C:\\Users\\53424\\AppData\\Roaming\\Typora\\typora-user-images\\1594012051660.png)\]

> 模拟场景

```sql
CREATE DATABASE shop CHARACTER SET utf8 COLLATE utf8_general_ci
USE shop
CREATE TABLE `account`(
`id` INT(3) NOT NULL AUTO_INCREMENT,
`name` VARCHAR(30) NOT NULL,
`money` DECIMAL(9,2) NOT NULL,
PRIMARY KEY (`id`)
)ENGINE=INNODB DEFAULT CHARSET=utf8

INSERT INTO account(`name`,`money`)
VALUES('A',2000),('B',10000)

-- 模拟转账：事务
SET autocommit = 0; -- 关闭自动提交
START TRANSACTION -- 开启事务（一组事务）
UPDATE account SET money = money-500 WHERE `name` = 'A' -- A 转账给B
UPDATE account SET money = money+500 WHERE `name` = 'B' -- B 收到钱

COMMIT ; -- 提交事务
ROLLBACK ; -- 回滚

SET autocommit=1 -- 恢复默认值


```

7、索引
====

> MySQL索引的建立对于MySQL的高效运行是很重要的，索引可以大大提高MySQL的检索速度。

### 7.1索引的分类

> 在一个表中，主键索引只能有一个，唯一索引可以有多个

*   主键索引 （PRIMARY KEY）
    *   唯一的标识，主键不可重复，只能有一个列作为主键
*   唯一索引 （UNIQUE KEY）
    *   避免重复的列出现，唯一索引可以重复，多个列都可以标识唯一索引
*   常规索引（KEY/INDEX）
    *   默认的，index,key关键字来设置
*   全文索引（FULLTEXT）
    *   在特点的数据库引擎下才有，MyISAM
    *   快速定位数据

```sql
-- 索引的使用
-- 1.在创建表的时候给字段增加索引
-- 2.创建完毕后，增加索引

-- 显示所有的索引信息
SHOW INDEX FROM 表

-- 增加一个索引
ALTER TABLE 表 ADD FULLTEXT INDEX 索引名（字段名）

-- EXPLAIN 分析sql执行状况
EXPLAIN SELECT * FROM student -- 非全文索引




```

### 7.2 测试索引

```sql
CREATE TABLE `app_user` (
`id` BIGINT(20) UNSIGNED NOT NULL AUTO_INCREMENT,
`name` VARCHAR(50) DEFAULT '',
`email` VARCHAR(50) NOT NULL,
`phone` VARCHAR(20) DEFAULT '',
`gender` TINYINT(4) UNSIGNED DEFAULT '0',
`password` VARCHAR(100) NOT NULL DEFAULT '',
`age` TINYINT(4) DEFAULT NULL,
`create_time` DATETIME DEFAULT CURRENT_TIMESTAMP,
`update_time` TIMESTAMP NOT NULL DEFAULT CURRENT_TIMESTAMP ON UPDATE CURRENT_TIMESTAMP,
PRIMARY KEY (`id`)
) ENGINE=INNODB DEFAULT CHARSET=utf8

-- 插入100万数据
DELIMITER $$ --  写函数之前必写
CREATE FUNCTION mock_data()
RETURNS INT 
BEGIN
DECLARE num INT DEFAULT 1000000;
DECLARE i INT DEFAULT 0;

WHILE i<num DO
-- 插入语句
INSERT INTO app_user(`name`,`email`,`phone`,`gender`,`password`,`age`)
VALUE(CONCAT('用户',i),'534240118@qq.com',FLOOR (CONCAT('18',RAND()*9999999)),FLOOR (RAND()*2),
UUID(),FLOOR (RAND()*100));

SET i = i+1;
END WHILE;
RETURN i;


END;

INSERT INTO app_user(`name`,`email`,`phone`,`gender`,`password`,`age`)
VALUE(CONCAT('用户',i),'534240118@qq.com',FLOOR (CONCAT('18',RAND()*9999999)),FLOOR (RAND()*2),
UUID(),FLOOR (RAND()*100))


SELECT mock_data();

SELECT * FROM app_user WHERE `name`='用户9999' -- 接近半秒

EXPLAIN SELECT * FROM app_user WHERE `name`='用户9999'  -- 查询99999条记录

-- id _ 表名_字段名
-- create index on 字段
CREATE INDEX id_app_user_name ON app_user(`name`); -- 0.001 s
EXPLAIN SELECT * FROM app_user WHERE `name`='用户9999'  -- 查询一条记录

```

索引在小数据的时候，用处不大，但是在大数据的时候，区别十分明显

### 7.3 索引原则

*   索引不是越多越好
*   不要对经常变动的数据加索引
*   小数据量的表不需要加索引
*   索引一般加在常用来查询的字段上

> 索引的数据结构

Hash 类型的索引

Btree: 默认innodb 的数据结构

阅读： http://blog.codinglabs.org/articles/theory-of-mysql-index.html

8、权限管理和备份
=========

### 8.1用户管理

> SQLyog 可视化管理

![](https://img-blog.csdnimg.cn/20200708013449970.png?x-oss-process=image/watermark,type_ZmFuZ3poZW5naGVpdGk,shadow_10,text_aHR0cHM6Ly9ibG9nLmNzZG4ubmV0L3FxXzMzOTU2NTM2,size_16,color_FFFFFF,t_70)

> SQL命令操作

用户表：mysql.user

本质：对这张表进行，增删改查

```sql
-- 创建用户  CREATE USER 用户名 IDENTIFIED BY '密码'
CREATE USER sanjin IDENTIFIED BY '123456'

-- 修改密码（修改当前密码）
SET PASSWORD = PASSWORD('111111')


-- 修改密码（修改指定用户密码）

SET PASSWORD FOR sanjin = PASSWORD('111111')


-- 重命名  rename user 原名字 to 新名字
RENAME USER sanjin TO sanjin2

-- 用户授权   ALL PRIVILEGES 全部的权限   库，表
-- ALL PRIVILEGES 除了给别人授权，其他都能干
GRANT ALL PRIVILEGES ON *.* TO sanjin2

-- 查询权限
SHOW GRANTS FOR sanjin2  -- 查看指定用户的权限
SHOW GRANTS FOR root@localhost


-- 撤销权限 REVOKE 哪些权限，在哪个库撤销，给谁撤销
REVOKE ALL PRIVILEGES ON *.* FROM sanjin2

-- 删除用户
DROP USER sanjin2


```

### 8.2 MySQL备份

为什么备份：

*   保证重要数据不丢失
*   数据转移

MySQL数据库备份的方式

*   直接拷贝物理文件
*   在SQLyog这种可视化工具中手动导出
    *   在想要导出的表或者库中，右键选择备份和导出
    *   ![](https://img-blog.csdnimg.cn/20200708013418659.png?x-oss-process=image/watermark,type_ZmFuZ3poZW5naGVpdGk,shadow_10,text_aHR0cHM6Ly9ibG9nLmNzZG4ubmV0L3FxXzMzOTU2NTM2,size_16,color_FFFFFF,t_70)

![](https://img-blog.csdnimg.cn/20200708013426360.png?x-oss-process=image/watermark,type_ZmFuZ3poZW5naGVpdGk,shadow_10,text_aHR0cHM6Ly9ibG9nLmNzZG4ubmV0L3FxXzMzOTU2NTM2,size_16,color_FFFFFF,t_70)

9、规范数据库设计
=========

**当数据库比较复杂的时候，我们就需要设计了**

糟糕的数据库设计：

*   数据冗余，浪费空间
*   数据库插入和删除都会麻烦，异常【屏蔽使用物理外键】
*   程序的性能差

良好的数据库设计：

*   节省内存空间
*   保证数据库的完整性
*   方便我们开发系统

软件开发中，关于数据库的设计

*   分析需求：分析业务和需要处理的数据库的需求
*   概要设计：设计关系图 E-R图

### 9.1设计数据库的步骤

以个人博客为例

*   收集信息，分析需求
  *   用户表（用户登录注销，用户的个人信息，写博客，创建分类）
    *   分类表（文章分类，谁创建的）
    *   文章表（文章的信息）
    *   友链表（友链信息）
    *   自定义表（系统信息，某个关键的字，或者某些主字段）
    *   说说表（发表心情…id ,content ,time）
*   标识实体（把需求落地到每个字段）
*   标识实体之间的关系
  
    *   写博客 user–>blog
    *   创建分类 user–>category
    *   关注 user–>user
    *   友链–>links
    *   评论 user–>user

### 9.2三大范式

为什么需要数据规范化？

*   信息重复
  
*   更新异常
  
*   插入异常
  
*   删除异常
  
    *   无法正常显示异常
*   删除异常
  
    *   丢失有效的信息

> 三大范式

**第一范式**（1NF）

原子性：保证每一列不可再分

**第二范式**（2NF）

前提：满足第一范式

每张表只描述一件事情

**第三范式**（3NF）

前提：满足第一范式和第二范式

第三范式需要确保数据表中的每一列数据都和主键直接相关，而不能间接相关。

（规范数据库的设计）

**规范性和性能的问题**

关联查询的表，不得超过三张表

*   考虑商业化的需求和目标（成本和用户体验） 数据库的性能更加重要
*   再规范性能的问题的时候，需要适当的考虑一下，规范性
*   故意给某些表加一些冗余的字段（从多表，变成单表）
*   故意增加一些计算列（从大数据量降低为小数据量的查询：索引）

10、JDBC(重点)
===========

### 10.1 数据库驱动

驱动：声卡，显卡，数据库

![](https://img-blog.csdnimg.cn/20200708013306539.png?x-oss-process=image/watermark,type_ZmFuZ3poZW5naGVpdGk,shadow_10,text_aHR0cHM6Ly9ibG9nLmNzZG4ubmV0L3FxXzMzOTU2NTM2,size_16,color_FFFFFF,t_70)

我们的程序会通过数据库驱动，和数据库打交道！

### 10.2 JDBC

SUN 公司为了简化开发人员的（对数据库的统一）操作，提供了一个(Java操作数据库的)规范，JDBC

这些规范的实现由具体的厂商去做

对于开发人员来说，我们只需要掌握JDBC的接口操作即可

![](https://img-blog.csdnimg.cn/20200708013314340.png?x-oss-process=image/watermark,type_ZmFuZ3poZW5naGVpdGk,shadow_10,text_aHR0cHM6Ly9ibG9nLmNzZG4ubmV0L3FxXzMzOTU2NTM2,size_16,color_FFFFFF,t_70)

java.sql

javax.sql

还需要导入数据库驱动包

### 10.3 第一个JDBC程序

> 创建测试数据库

```sql
CREATE DATABASE jdbcStudy CHARACTER SET utf8 COLLATE utf8_general_ci;

USE jdbcStudy;

CREATE TABLE `users`(
id INT PRIMARY KEY,
NAME VARCHAR(40),
PASSWORD VARCHAR(40),
email VARCHAR(60),
birthday DATE
);

INSERT INTO `users`(id,NAME,PASSWORD,email,birthday)
VALUES(1,'zhansan','123456','zs@sina.com','1980-12-04'),
(2,'lisi','123456','lisi@sina.com','1981-12-04'),
(3,'wangwu','123456','wangwu@sina.com','1979-12-04')


```

1.创建一个普通项目

2.导入数据库驱动

\[外链图片转存失败,源站可能有防盗链机制,建议将图片保存下来直接上传(img-12VBmers-1594142971429)(C:\\Users\\53424\\AppData\\Roaming\\Typora\\typora-user-images\\1594046904540.png)\]

3.编写测试代码

```java
package com.kuang.lesson01;
//我的第一个JDBC程序

import java.sql.Connection;
import java.sql.DriverManager;
import java.sql.ResultSet;
import java.sql.Statement;

public class JdbcFirstDemo {
    public static void main(String[] args) throws Exception {
        //1. 加载驱动
        Class.forName("com.mysql.jdbc.Driver");//固定写法
        //2. 用户信息和url
        //useUnicode=true&characterEncoding=utf8&&useSSL=true
        String url ="jdbc:mysql://localhost:3306/jdbcstudy?useUnicode=true&characterEncoding=utf8&&useSSL=false";
        String name = "root";
        String password = "123456";

        //3. 连接成功，返回数据库对象  connection代表数据库
        Connection connection= DriverManager.getConnection(url,name,password);
        //4. 执行SQL的对象 statement 执行SQL的对象
        Statement statement = connection.createStatement();

        //5. 执行SQL的对象 去执行SQL   可能存在结果，查看返回结果
        String sql="SELECT * FROM users";
        ResultSet resultSet = statement.executeQuery(sql);//返回的结果集,结果集中封装了我们全部查询的结果
        while(resultSet.next()){
            System.out.println("id+"+resultSet.getObject("id"));
            System.out.println("name+"+resultSet.getObject("NAME"));
            System.out.println("password+"+resultSet.getObject("PASSWORD"));
            System.out.println("email+"+resultSet.getObject("email"));
            System.out.println("birthday+"+resultSet.getObject("birthday"));
        }
        //6. 释放连接
        resultSet.close();
        statement.close();
        connection.close();
    }
}

```

步骤总结：  
1.加载驱动

2.连接数据库 DriverManager

3.获取执行SQL的对象 Statement

4.获得返回的结果集

5.释放连接

> DriverManager

```java
//DriverManager.registerDriver(new com.mysql.jdbc.Driver());
Class.forName("com.mysql.jdbc.Driver");//固定写法
Connection connection= DriverManager.getConnection(url,name,password);

//connection代表数据库
//数据库设置自动提交
//事务提交
//事务回滚
connection.rollback();
connection.commit();
connection.setAutoCommit();

```

> URL

```java
String url ="jdbc:mysql://localhost:3306/jdbcstudy?useUnicode=true&characterEncoding=utf8&&useSSL=false";

//mysql 默认3306
//协议://主机地址:端口号/数据库名？参数1&参数2&参数3

//Oracle   1521
//jdbc:oralce:thin:@localhost:1521:sid


```

> statement 执行SQL的对象 pPrepareStatement 执行SQL的对象

```java
String sql="SELECT * FROM users";//编写Sql

statement.executeQuery();
statement.execute();
statement.executeUpdate();//更新，插入，删除，返回一个受影响的行数


```

> ResultSet 查询的结果集，封装了所以的查询结果

获得指定的数据类型

```java
ResultSet resultSet = statement.executeQuery(sql);//返回的结果集,结果集中封装了我们全部查询的结果
        resultSet.getObject();//在不知道列类型下使用
        resultSet.getString();//如果知道则指定使用
        resultSet.getInt();
        



```

遍历,指针

```java
        resultSet.next(); //移动到下一个
        resultSet.afterLast();//移动到最后
        resultSet.beforeFirst();//移动到最前面
        resultSet.previous();//移动到前一行
        resultSet.absolute(row);//移动到指定行


```

> 释放内存

```java
//6. 释放连接
        resultSet.close();
        statement.close();
        connection.close();//耗资源


```

### 10.4statement对象

**Jdbc中的statement对象用于向数据库发送SQL语句，想完成对数据库的增删改查，只需要通过这个对象向数据库发送增删改查语句即可。** 

Statement对象的executeUpdate方法，用于向数据库发送增、删、改的sq|语句， executeUpdate执行完后， 将会返回一个整数(即增删改语句导致了数据库几行数据发生了变化)。

Statement.executeQuery方法用于向数据库发生查询语句，executeQuery方法返回代表查询结果的ResultSet对象。

> CRUD操作-create

使用executeUpdate(String sql)方法完成数据添加操作，示例操作：

```java
 Statement statement = connection.createStatement();
        String sql = "insert into user(...) values(...)";
        int num = statement.executeUpdate(sql);
        if(num>0){
            System.out.println("插入成功");
        }


```

> CRUD操作-delete

使用executeUpdate(String sql)方法完成数据删除操作，示例操作：

```java
Statement statement = connection.createStatement();
        String sql = "delete from user where id =1";
        int num = statement.executeUpdate(sql);
        if(num>0){
            System.out.println("删除成功");
        }


```

> CURD操作-update

使用executeUpdate(String sql)方法完成数据修改操作，示例操作：

```java
Statement statement = connection.createStatement();
        String sql = "update user set name ='' where name = ''";
        int num = statement.executeUpdate(sql);
        if(num>0){
            System.out.println("修改成功");
        }


```

> CURD操作-read

使用executeUpdate(String sql)方法完成数据查询操作，示例操作：

```java
Statement statement = connection.createStatement();
        String sql = "select * from  user where id =1";
        ResultSet rs= statement.executeQuery(sql);
        if(rs.next()){
            System.out.println("");
        }


```

> 代码实现

1.提取工具类

```java
package com.kuang.lesson02.utils;

import java.io.IOException;
import java.io.InputStream;
import java.sql.*;
import java.util.Properties;

public class JdbcUtils {
    private static String driver = null;
    private static String url = null;
    private static String username = null;
    private static String password = null;
    static {
        try{
            InputStream in = JdbcUtils.class.getClassLoader().getResourceAsStream("db.properties");
            Properties properties = new Properties();
            properties.load(in);
            driver=properties.getProperty("driver");
            url=properties.getProperty("url");
            username=properties.getProperty("username");
            password=properties.getProperty("password");

            //1.驱动只用加载一次
            Class.forName(driver);

        } catch (IOException e) {
            e.printStackTrace();
        } catch (ClassNotFoundException e) {
            e.printStackTrace();
        }
    }


    //2.获取连接
    public static Connection getConnection() throws Exception{
        return DriverManager.getConnection(url, username, password);
    }
    //3.释放资源
    public static void release(Connection conn, Statement st, ResultSet rs) throws SQLException {

        if(rs!=null){
            rs.close();
        }
        if (st!=null){
            st.close();
        }
        if(conn!=null){
            conn.close();
        }

    }
}



```

2.编写增删改的方法，`exectueUpdate`

```java
package com.kuang.lesson02.utils;

import java.sql.Connection;
import java.sql.ResultSet;
import java.sql.Statement;

import static com.kuang.lesson02.utils.JdbcUtils.*;

public class TestInnsert {
    public static void main(String[] args){
        Connection conn =null;
        Statement st = null;
        ResultSet rs =null;



        try {
             conn = getConnection();//获取连接
            st = conn.createStatement();//获取SQL执行对象
            String sql = "INSERT INTO users(id,`NAME`,`PASSWORD`,`email`,`birthday`)" +
                    "VALUES(5,'sanjin','123456','233223@qq.com','2020-01-01')";

            int i = st.executeUpdate(sql);
            if(i>0){
                System.out.println("插入成功");
            }
        JdbcUtils.release(conn,st,rs);
        } catch (Exception e) {
            e.printStackTrace();
        }
    }

}



```

3.查询 `executeQuery`

```java
package com.kuang.lesson02.utils;

import java.sql.Connection;
import java.sql.ResultSet;
import java.sql.SQLException;
import java.sql.Statement;

import static com.kuang.lesson02.utils.JdbcUtils.*;

public class TestInnsert {
    public static void main(String[] args) throws SQLException {
        Connection conn =null;
        Statement st = null;
        ResultSet rs =null;



        try {
             conn = getConnection();//获取连接
            st = conn.createStatement();//获取SQL执行对象
            String sql = "select * from users";
            rs=st.executeQuery(sql);//查询完毕返回结果集

            while (rs.next()){
                System.out.println(rs.getString("NAME"));
            }
        JdbcUtils.release(conn,st,rs);
        } catch (Exception e) {
            e.printStackTrace();
        }finally {
            JdbcUtils.release(conn,st,rs);
        }
    }

}


```

> SQL注入问题

sql存在漏洞，会被攻击导致数据泄露 **SQL会被拼接 or**

```java
package com.kuang.lesson02.utils;

import java.sql.Connection;
import java.sql.ResultSet;
import java.sql.SQLException;
import java.sql.Statement;

import static com.kuang.lesson02.utils.JdbcUtils.getConnection;

public class SQL注入 {
    public static void main(String[] args) {


        //SQL注入
 login("' or '1=1","123456");
    }
    public static void login(String name,String password){


        Connection conn =null;
        Statement st = null;
        ResultSet rs =null;



        try {
            conn = getConnection();//获取连接
            st = conn.createStatement();//获取SQL执行对象
            String sql = "select * from users where `NAME`='"+ name +"'  AND `PASSWORD`='"+ password +"'" ;
            rs=st.executeQuery(sql);//查询完毕返回结果集

            while (rs.next()){
                System.out.println(rs.getString("NAME"));
            }
            JdbcUtils.release(conn,st,rs);
        } catch (Exception e) {
            e.printStackTrace();
        }finally {
            try {
                JdbcUtils.release(conn,st,rs);
            } catch (SQLException throwables) {
                throwables.printStackTrace();
            }
        }
    }
}



```

### 10.5 PreparedStatement对象

PreparedStatement 可以防止SQL注入 ，效率更高。

1.  新增
2.  删除
3.  查询

```java
package com.kuang.lesson03;

import com.kuang.lesson02.utils.JdbcUtils;

import java.sql.Connection;
import java.sql.PreparedStatement;
import java.sql.ResultSet;
import java.sql.SQLException;

public class Test {
    public static void main(String[] args) {
        Connection connection= null;
        PreparedStatement pstm=null;
        try {

            connection = JdbcUtils.getConnection();
            //区别
            //使用问好占位符代替参数
            String sql = "insert into users(id,`NAME`) values(?,?)";
            pstm = connection.prepareStatement(sql);//预编译sql，先写sql然后不执行
            //手动赋值
            pstm.setInt(1,8);
            pstm.setString(2,"SANJIN");

            //执行
            int i = pstm.executeUpdate();
            if (i>0){
                System.out.println("插入成功");
            }
        } catch (Exception e) {
            e.printStackTrace();
        }finally {
            try {
                JdbcUtils.release(connection,pstm,null);
            } catch (SQLException throwables) {
                throwables.printStackTrace();
            }
        }
    }
}


```

防止SQL注入本质，传递字符 带有“ ”，转义字符会被转义

### 10.6 使用IDEA连接数据库

![](https://img-blog.csdnimg.cn/20200708013123797.png?x-oss-process=image/watermark,type_ZmFuZ3poZW5naGVpdGk,shadow_10,text_aHR0cHM6Ly9ibG9nLmNzZG4ubmV0L3FxXzMzOTU2NTM2,size_16,color_FFFFFF,t_70)

连接成功后，可以选择数据库

![](https://img-blog.csdnimg.cn/20200708013148715.png?x-oss-process=image/watermark,type_ZmFuZ3poZW5naGVpdGk,shadow_10,text_aHR0cHM6Ly9ibG9nLmNzZG4ubmV0L3FxXzMzOTU2NTM2,size_16,color_FFFFFF,t_70)

双击数据库

![](https://img-blog.csdnimg.cn/20200708013157507.png?x-oss-process=image/watermark,type_ZmFuZ3poZW5naGVpdGk,shadow_10,text_aHR0cHM6Ly9ibG9nLmNzZG4ubmV0L3FxXzMzOTU2NTM2,size_16,color_FFFFFF,t_70)

更新数据

![](https://img-blog.csdnimg.cn/20200708013204924.png?x-oss-process=image/watermark,type_ZmFuZ3poZW5naGVpdGk,shadow_10,text_aHR0cHM6Ly9ibG9nLmNzZG4ubmV0L3FxXzMzOTU2NTM2,size_16,color_FFFFFF,t_70)

编写sql代码的地方  
![](https://img-blog.csdnimg.cn/20200708013211958.png)

### 10.7 JDBC事务

**要么都成功，要么都失败**

> ACID原则

原子性：要么全部完成，要么都不完成

一致性：结果总数不变

隔离性：**多个进程互不干扰**

持久性：一旦提交不可逆，持久化到数据库了

隔离性的问题：

脏读： 一个事务读取了另一个没有提交的事务

不可重复读：在同一个事务内，重复读取表中的数据，表发生了改变

虚读（幻读）：在一个事务内，读取到了别人插入的数据，导致前后读出来的结果不一致

> 代码实现

1.  开启事务`conn.setAutoCommit(false);`
  
2.  一组业务执行完毕，提交事务
  
3.  可以在catch语句中显示的定义回滚，但是默认失败会回滚
  
    ```java
    package com.kuang.lesson04;
    
    import com.kuang.lesson02.utils.JdbcUtils;
    
    import java.sql.Connection;
    import java.sql.PreparedStatement;
    import java.sql.ResultSet;
    import java.sql.SQLException;
    
    public class Action {
        public static void main(String[] args) {
    
            Connection conn =null;
            PreparedStatement ps = null;
            ResultSet rs = null;
    
            try {
                conn = JdbcUtils.getConnection();
                //关闭数据库的自动提交功能， 开启事务
                conn.setAutoCommit(false);
                //自动开启事务
                String sql = "update account set money = money-500 where id = 1";
                ps =conn.prepareStatement(sql);
                ps.executeUpdate();
                String sql2 = "update account set money = money-500 where id = 2";
                ps=conn.prepareStatement(sql2);
                ps.executeUpdate();
    
                //业务完毕，提交事务
                conn.commit();
                System.out.println("操作成功");
            } catch (Exception e) {
                try {
                    //如果失败，则默认回滚
                    conn.rollback();//如果失败，回滚
                } catch (SQLException throwables) {
                    throwables.printStackTrace();
                }
                e.printStackTrace();
            }finally {
                try {
                    JdbcUtils.release(conn,ps,rs);
                } catch (SQLException throwables) {
                    throwables.printStackTrace();
                }
            }
        }
    }
    
    
    ```

### 10.8数据库连接池

数据库连接–执行完毕–释放

连接–释放 十分浪费资源

**池化技术**： 准备一些预先的资源，过来就连接预先准备好的

常用连接数 100

最少连接数：100

最大连接数 ： 120 业务最高承载上限

排队等待，

等待超时：100ms

编写连接池，实现一个接口 DateSource

> 开源数据源实现(拿来即用)

DBCP

C3P0

Druid: 阿里巴巴

使用了这些数据库连接池之后，我们在项目开发中就不需要编写连接数据库的代码了

> DBCP

需要用到的jar包

dbcp.ar

> C3P0

> 结论

无论使用什么数据源，本质是不变的，DateSource接口不会变，方法就不会变

MySQL必知必会
=========

5-排序检索数据
------------

```mysql
  SELECT products.prod_name 
  FROM table1
  
  limit m,n -- 从m+1条开始，取n条数据
  select aa from table1 order by aa;
  -- 按多个列排序
  select a,b,c from table1 order by b,c;
  select a,b,c from table1 order by b DESC,C;
  
  DESC 只用于位于前面的列名
  
 ASC 升序排列（升序是默认的）
 
 select a from table1 order by a DESC limit 1;
 
 from  - order by - limit;

```

6-过滤数据
--------

```mysql
select - where 子句 指定搜素条件
select a,b from table1 where a =1;
select a,b from table1 where c =1;
select a,b from table1 where a <>1;
单引号 用来限定 字符串
select a,b from table1 where b BETWEEN 5 AND 10;

-- 空值检查
NULL 无值（no value），它与字段包含0、空字符串或仅仅包含空格不同。
select a from table1 where b is null;

```

7-数据过滤
----------

```mysql
-- 组合 WHERE子句
逻辑操作符 
select a,b,c from table1 where a = 100 and b <= 120;
OR操作符告诉DBMS匹配任一条件而不是同时匹配两个条件
select a,b,c from table1 where a = 100 or b <= 120;

SQL（像多数语言一样）在处理OR操作符前，优先处理AND操作符
问题的解决方法是使用圆括号明确地分组相应的操作符

select a,b,c from table1 where (a=100 or b=20)  and c=11;
任何时候使用具有AND和OR操作符的WHERE子句，都应该使用圆括号明确地分组操作符。不要过分依赖默认计算次序
select a,b from table1 where b IN (1,2) order by c;

IN的最大优点是可以包含其他SELECT语句，使得能够更动态地建立WHERE子句

NOT 操作符
select a,b from table1 where b NOT IN (1,2) order by c;


```

8-用通配符进行过滤
--------------

```mysql
-- 什么是通配符、如何使用通配符以及怎样使用LIKE操作符进行通配搜索？

LIKE 操作符
在搜索串中，%表示任何字符出现任意次数
-- 找出所有以词jet起头
select * from table1 where b LIKE 'jet%';
%告诉MySQL接受jet之后的任意字符，不管它有多少字符

根据MySQL的配置方式，搜索可以是区分大小写的
select * from table1 where b LIKE '%jet%';
搜索模式’%jet%’表示匹配任何位置包含文本jet的值，而不论它之前或之后出现什么字符
除了一个或多个字符外，%还能匹配0个字符。%代表搜索模式中给定位置的0个、1个或多个字符
即使是WHERE prod_name LIKE '%'也不能匹配用值NULL作为产品名的行。
null 是 通配符 % 匹配的例外

下划线(_) 通配符：下划线只匹配单个字符而不是多个字符。
_总是匹配一个字符，不能多也不能少
在确实需要使用通配符时 功能代价比较大，花费开销更长
-- 不要过度使用

```

9-用正则表达式进行搜索
----------------

```mysql
LIKE与REGEXP 在LIKE和REGEXP之间有一个重要的差别
LIKE匹配整个列。如果被匹配的文本在列值中出现，LIKE将不会找到它，相应的行也不被返回（除非使用通配符）。而REGEXP在列值内进行匹配，如果被匹配的文本在列值中出现，REGEXP将会找到它，相应的行将被返回。
select a from table1 where a regexp '100|200' order by a;
使用了正则表达式1000|2000。|为正则表达式的OR操作符

select a from table1 where a regexp '[123] Ton' order by a;
使用了正则表达式[123] Ton。[123]定义一组字符，它的意思是匹配1或2或3

为否定一个字符集，在集合的开始处放置一个^即可 
[^123] 匹配除这些字符外的任何东西。

[1-5]定义了一个范围，这个表达式意思是匹配1到5
．匹配任意字符，因此每个行都被检索出来
-- 匹配特殊字符 前面加 双斜杠 \\
了匹配特殊字符，必须用\\为前导。\\-表示查找-, \\．表示查找．
select a from table1 where regexp '\\.' order by a;
 多数正则表达式实现使用单个反斜杠转义特殊字符，以便能使用这些字符本身。但MySQL要求两个反斜杠（MySQL自己解释一个，正则表达式库解释另一个
 -- 重复元字符
 * 0个或者是多个匹配
 + 1个或多个匹配{1,}
 ? 0个或1个匹配{0,1}
 {n} 指定数目的匹配
 {n,} 不少于指定数目的匹配
 {n,m} 匹配数目的范围 
 
 -- 定位符
 ^ 文本的开始
 $ 文本的结尾
 [[:<:]] 词的开始
 [[:>:]] 词的结尾
 
 找到以小数点开始的数
 select a from table1 where a regexp '^[0-9\\.]'
 order by a ;
 ^[0-9\\.]只在．或任意数字为串中第一个字符时才匹配它们
 

```

10-创建计算字段
-------------

```mysql
Concat() 拼接函数
select Concat( a,'(',b,')') from table1 order by a;
Concat()需要一个或多个指定的串，各个串之间用逗号分隔

RTrim()函数去掉值右边的所有空格
Trim()（去掉串左右两边的空格
LTrim()函数去掉值左边的所有空格
 -- 别名  AS
AS vend_title。它指示SQL创建一个包含指定计算的名为vend_title的计算字段
 -- 计算
 select a,b,c,b*c as d
 from table1 
 where a = 100; 
 将结果 b*c  命名为d 的新列输出！
 可以省略FROM子句以便简单地访问和处理表达式
 SELECT 3*2；将返回6, SELECT Trim('abc')；将返回abc，而SELECT Now()利用Now()函数返回当前日期和时间
 

```

11-使用数据处理函数
-------------

```mysql
SQL支持利用函数来处理数据
-- 文本处理函数
select a ,Upper(a) as b from table1 order by a;
Upper()将文本转换为大写
Left() 返回串左边的字符
Length() 返回串的长度
Locate() 找出串的一个子串
Lower() 将串转换为小写
Right() 返回串的右边的字符
Soundex() 返回串的DOUNDEX值
SubString() 返回子串的字符

 -- 使用Soundex()函数进行搜索，它匹配所有发音类似于Y.Lie的联系名
 select a,b from table1 
 where Soundex(b) = Soundex('Y Lie');
 
 日期和时间处理函数

```

\[外链图片转存失败,源站可能有防盗链机制,建议将图片保存下来直接上传(img-uazOJxKB-1613640008235)(C:\\Users\\ye\\AppData\\Roaming\\Typora\\typora-user-images\\image-20210114193737733.png)\]

```mysql
无论你什么时候指定一个日期，不管是插入或更新表值还是用WHERE子句进行过滤，日期必须为格式yyyy-mm-dd
2005年9月1日，给出为2005-09-01

如果要的是日期，请使用Date() 如果你想要的仅是日期，则使用Date()是一个良好的习惯,如果由于某种原因表中以后有日期和时间值,SQL代码也不需要改变。
select a,b from table1 where Date(a)= '2021-01-14';

Year()是一个从日期（或日期时间）中返回年份的函数。类似，Month()从日期中返回月份。因此，WHERE Year(order_date)=2005 AND Month(order_date) = 9
检索出order_date为2005年9月的所有行
select a,b from table1 where Year(b)= 2005 AND Month(b)=9; 

-- 数字处理函数

```

12-汇总数据
-----------

```mysql
-- 介绍什么是SQL的聚集函数以及如何利用它们汇总表的数据。
AVG() 返回某列的平均值
COUNT() 返回某列的行数
MAX() 返回某列的最大值
MIN() 返回某列的最小值
SUM() 返回某列值之和

AVG()可用来返回所有列的平均值，也可以用来返回特定列或行的平均值
select AVG(a) as avg_a from table1;
 -- SELECT语句返回值avg_price，它包含products表中所有产品的平均价格。如第10章所述，avg_price是一个别名
 select AVG(a) as avg_a from table1 where b=1001;
 AVG() 只能用于单个列，为了获得多个列的平均值，必须使用多个AVG()函数
 -- NULL值 AVG()函数忽略列值为NULL的行。
 
 COUNT()确定表中行的数目或符合特定条件的行的数目
 使用COUNT(*)对表中行的数目进行计数，不管表列中包含的是空值（NULL）还是非空值。
 使用COUNT(column)对特定列中具有值的行进行计数，忽略NULL值。
 select COUNT(*) AS num from table1;
 -- 利用COUNT(*)对所有行计数，不管行中各列有什么值。计数值在num中返回
 select COUNT(a) as num_a from table1;
 -- 特定列中具有值的行进行计数，忽略NULL值。
 -- !! NULL值 如果指定列名，则指定列的值为空的行被COUNT()函数忽略，但如果COUNT()函数中用的是星号（*），则不忽略。
 
 MAX()返回指定列中的最大值。MAX()要求指定列名
 select MAX(a) AS a_max from table1;
 -- NULL值 MAX()函数忽略列值为NULL的行
 
 MIN()的功能正好与MAX()功能相反，它返回指定列的最小值。与MAX()一样，MIN()要求指定列名
 select MIN(a) as a_min from table1;
 NULL值 MIN()函数忽略列值为NULL的行。
 
 SUM()用来返回指定列值的和（总计)
 select SUN(a) as a_sum 
 from table1 where b = 1001;
 SUM()也可以用来合计计算值
 select SUN(a * b) as ab_sum from table1 where c = 1001;
 -- 在多个列上进行计算 如本例所示，利用标准的算术操作符，所有聚集函数都可用来执行多个列上的计算
 NULL值 SUM()函数忽略列值为NULL的行
 
 只包含不同的值，指定DISTINCT参数
 ALL为默认 ALL参数不需要指定，因为它是默认行为。如果不指定DISTINCT
 select AVG(DISTINCT a) as avg_a from table1 where b = 1001;
 DISTINCT必须使用列名，不能用于计算或表达式
 取别名 在指定别名以包含某个聚集函数的结果时，不应该使用表中实际的列名

```

13-分组数据
----------

```mysql
-- GROUP BY子句指示MySQL分组数据，然后对每个组而不是整个结果集进行聚集
SELECT A,COUNT(*) AS sh 
FROM TABLE1
GROUP BY A;

-- 事实上，目前为止所学过的所有类型的WHERE子句都可以用HAVING来替代。唯一的差别是WHERE过滤行，而HAVING过滤分组
SELECT A,COUNT(*) AS sh 
FROM TABLE1
GROUP BY A
HAVING COUNT(*) >=2;
-- having 是对分组后的结果进行过滤
-- GROUP BY 分组  ORDER BY 子句排序输出

```

14-使用子查询
---------

```mysql
-- 每个步骤都可以单独作为一个查询来执行。可以把一条SELECT语句返回的结果用于另一条SELECT语句的WHERE子句
-- 子查询是从内向外处理的 在WHERE子句中使用子查询能够编写出功能很强并且很灵活的SQL语句。对于能嵌套的子查询的数目没有限制，不过在实际使用时由于性能的限制，不能嵌套太多的子查询。
-- 不建议使用太多嵌套的子查询

```

15-联结表
-------

```mysql
-- join 联结表
-- 外键为某个表中的一列，它包含另一个表的主键值，定义了两个表之间的关系
-- 由没有联结条件的表关系返回的结果为笛卡儿积。检索出的行的数目将是第一个表中的行数乘以第二个表中的行数

```

16-创建高级联结
---------

```mysql
-- 1.使用表别名
-- 2. 使用不同的联结
 -- 自联结通常作为外部语句用来替代从相同表中检索数据时使用的子查询语句。虽然最终的结果是相同的，但有时候处理联结远比处理子查询快得多
 -- 自联结效果会比 子查询处理更快
 select a1.id,a1.name
 from table1 as p1,table1 as p2
 where p1.id = p2.id
 and p2.name = 'wqwq';
 
 select table1.id,table2.id
 from table1 inner join table2
 on table1.id = table2.id;
 
 	select table1.id,table2.name
 	FROM table1 left outer join table2
 	on table1.id = table2.id;
 	
 	-- 在使用OUTER JOIN语法时，必须使用RIGHT或LEFT关键字指定包括其所有行的表（RIGHT指出的是OUTER JOIN右边的表，而LEFT指出的是OUTER JOIN左边的表
 	
 	-- 最后添加
 	GROUP BY 对结果进行聚合

```

17-组合查询
-------

```mysql
	-- UNION的使用很简单。所需做的只是给出每条SELECT语句，在各条语句之间放上关键字UNION。
	-- 对多条语句进行组合
	UNION指示MySQL执行两条SELECT语句，并把输出组合成单个查询结果集
	UNION必须由两条或两条以上的SELECT语句组成，语句之间用关键字UNION分隔（因此，如果组合4条SELECT语句，将要使用3个UNION关键字
	UNION中的每个查询必须包含相同的列、表达式或聚集函数
	-- 包含或取消重复的行
	包含 union all
	取消重复的行(默认) union 
	-- 只能使用一条ORDER BY子句，它必须出现在最后一条SELECT语句之后。

```

18-全文搜索
-------

**MyISAM** 支持使用全文本搜索

```mysql
	MyISAM 支持全文本搜索
	InnoDB 不支持全文搜索
	-- 第8章介绍了LIKE关键字，它利用通配操作符匹配文本（和部分文本）。使用LIKE，能够查找包含特殊值或部分值的行
	-- 使用全文本搜索时，MySQL不需要分别查看每个行，不需要分别分析和处理每个词。MySQL创建指定列中各词的一个索引，搜索可以针对这些词进行。
	为了使用全文搜索，必须索引被搜索的列
	为了进行全文本搜索，MySQL根据子句FULLTEXT(note_text)的指示对它进行索引
	在定义之后，MySQL自动维护该索引。在增加、更新或删除行时，索引随之自动更新
	使用两个函数Match()和Against()执行全文本搜索
	Match()指定被搜索的列，Against()指定要使用的搜索表达式
	select a
	from table1
	where Match(a) Against('robot');
	
	-- 如果对应表达式在 select 里面
	在SELECT而不是WHERE子句中使用Match()和Against()。这使所有行都被返回（因为没有WHERE子句）。Match()和Against()用来建立一个计算列（别名为rank），此列包含全文本搜索计算出的等级值

```

19-插入数据
-------

```mysql
	inINSERT
	ININSERT是用来插入（或添加）行到数据库表的
	-- 各个列必须以它们在表定义中出现的次序填充
	niinsert into table1
	avVALUES('aa','bb','cc','dd');
	
	ininsert into table1(a,b,c,d)
	avVALUES('aa','bb','cc','dd');

```

```mysql
	INSERT
	INSERT是用来插入（或添加）行到数据库表的
	-- 各个列必须以它们在表定义中出现的次序填充
	insert into table1
	VALUES('aa','bb','cc','dd');
	-- 表名后的括号里明确地给出了列名。在插入行时，MySQL将用VALUES列表中的相应值填入列表中的对应项
	insert into table1(a,b,c,d)
	VALUES('aa','bb','cc','dd');
	-- 总是使用列的列表 一般不要使用没有明确给出列的列表的INSERT语句。使用列的列表能使SQL代码继续发挥作用，即使表结构发生了变化
	插入多行数据
	insert into table1(a,b,c,d)
	VALUES('aa','bb','cc','dd'),
	VALUES('aa','bb','cc','dd');
	-- 因为MySQL用单条INSERT语句处理多个插入比使用多条INSERT语句快。

```

20-更新和删除数据
----------

```mysql
update table1 
set a='12345',b='555'
where b='321';
-- 即使是发生错误，也继续进行更新，可使用IGNORE关键字

delete from table1 
where a = 10086;
-- DELETE删除整行而不是删除列。为了删除指定的列，请使用UPDATE语句
-- 使用TRUNCATETABLE语句，它完成相同的工作，但速度更快（TRUNCATE实际是删除原来的表并重新创建一个表，而不是逐行删除表中的数据）
-- 如果省略了WHERE子句，则UPDATE或DELETE将被应用到表中所有的行


```

21-创建和操纵表
---------

```mysql
-- 不要把NULL值与空串相混淆。NULL值是没有值，它不是空串。如果指定’'（两个单引号，其间没有字符），这在NOT NULL列中是允许的。空串是一个有效的值，它不是无值。NULL值用关键字NULL而不是空串指定
-- 为创建由多个列组成的主键，应该以逗号分隔的列表给出各列名
-- 每个表只允许一个AUTO_INCREMENT列，而且它必须被索引（如，通过使它成为主键)
SELECT_last_insert_id() 此语句返回最后一个AUTO_INCREMENT,用于后续的MySQL语句

-- MySQL与其他DBMS不一样，它具有多种引擎。它打包多个引擎，这些引擎都隐藏在MySQL服务器内 引擎类型可以混用

-- 为更新表定义，可
使用ALTER TABLE语句

-- 删除表
DROP TABLE table1;
删除表之间的区别
TRUNCATE 和DELETE只删除数据， DROP则删除整个表（结构和数据）

-- 重命名表
RENAME TABLE table1 to table2;
-- 将table1 的名字改为 table2

```

22-视图
-----

```mysql
-- 视图是虚拟的表。与包含数据的表不一样，视图只包含使用时动态检索数据的查询
-- 作为视图，它不包含表中应该有的任何列或数据，它包含的是一个SQL查询
为什么使用视图：
1. 重用SQL
2. 简化复杂的SQL操作
3. 保护数据
4. 使用表的组成而不是整个表
-- 视图仅仅是用来查看存储在别处的数据的一种设施
视图用CREATE VIEW语句来创建
使用SHOW CREATE VIEW viewname；来查看创建视图的语句
用DROP删除视图，其语法为DROP VIEW viewname;
直接用CREATE OR REPLACE VIEW 更新视图

 CREATE VIEW viewaa as 
 select a from table1 where a='123';
 
--  视图的另一常见用途是重新格式化检索出的数据
-- 视图非常容易创建，而且很好使用。正确使用，视图可极大地简化复杂的数据处理
视图大多数是不可更新的，因为视图的主要作用的 数据检索
-- 图提供了一种MySQL的SELECT语句层次的封装，可用来简化数据处理以及重新格式化基础数据或保护基础数据

```

23-使用存储过程
---------

```mysql
存储过程简单来说，就是为以后的使用而保存的一条或多条MySQL语句的集合
-- 使用存储过程有3个主要的好处，即简单、安全、高性能

BEGIN和END语句用来限定存储过程体
CREATE PROCEDURE product()
begin
	select avg(a) a aavg
	from table1;
end;
-- 针对两个 ; 的结束标记
-- 解决办法是临时更改命令行实用程序的语句分隔符
DELIMITER //
 -- 告诉命令行实用程序使用//作为新的语句结束分隔符
 那么，如何使用这个存储过程
 call product();  
 -- 执行刚创建的存储过程并显示返回的结果，因为存储过程实际上是一种函数
 
 删除存储过程  
 DROP PROCEDURE product;
 -- 删除刚创建的存储过程。请注意没有使用后面的()，只给出存储过程名。
 也可以加入判断删除
 DROP PROCEDURE IF EXISTS product;
 
 -- 使用参数
 MySQL支持IN（传递给存储过程）、OUT（从存储过程传出，如这里所用）和INOUT（对存储过程传入和传出）
 
-- 所有MySQL变量都必须以 @ 开始
CREATE PROCEDURE produce(
	OUT p1 DECIMAL(8,2),
    OUT p2 DECIMAL(8,2)
)
BEGIN 
	select min(a_price)
	into p1
	from table1;
	select max(a_price)
	into p2
	from table1;
END;
-- 调用此存储过程
CALL produce(@price_low,@price_max);

-- 显示存储过程
select @price_low;

-- 这次使用IN和OUT参数编写
CREATE PROCEDURE produce(
    in onnumber INT,
    out a decimal(8,2)
) 
BEGIN
	SELECT SUN(a * b)
	FROM table1
	where a = onnumber
	INTO a;
END;
-- 为调用这个新存储过程 给函数传递对应的两个参数
CALL produce(2005,@totala);
select @totala;

-- 检查存储过程的CREATE语句
使用SHOW CREATE PROCEDURE 存储名;
-- 获得包括何时、由谁创建等详细信息的存储过程列表
SHOW PROCEDURE STATUS


```

24-使用游标
-------

```mysql
有时，需要在检索出来的行中前进或后退一行或多行。这就是使用游标的原因。游标（cursor）
-- 创建游标 游标用DECLARE语句创建
-- DECLARE语句用来定义和命名游标，这里为ordernumbers。存储过程处理完成后，游标就消失（因为它局限于存储过程）
-- 打开游标
open cursor;
close cursor;
CLOSE释放游标使用的所有内部内存和资源，因此在每个游标不再需要时都应该关闭
隐含关闭，在end 语句时自动关闭
create procedure process()
begin
	declare ordernumber cursor
	for 
	select a from table1;
	-- open the cursor
	open ordernumber;
	-- close the cursor
	close ordernumber;
end;

-- 在一个游标被打开后，可以使用FETCH语句分别访问它的每一行

```

25-使用触发器
--------

```mysql
-- 如果你想要某条语句（或某些语句）在事件发生时自动执行
触发器应该响应的活动（DELETE、INSERT或UPDATE
触发器用CREATE TRIGGER语句创建

```

26-事务处理
-------

```mysql
事务处理（transaction processing）可以用来维护数据库的完整性，它保证成批的MySQL操作要么完全执行，要么完全不执行。
事务处理是一种机制，用来管理必须成批执行的MySQL操作，以保证数据库不包含不完整的操作结果
利用事务处理，可以保证一组操作不会中途停止，它们或者作为整体执行，或者完全不执行（除非明确指示）。如果没有错误发生，整组语句提交给（写到）数据库表。如果发生错误，则进行回退（撤销）以恢复数据库到某个已知且安全的状态。
事务（transaction）指一组SQL语句
回退（rollback）指撤销指定SQL语句的过程；
提交（commit）指将未存储的SQL语句结果写入数据库表
保留点（savepoint）指事务处理中设置的临时占位符（place-holder），你可以对它发布回退（与回退整个事务处理不同）
-- 开始事务
start transaction
-- 回滚
rollback;
ROLLBACK只能在一个事务处理内使用（在执行一条START TRANSACTION命令之后
事务处理用来管理INSERT、UPDATE和DELETE语句。你不能回退SELECT语句。（这样做也没有什么意义。）你不能回退CREATE或DROP操作

般的MySQL语句都是直接针对数据库表执行和编写的。这就是所谓的隐含提交 
-- 自动提交
为了支持回退部分事务处理，必须能在事务处理块中合适的位置放置占位符
savepoint delete1
rollback to delete1;
释放保留点 保留点在事务处理完成（执行一条ROLLBACK或COMMIT）后自动释放。
自MySQL 5以来，也可以用RELEASE SAVEPOINT明确地释放保留点。

-- autocommit标志决定是否自动提交更改，不管有没有COMMIT语句。设置autocommit为0（假）指示MySQL不自动提交更改（直到autocommit被设置为真为止）
set autocommit = 0;

```

