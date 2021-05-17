1、初试MySQL
=========

JavaEE: 企业级Java开发 Web

前端（页面：展示，数据！）

后台（连接点：连接数据库JDBC、连接前端（控制、控制视图跳转、给前端传递数据））

数据库（存数据、Txt、Excel、World）

*   只会写代码，学好数据库，基本混饭吃~
*   操作系统、数据结构与算法、一个不错的程序员~
*   离散数学、数字电路、体系结构 + 实战经验 高级程序猿~

1.1、为什么学数据库
-----------

1.  岗位需求
2.  大数据时代~ 得数据者得天下~
3.  被迫需求：存数据 去IOE
4.  **数据库是所有软件体系中最核心的存在** DBA

1.2、什么是数据库
----------

数据库（DB、DataBase）

概念：数据仓库、软件、安装在操作系统（window,linux,mac，…）之上~ SQL 可以存储大量的数据，500万条以下~

作用：存储数据、管理数据

1.3、数据库分类
---------

**关系型数据库：** （SQL）

*   MySQL ,Oracle,Sql Server, DB2 ,SQLlite
*   **通过表和表之间，行和列之间的关系进行数据的存储**： 学员信息表，考勤表 …

**非关系数据库：** （NoSQL）Not Only

*   Redis MongDB
*   非关系型数据库，对象存储，通过对象的自身的属性来决定

DBMS（数据库管理系统）

*   数据库的管理软件，科学有效的管理我们的数据 ，维护和获取数据
*   MySQL 数据库管理系统

1.4、MySQL简介
-----------

MySQL是一个**关系型数据库管理系统**

前世：由瑞典MySQL AB 公司开发

今生：属于 [Oracle](https://baike.baidu.com/item/Oracle) 旗下产品

MySQL是最好的 [RDBMS](https://baike.baidu.com/item/RDBMS/1048260) (Relational Database Management System，关系数据库管理系统) 应用软件之一。

开源数据库软件~

体积小、速度快、总体拥有成本低、所有人必须会~

中小型网站、或者大型网站，集群！

**5.7版本 稳定** 8.0

**安装建议**

1.  尽量不要用exe 安装，注册表
2.  尽量压缩包安装~

1.5、安装MySQL
-----------

压缩包[下载地址](https://dev.mysql.com/get/Downloads/MySQL-5.7/mysql-5.7.20-winx64.zip)

[MySQL下载教程](https://blog.csdn.net/weidong_y/article/details/81660958)

1、解压压缩包

2、配置到环境变量 加入到path

3、新建配置文件 mysql 配置文件 my.ini 目录换成自己的，datadir会自动新建

```bash
[mysqld]
basedir=D:\MySQL\mysql-5.7.23-winx64\
datadir=D:\MySQL\mysql-5.7.23-winx64\data\
port=3306
skip-grant-tables

```

4、管理员模式下CMD 并将路径切换到mysql的bin目录下，然后输入 mysqld -install (安装mysql服务)

5、在输入 mysqld --initialize-insecure --user=mysql 初始化数据文件（data）

6、然后再启动mysql （net start mysql）

7、用命令mysql -u root -p进入mysql 管理界面（密码为空） -p后面不要加空格

8、进入界面后修改root密码

update mysql.user set authentication\_string=password(‘123456’) where user=‘root’ and Host=‘localhost’;

最后输入 flush privileges; 刷新权限

9、修改文件 最后的my.ini 最后一句注释

10、重启mysql 即可正常运行 (exit)

net stop mysql

net start mysql

11、两种登录方式 一种 mysql -u root -p(密码) 不安全、另一种 mysql -u root -p 再输入密码 （安全）

可能出现的问题：

1.  缺少组件.dll
2.  命令输出
3.  sc delete mysql 请空服务 （慎重）

1.6 、安全可视化软件（SQLyog）
--------------------

sqlyog软件安装和使用：

[sqlyog实验教程](https://blog.csdn.net/lihua5419/article/details/73881837/#commentBox)

1、新建一个数据库school

2、新建一张表student

每一个sqlyog的执行操作，本质都是mysql语句的操作

查看表：右键 -> 打开表 尝试添加多条信息 刷新 确定

1.7、连接数据库
---------

命令行连接~ mysql -u root -p 连接数据库

– 是sql 的注释

```sql
update mysql.user set authentication_string=password('123456') where user='root' and Host='localhost';
--修改用户密码
flush privileges; --刷新权限
----------------------
--所有语句用 分号 结尾
show databases;  --查看所有的数据库
mysql> use school --切换数据库 使用use 数据库名
Database changed

show tables; -- 查看数据库所有的表
desc(describe) student; -- 查看表结构
create database 表名; --创建一个数据库表

exit; --退出连接
-- 单行注释（SQL 本来的注释）
/**/ 多行注释


```

**数据库** XXX 语言 CRUD 增删改查！~

DDL 定义

DML 操作

DQL 查询

DCL 控制

2、操作数据库
=======

操作数据库 > 操作数据库中的表 > 操作数据库中表的数据

mysql关键字不区分大小写

2.1、操作数据库（了解）
-------------

#### 1、创建数据库

```sql
CREATE DATABASE [IF NOT EXISTS] school;

```

#### 2、删除数据库

```sql
drop database [if exists] xxx;

```

**Delete** ：删除数据表中的行（可以删除某一行，也可以在不删除数据表的情况下删除所有行）删除某一行：  
Delete from 数据表名称 where 列名称=值；  
删除所有行：Delete \* from 数据表名称

**Drop**:删除数据表或数据库，或删除数据表字段  
删除数据库： drop database 数据库名称  
删除数据表：（表的结构、属性、索引也会被删除）

​ use 数据库名称

​ drop table 数据表1名称，数据表2名称

删除数据表字段（列）：

​ use 数据库名称

​ alter table 数据表名称

​ drop column 字段名（列名称）

**Truncate**

Truncate：删除数据表中的数据（仅数据表中的数据，不删除表）。

​ truncate table \[数据表名称\]

​ “ TRUNCATE TABLE语句是一种快速、无日志记录的方法。TRUNCATE TABLE语句与不含有 WHERE 子句的 DELETE 语句在功能上相同。但是，TRUNCATE TABLE语句速度更快，并且使用更少的系统资源和事务日志资源。”

**比较**

删除数据的速度，一般来说: drop> truncate > delete

“与 DELETE 语句相比，TRUNCATE TABLE语句具有以下优点：所用的事务日志空间较少。

DELETE 语句每次删除一行，并在事务日志中为所删除的每行记录一项。TRUNCATE TABLE 通过释放用于存储表数据的数据页来删除数据，并且在事务日志中只记录页释放。使用的锁通常较少。当使用行锁执行 DELETE 语句时，将锁定表中各行以便删除。TRUNCATE TABLE 始终锁定表和页，而不是锁定各行。如无例外，在表中不会留有任何页。

执行 DELETE 语句后，表仍会包含空页。例如，必须至少使用一个排他 (LCK\_M\_X) 表锁，才能释放堆中的空表。如果执行删除操作时没有使用表锁，表（堆）中将包含许多空页。对于索引，删除操作会留下一些空页，尽管这些页会通过后台清除进程迅速释放。

与 DELETE 语句相同，使用 TRUNCATE TABLE语句清空的表的定义与其索引和其他关联对象一起保留在数据库中。

#### 3、使用数据库

```sql
-- ` tab上面的按键，如果表名或者字段名是一个特殊字符，就带这个符号 
use xxx;

```

#### 4、查看数据库

```sql
SHOW DATABASES 
--查看所有的数据库

```

对比SQLyog 的可视化操作、

学习思路：

*   对照可视化记录，查看SQL
*   固定的语法关键字，必须要记住~

2.2、数据库的列类型
-----------

列的数据类型了解：

> 数值

*   tinyint 十分小的数据 1个字节
*   smallint 较小的数据 2个字节
*   mediumint 中等大小的数据 3个字节
*   **int 标准的整数 4个字节 常用的**
*   bigint 较大的数据 8个字节
*   float 浮点数 4个字节
*   double 浮点数 8个字节（精度问题）
*   decimal 字符串形式的浮点数 金融计算的时候，一般是使用decimal

> 字符串

*   char 字符串固定大小的 0~255
*   **varchar 可变字符串 0~65535 常用的 String**
*   tinytext 微型文本 2^8 -1
*   **text 文本串 2^16 -1** 保存大文本

> 时间日期

java.util.Date

*   date YYYY-MM-DD 日期格式
*   time HH: mm : ss 时间格式
*   datetime YYYY-MM-DD HH:mm: ss **最常用的时间格式**
*   **timestamp 时间戳 1970.1.1 到现在的毫秒数！**
*   year 年份表示

> null

*   没有值，未知
*   注意，不要使用Null 进行运算,结果一定为 null

2.3、数据库的字段属性
------------

Unsigned

*   无符号的整数
*   不能声明为负数

zerofill

*   0 填空的
*   不足的位数，使用0来填充

自增

*   通常理解为自增，自动在上一条记录的基础上 +1 （默认）
*   通常用来设计唯一的主键~ index ，必须是整数类型自增
*   可以自定义设计主键自增的起始值和步长

非空 null not null

*   假设设置为 not null ，如果不给它赋值，就会报错！
*   Null 如果不填值，默认就是null~

默认

*   设置默认的值~
*   sex 默认值为 男,不如不指定就会有默认的值

拓展

```sql
/*
每一个表，都必须存在以下五个字段~~
未来做项目用的，表示一个记录存在的意义
id 主键
`version` 乐观锁
is_delete 伪删除
gmt_create 创建时间
gmt_update 修改时间
*/

```

2.4、创建数据表
---------

```sql
-- 使用英文 () ，表的名称 和 字段 精良使用 `` 括起来
-- auto_increment 自增
-- 字符串 使用单引号 括起来，所偶语句后面加 英文的 (,) 最后一个不用加
-- PRIMARY KEY 主键 一般一个表只能有一个唯一的主键
CREATE TABLE  IF NOT EXISTS `student` (
	`id` INT(4) NOT NULL AUTO_INCREMENT COMMENT '学号',
    `name` VARCHAR(30) NOT NULL DEFAULT '匿名' COMMENT '姓名',
    `sex` VARCHAR(2) NOT NULL DEFAULT `女` COMMENT '性别',
    `birthday` DATETIME DEFAULT NULL COMMENT '出生日去',
    `address` VARCHAR(100) DEFAULT NULL COMMENT '家庭地址',
    `email` VARCHAR(50) DEFAULT NULL COMMENT '邮箱'，
    PRIMARY KEY(`id`)
)ENGINE = INNODB DEFAULT CHARSET = utf8

```

格式

```sql
CREATE TABLE [IF NOT EXISTS] `表名`(
	`字段名` 列类型 [属性] [索引] [注释],
    `字段名` 列类型 [属性] [索引] [注释],
    ......
    `字段名` 列类型 [属性] [索引] [注释]
    PRIMARY KEY(`字段名`)
)[表类型] [字符集设置] [注释]

```

查看创建数据库的语句  
**常用命令**

```sql
SHOW CREATE DATABASE school -- 查看创建数据库的语句	逆向操作 查看学习
SHOW CREATE TABLE student --查看 student 数据表的定义语句
DESC student  -- 显示表的结构

```

2.5、数据表的类型
----------

```sql
-- 关于数据库的引擎
/*
INNODB 默认使用~
MYISAM 早期使用的
*/

```

有什么区别？

|  | MYISAM | INNODB |
| --- | --- | --- |
| 事务支持 | 不支持 | 支持 |
| 数据行锁定 | 不支持 | 支持 |
| 外键 | 不支持 | 支持 |
| 全文索引（大段文章，找出某一字段） | 支持 | 不支持 |
| 表空间的大小 | 较小 | 较大，约为2倍 |

INNODB在5.6 之后的版本支持 全英文的索引了  
常规操作使用：

*   MYISAM 节约空间，速度较快
*   INNODB 安全性高，事务的处理，多表多用户操作

> 在物理空间存在的位置

所有数据库文件在 data 下  
本质还是文件的存储！  
MYSQL 引擎在物理文件上的区别

*   INNODB 在数据库表中只有一个 \*.frm 文件，以及上级目录下的 ibdata1 文件
*   MYISAM 对应文件
    *   \*.frm -表结构的定义文件
    *   \*.MYD 数据文件(data)
    *   \*.MYI 索引文件（index）

> 设置数据库表的字符集编码

```sql
CHARSET= utf8

```

不设置的话，会是mysql 的默认的字符集编码 **不支持中文**  
在 my.ini 中配置默认的编码

```sql
character-set-server=utf8

```

建议每个文件都设置，保证通用性

2.6、 修改删除表
----------

```sql
-- 修改表明 ALTER TABLE 旧表名 RENAME AS 新表名
ALTER TABLE teacher RENAME AS teacheraaa
-- 增加表的字段 ALTER TABLE 表名 ADD 字段名 列属性
ALTER TABLE teachaer ADD age INT(11)

-- 修改表的字段 （重命名，修改约束！）
-- 
ALTER TABLE teacher MODIFY age VARCHAR(11)  --修改约束（字符的约束）
ALTER TABLE teacher CHANGE age ageer INT(1)	--字段重命名

--空mysqll表内容常见的有两种方法：一种delete，一种是truncate 。 不带where参数的delete语句可以删除mysql表中所有内容，使用truncate table也可以清空mysql表中所有内容。效率上truncate比delete快，但truncate删除后不记录mysql日志，不可以恢复数据。
-- delete的效果有点像将mysql表中所有记录一条一条删除到删完，而truncate相当于保留mysql表的结构，重新创建了这个表，所有的状态都相当于新表。
-- 删除表的字段
--TRUNCATE [TABLE] tbl_name
ALTER TABLE teacher drop age。 

```

change 用来字段重命名，不能修改字段类型  
modify 不用来字段重命名，只能修改字段类型和约束

```sql
-- 删除表 （将存在的表删除）
DROP TABLE IF EXISIS teacher 
-- 所有的创建&删除操作 都尽量加上判断，以免报错

```

**注意点**

*   \`\` （反引号） 包好字段
*   注释 – /\* \*/
*   SQL 关键字，对大小写敏感
*   所有的符号，使用英文

3、CSV导入数据库
==========

1.大文件导入
-------

```sql
LOAD DATA LOCAL INFILE 'D:/2020-08-12/downloaddata/all_in_one2.csv' INTO TABLE daily_table FIELDS TERMINATED BY ',' ENCLOSED BY '"' LINES TERMINATED BY '\n' IGNORE 1 ROWS;

```

**记得加上 LOCAL 和正斜杠的处理**

2.MySQL 导入数据load data infile用法
------------------------------

**1、load data infield功能：** 

MySQL的一个高效导入数据的方法，它的速度非常快。是MySQL里一款强大的数据导入工具。

2、语法：

load data \[low\_priority\] \[local\] infile ‘file\_name txt’ \[replace | ignore\]  
into table tbl\_name  
\[fields  
\[terminated by’t’\]  
\[OPTIONALLY\] enclosed by ‘’\]  
\[escaped by’’ \]\]  
\[lines terminated by’n’\]  
\[ignore number lines\]  
\[(col\_name, )\]

说明：

load data infile语句从一个文本文件中以很高的速度读入一个表中。使用这个命令之前，mysqld进程（服务）必须已经在运行。为了安全原因，当读取位于服务器上的文本文件时，文件必须处于数据库目录或可被所有人读取。另外，为了对服务器上文件使用load data infile，在服务器主机上你必须有file的权限。

1 如果你指定关键词low\_priority，那么MySQL将会等到没有其他人读这个表的时候，才把插入数据。可以使用如下的命令：  
_**\*load data low\_priority infile “/home/mark/data sql” into table Orders;\***_

2 如果指定local关键词，则表明从客户主机读文件。如果local没指定，文件必须位于服务器上。

3 replace和ignore关键词控制对现有的唯一键记录的重复的处理。如果你指定replace，新行将代替有相同的唯一键值的现有行。如果你指定ignore，跳过有唯一键的现有行的重复行的输入。如果你不指定任何一个选项，当找到重复键时，出现一个错误，并且文本文件的余下部分被忽略。例如：

___\*_\*load data low\_priority infile “/home/mark/data sql” replace into table Orders;\*\*_\*_\*

4 分隔符

（1） fields关键字指定了文件记段的分割格式，如果用到这个关键字，MySQL剖析器希望看到至少有下面的一个选项：  
terminated by：分隔符，意思是以什么字符作为分隔符  
enclosed by：字段括起字符  
escaped by：转义字符

lines terminated by：描述字段的分隔符，默认情况下是tab字符（\\t）  
ignore number lines:用来忽略导入文件的开始的行。例如：number＝1，则忽略导入文件的第一行数据。

___\*_\*例如：load data infile “/home/mark/Orders txt” replace into table Orders fields terminated by’,’ enclosed by ‘"’;\*\*_\*_\*

（2）lines 关键字指定了每条记录的分隔符默认为’\\n’即为换行符

如果两个字段都指定了那fields必须在lines之前。如果不指定fields关键字缺省值与如果你这样写的相同： fields terminated by’\\t’ enclosed by ’ ‘’ ‘ escaped by’\\’

如果你不指定一个lines子句，缺省值与如果你这样写的相同： lines terminated by’\\n’

例如：load data infile “/jiaoben/load.txt” replace into table test fields terminated by ‘,’ lines terminated by ‘/n’;

5 load data infile 可以按指定的列把文件导入到数据库中。 当我们要把数据的一部分内容导入的时候，，需要加入一些栏目（列/字段/field）到MySQL数据库中，以适应一些额外的需要。比方说，我们要从Access数据库升级到MySQL数据库的时候

下面的例子显示了如何向指定的栏目(field)中导入数据：  
___\*_\*load data infile “/home/Order txt” into table Orders(Order\_Number, Order\_Date, Customer\_ID);\*\*_\*_\*

6 当在服务器主机上寻找文件时，服务器使用下列规则：  
（1）如果给出一个绝对路径名，服务器使用该路径名。  
（2）如果给出一个有一个或多个前置部件的相对路径名，服务器相对服务器的数据目录搜索文件。  
（3）如果给出一个没有前置部件的一个文件名，服务器在当前数据库的数据库目录寻找文件。  
例如： /myfile txt”给出的文件是从服务器的数据目录读取，而作为“myfile txt”给出的一个文件是从当前数据库的数据库目录下读取。

3、例子：

(1)建表：

```sql
create table testLoadData(
 id bigint(20) not null auto_increment,
 username char(10) not null,
 age tinyint(3) UNSIGNED not null,
 description  text not null,
 primary key(id),
 unique key(username)
)engine=myisam default charset=utf8;

```

注意：charset为utf8,下面在创建txt时，字符编码应该也为utf8，不然导入数据的中文会出现乱码。

(2)本机创建txt文本，作为导入文件。Mac下存放完整目录如下：/Users/xxx/Downloads/loaddata.txt

其中：xxx是本机名

文件内容为：

```ruby
"李明","20","相貌好，人品好！哈哈"
"黎明","21","人好心善！哈哈"
"李静","20","相貌平常！哈哈"
"赵明","24","很强"
"赵敏","34","XXXXX"
"赵鑫","52","***%*￥*￥*￥*￥"
"钱鑫","45","都是钱啊。。。"
"几米","12","棒棒哒小说家"
"李毅","21","小学同学呢"
"皮皮","52","乖巧的孩子一个"
"周州","96","非常英俊"
"李浩","10","不知道说什么好"
"韦唯","20","美美的的姑娘"
"郑伊","20","的确是好个好人"
"周丽","10","学习很好"
"马青","60","大家的评价很高啊"
"华克","100","威武的不行了"
"邹平邑","63","吃货一个"
"喆力","15","想到的都是吃"

```

(3)sql脚本导数据：

```sql
LOAD DATA local INFILE '/Users/caoxiaohong/Downloads/loaddata.txt' IGNORE INTO TABLE testLoadData 
FIELDS TERMINATED BY ',' ENCLOSED BY '"' LINES TERMINATED BY '\n' ignore 1 lines (username, age, description);

```

(4)查询导入数据：

```sql
select * from testLoadData;

```

### **提升**

之后我找到了一种直接导入文件的方法：在mysql中可以使用：

```sql
LOAD DATA [LOW_PRIORITY | CONCURRENT] [LOCAL] INFILE 'file_name.txt'
[REPLACE | IGNORE]
INTO TABLE tbl_name
[FIELDS
    [TERMINATED BY 'string']
    [[OPTIONALLY] ENCLOSED BY 'char']
    [ESCAPED BY 'char' ]
]
[LINES
    [STARTING BY 'string']
    [TERMINATED BY 'string']
]
[IGNORE number LINES]
[(col_name_or_user_var,...)]
[SET col_name = expr,...)]123456789101112131415

```

LOAD DATA INFILE语句用于高速地从一个**文本文件中**读取行，并装入一个表中。

*   关键字理解：(摘录)
    
*   LOW\_PRIORITY & CONCURRENT
    
    *   LOW\_PRIORITY: LOAD DATA语句的执行被延迟，直到没有其它的客户端从表中读取为止.
    *   CONCURRENT :如果一个MyISAM表满足同时插入的条件（即该表在中间有空闲块），LOADDATA正在执行时，其它线程会从表中重新获取数据。即使没有其它线程在同时使用本表格使用本选项也会略微影响LOAD DATA的性能。
*   LOCAL :
    
    *   如果指定了LOCAL，则被认为与连接的客户端有关,如果指定了LOCAL，则文件会被客户主机上的客户端读取，并被发送到服务器。文件会被给予一个完整的路径名称，以指定确切的位置。如果给定的是一个相对的路径名称，则此名称会被理解为相对于启动客户端时所在的目录,使用了LOCAL 参数，其实会比直接操作数据库文件慢，毕竟每次都会通过mysql客户端来处理文件，再发送给sever 处理。
        
    *   如果LOCAL没有被指定，则文件必须位于服务器主机上，并且被服务器直接读取。当在服务器主机上为文件定位时，服务器使用以下规则：
        
        > 1.  如果给定了一个绝对的路径名称，则服务器使用此路径名称。
        > 2.  如果给定了带有一个或多个引导组件的相对路径名称，则服务器会搜索相对于服务器数据目录的文件。
        > 3.  如果给定了一个不带引导组件的文件名称，则服务器会在默认数据库的数据库目录中寻找文件。
        
*   REPLACE & IGNORE
    
    *   如果您指定了REPLACE，则输入行会替换原有行（换句话说，与原有行一样，对一个主索引或唯一索引具有相同值的行）
    *   如果您指定IGNORE，则把原有行复制到唯一关键字值的输入行被跳过
    *   如果您这两个选项都不指定，则运行情况根据LOCAL关键词是否被指定而定。不使用LOCAL时，当出现重复关键字值时，会发生错误，并且剩下的文本文件被忽略。使用LOCAL时，默认的运行情况和IGNORE被指定时的情况相同；这是因为在运行中间，服务器没有办法中止文件的传输。如果您希望在载入运行过程中忽略外键的限制，您可以在执行LOAD DATA前发送一个  
        SET FOREIGN\_KEY\_CHECKS=0语句
*   LOAD DATA INFILE &SELECT…INTO OUTFILE
    
    *   要从一个表中把数据写入一个文件中，应使用SELECT…INTO OUTFILE。
    *   要读取文件，放回到表中，应使用LOAD DATA INFILE。
*   FIELDS（控制数据格式）和LINES（控制行格式）
    
*   子句的语法对于两个语句是一样的。两个子句都是自选的，但是如果两个都被指定了，FIELDS必须位于LINES的前面。两条语句需要选择其中一条，两条默认执行语句如下：
    
    *   `FIELDS TERMINATED BY '\t' ENCLOSED BY '' ESCAPED BY '\\'`
    *   `LINES TERMINATED BY '\n' STARTING BY '`

例子：

```sql
LOAD DATA INFILE '/tmp/test.txt' INTO TABLE test LINES STARTING BY "xxx";1

```

> xxx”row”,1  
> something xxx”row”,2  
> 得到数据(“row”,1)和(“row”,2)。

4.MYSQL 数据管理
============

4.1外键（了解即可）
-----------

```sql
KEY 'FK_gradeid'(`gradeid`) constraint 'FK_gradeid' KEY(`gradeid`)
REFERENCE `grade`(`gradeid`)
-- 定义外键，给这个外键添加约束（执行引用）

```

删除有外键关系的表时，必须先删除引用别人的表（从表）  
再删除被引用的表（主表）

以上操作都是物理外键，数据库级别的外键，不建议使用（外键的使用容易造成很多困扰，了解即可）  
最佳实践

*   数据库就是单纯的表，只用来存储数据，只有行和列
*   我们要使用多张表的数据，想使用外键，建议通过程序的逻辑来实现

```sql
-- 创建表的时候 没有外键关系
ALTER table `student`
ADD constraint `FK_gradid` FOREIGN key (`gradid`) REFERENCE `grade`(`gradeid`)

```

公式：

```sql
ALTER TABLE 表
add constraint 约束名 foreign key (作为外键的列)
reference `哪个表`(`哪个字段`)

```

4.2 DML 语言（全部记住）
----------------

(data manipulation language)数据操纵语言

DML(Data Manipulation Language)数据操纵语言：  
适用范围：对数据库中的数据进行一些简单操作，如insert,delete,update,select等.

DDL(Data Definition Language)数据定义语言：  
适用范围：对数据库中的某些对象(例如，database,table)进行管理，如Create,Alter和Drop.

数据库意义： 数据存储，数据管理  
DML 语言，数据操作语言

*   INSERT
*   UPDATE
*   DELETE

4.3 添加 insert
-------------

添加，插入语句

```sql
insert into 表名 ([字段1,字段2,...]) values (('值1'),('值2')...) 
( [] ) 中括号内的 内容是可选内容

```

由于 主键自增，所以我们可以省略，如果不写表的字段，他就会一一匹配  
一般写插入语句，我们一定要数据和字段 一一 对应

```sql
-- 插入多个字段
insert into `grade`(`gradename`) values(`大二`),(`大一`);

```

每一个 具体的对象，插入对应属性，都是一个一个对应的  
注意事项

*   字段之间使用英文逗号，隔开
*   字段是可以省略的，但是内部的值要一一对应
*   可以同时插入多条数据，values 后面的值，需要使用时，用 , 隔开即可 values(),(),()…

4.4 修改 update
-------------

```sql
-- update 修改谁 （条件） set 原来的值 = 新值
-- 修改学员的名字
update `student` set `name` = '???' where id = 1;
-- 不添加 where 条件时，不指定条件的情况下，会修改所有的数据、
-- 语法：
update 表名 set colnum_name = value ,[colnum_name = value,....]

```

条件 where 子句 运算符 id 等判断等于某个值，在某区间内修改

**我爱你**

| 操作符 | 含义 | 范围 | 结果 |
| --- | --- | --- | --- |
| \= | 等于 |  |  |
| <> 或 != | 不等于 |  |  |
| \> 或 < | 大于 或 小于 |  |  |
| \>= 或 <= | 大于等于 或 小于等于 |  |  |
| Between … and … | 包含 | beteween 2 and 5 | \[2,5\] 闭区间的范围内 |
| and | 且 |  |  |
| or | 或 |  |  |

**操作符** 返回一个 布尔值  
通过多个条件 定义语句 and or

```sql
-- 语法 :
update 表名 set colnum_name = value,[colnum_name = value] where [条件]

```

**注意点：** 

*   colnum\_name 是数据库的列 ，尽量带上 反引号 \`\`
*   条件筛选的条件，如果没有指定，则会修改所有的列
*   value 是一个具体的值，也可以是一个变量（函数）
*   多个设备的属性之间，使用英文逗号隔开~

4.5 删除 delete
-------------

```sql
 delete 命令
语法： delete from 表名 [where 条件]
delete from `student` where id = 1;

truncate 命令
-- 作用： 完全请空一个数据库表，表的结构和索引约束不会变！
TRUNCATE TABLE "表格名";

```

**delete 和 truncate 区别**

*   相同点： 都能删除数据，都不会删除表结构
*   不同点
    *   truncate 重新设置，自增列 计数器会归零，不会影响事务
    *   delete 不会影响自增列

了解：delete 删除的问题~ 重启数据库现象

*   Innodb 自增列会以1 开始，（存在内存当中的，断电即失）
*   MyISAM 继续上一个自增量开始，（存在文件中，不会丢失）

5.DQL 查询数据（最重点）
===============

5.1 DQL （date query Language：数据查询语言）
------------------------------------

*   所有查询操作都用它 select
*   简单的查询，复杂的查询它都能做~
*   数据库中最核心的语言，最重要的语言
*   使用频率最高的语言

5.2 指定查询字段

```sql
select * from `student`
-- 查询全部的学生，select 字段 from 表
-- 查询指定的字段
select `StudentNo`,`StudentName` FROM student;
-- 别名 ，给结果起名字，也可以给字段或 表 起别名

```

Select 完整的语法

```sql
select [all | distinct]
{* | table.* | [table.field[as alias1][,table.field[as alias2]][,...]]}
from table_name [as table_alias]
[left | right | inner join table_name2] --联合查询
[where ...] -- 指定结果需满足的条件
[GROUP BY ...] -- 指定结果按照那几个字段来分组

concat() 拼接

```

5.2、去重库的表达式
-----------

```mysql
去重 distinct  
重复数据 只显示一条
select version()
select 计算结果
select @@auto_increment_increment  -- 查询自增的步长

-- 模糊查询


```

5.3 聚合函数
--------

```mysql
COUT() 计数
-- 统计表中的数据的行数   查主键最快
select count(student) from student; -- count 指定列 忽略null
select count(*) from student; 	-- 不会忽略 null
select count(1) from student; -- 计算行数 没什么差别

-- 根据不同
GROUP BY 
HAVING ...

WHERE 后面不能使用聚合函数

```

5.4 MD5加密
---------

```mysql
md5() 函数
-- 插入后加密
insert into table1 value(1,'xiaoming',md5('123'))
update table1 set pwd = MD5(pwd)
-- 如何校验 将用户传递进来的密码md5加密然后 比对加密密码

```

5.5、事务
------

```mysql
-- mysql 是默认开启事务自动提交的
set autocommit = 0  关闭
set autocommit = 1  开启事务
START transaction

事务一旦提交 就被持久化了

```

6.索引
====

6.1索引
-----

*   主键索引 primary key
    *   唯一的标识，主键不可重复，只能有一个列作为主键
*   唯一索引 union key
    *   一个表中可以有多个唯一索引，多个列都可以标识
*   常规索引 key / index
    *   默认的 index key 设置
*   全文索引
    *   特定数据引擎 MyISAM

```mysql
show index from table1 
 -- 增加索引
ALTER TABLE 表名 ADD 索引类型 （unique,primary key,fulltext,index）[索引名]（字段名）
alter table table_name add unique (column_list) ;

-- 插入100万条数据
delimiter $$ --

-- 创建索引
create index 索引名 on 表(字段)
索引在小数据量用处不大，但是数据量一大加速明显


```

*   索引不是越多越好
*   不要对经常变动的数据添加索引
*   索引一般加在常用的查询字段上

7.权限管理和备份
=========

备份保证重要的数据不丢失

备份方式

*   直接拷贝data文件
*   在可视化工具中手动导出
*   使用命令行 mysqldump 语法使用
    *   mysqldump -h 主机 -u 用户名 -p 密码 数据库 表名 > 物理磁盘位置/文件名

8.数据库的设计
========

当数据库比较复杂的时候，需要设计数据库

*   节省内存空间
*   保证数据库的完整性
*   方便开发系统
*   分析需求：分析业务和需要处理的数据库需求
*   概要设计：设计关系图 E-R图

**JDBC** （Java操作数据库）
====================

在架构内没有什么是加一层不能解决的

Java.sql javax.sql 数据导入驱动包

*   加载驱动 Class.forName
*   连接数据库 DriverManager
*   获得执行sql 对象 statement
*   获得返回的结果集 resultSet
*   释放连接

```java
package com.weirui;

import java.sql.*;

// 第一个JDBC
public class jdbc01 {
    public static void main(String[] args) throws ClassNotFoundException, SQLException {
        //加载驱动  固定写法，加载驱动
        Class.forName("com.mysql.jdbc.Driver");
        //连接用户信息
        //jdbc:mysql://localhost:3306/数据库名?参数
        //jdbc:oracel:thin:@localhost:1521:sid
        String url = "jdbc:mysql://localhost:3306/book?useUnicode=true" +
                "&characterEncoding=utf-8&useSSL=true";
        String username = "root";
        String pwd = "123456";
        //连接成功,返回数据库对象  
        //Connection 代表数据库能干的 都有对应方法
        Connection connection = DriverManager.getConnection(url,username,pwd);

        // 执行SQL的对象 statement 执行sql的对象
        Statement statement = connection.createStatement();

        // 执行SQL对象去执行 SQL
        String sql = "select * from user";
        //返回结果集 封装我们全部查询出来的结果
        ResultSet resultSet = statement.executeQuery(sql); // 查询操作
        
        while (resultSet.next()){
            // 对应数据库 列名
            System.out.println("name" + resultSet.getObject("name"));
            //getObject 不知道类型的情况下使用
            System.out.println("id" + resultSet.getObject("id"));
            System.out.println("-------");
        }
        // 释放连接
        resultSet.close();
        statement.close();
        connection.close();
    }
}


// 常用对象
statement.execute();  //执行任何操作
statement.executeQuery(); //查询操作
statement.executeUpdate(); //更新 插入 删除

//结果对象
// resultSet 查询结果集
resultSet.next();
resultSet.previous();
resultSet.beforeFirst();
resultSet.absolute(row); //移动到指定行
// 释放资源
resultset.close();
statement.close();
connection.close();

```

注意配置 db.properties 在src 的当前目录下

```java
driver=com.mysql.jdbc.Driver
url = jdbc:mysql://localhost:3306/book?useUnicode=true&characterEncoding=utf-8&useSSL=true
username = root
pwd = 123456
  // TestSelect
package com.weirui.lesson2;

import com.weirui.lesson2.utils.JdbcUtils;

import java.sql.Connection;
import java.sql.ResultSet;
import java.sql.SQLException;
import java.sql.Statement;

public class TestSelect {
    public static void main(String[] args) {
        Connection connection = null;
        Statement statement = null;
        ResultSet resultSet = null;
        try {
            // 获取数据库连接
             connection = JdbcUtils.getConnection();
             // 获得SQL的执行对象
             statement = connection.createStatement();

             String sql = "select * from user";
             // sql 查询
             resultSet = statement.executeQuery(sql);
            while (resultSet.next()){
                // 对应数据库 列名
                System.out.println("name" + resultSet.getObject("name"));
                System.out.println("id" + resultSet.getObject("id"));
                System.out.println("-------");
            }

        } catch (SQLException throwables) {
            throwables.printStackTrace();
        }finally {
            JdbcUtils.release(connection,statement,resultSet);
        }
    }
}

// JdbcUtils.java
package com.weirui.lesson2.utils;

import java.io.InputStream;
import java.sql.*;
import java.util.Properties;

public class JdbcUtils {
    private static String driver = null;
    private static String url = null;
    private static String username = null;
    private static String pwd = null;
    static {
        try {
            // 配置文件  返回输入流
            InputStream in = JdbcUtils.class.getClassLoader().getResourceAsStream("db.properties");
            Properties properties = new Properties();
            properties.load(in);

            driver = properties.getProperty("driver");
            url = properties.getProperty("url");
            username = properties.getProperty("username");
            pwd = properties.getProperty("pwd");

            // 驱动只要加载一次
            Class.forName(driver);
        } catch (Exception e) {

            e.printStackTrace();
        }
    }
    // 获取连接
    public static Connection getConnection() throws SQLException {
        return DriverManager.getConnection(url,username,pwd);
    }

    //释放连接资源
    public static void release(Connection connection, Statement statement, ResultSet resultSet){
        if (resultSet != null){
            try {
                resultSet.close();
            } catch (SQLException throwables) {
                throwables.printStackTrace();
            }
        }
        if (statement != null){
            try {
                statement.close();
            } catch (SQLException throwables) {
                throwables.printStackTrace();
            }
        }

        if (connection != null){
            try {
                connection.close();
            } catch (SQLException throwables) {
                throwables.printStackTrace();
            }
        }

    }
}


```

SQL**注入问题**
-----------

不合法的输入数据没有过滤，对应添加额外语句，欺骗服务器  
sql会被拼接 or 的拼接情况

select \* from user where username = ‘qqq’ or ‘1=1’ and pwd = ‘123’ or ‘1=1’;

对特定语句进行拼接

PrepareStatement 对象
-------------------

**可以防止sql 注入**，并且效率更高

```java
package com.weirui.lesson3;

import com.weirui.lesson2.utils.JdbcUtils;

import java.sql.*;

public class TestInsert {
    public static void main(String[] args) {
        Connection connection = null;
        PreparedStatement preparedStatement = null;

        try {
            connection = JdbcUtils.getConnection();
            // 有所区别 不同之处 更安全并且避免 sql 注入
            // 需要先写sql 预编译sql 然后不执行 使用？占位符代替参数
            String sql = "insert into user(id,pwd,name,class,status,admin,last_login_time)" +
                    "values(?,?,?,?,?,?,?)";
            preparedStatement = connection.prepareStatement(sql);
            //手动赋值参数
            preparedStatement.setInt(1,111111);
            preparedStatement.setInt(2,123456);
            preparedStatement.setString(3,"小老虎");
            preparedStatement.setString(4,"终极一班");
            preparedStatement.setInt(5,1);
            preparedStatement.setInt(6,1);
            // sql.Date  数据库用的  util.Data 传入一个时间戳
            preparedStatement.setDate(7,new java.sql.Date(new java.util.Date().getTime()));
            // 执行
            int i = preparedStatement.executeUpdate();
            if (i > 0){
                System.out.println("插入成功");
            }

        } catch (SQLException throwables) {
            throwables.printStackTrace();
        }finally {
            JdbcUtils.release(connection,preparedStatement,null);
        }
    }
}


```

PreparedStatement 防止注入的本质：把传递进来的参数当作字符，假设其中存在转义字符，就直接忽略，会被直接转义

JDBC事务
------

要么都成功要么都失败

ACID 原子隔离一致持久  
隔离性问题： 脏读 不可重复读 幻读

```java
try{
// 关闭数据库的自动提交，会开启事务
	conn.setAutoCommit(false);
    sql;
    sql;
    conn.commit();
}catch(SQLException e){
    conn.rollback();
}finally{
    // 释放连接
}

```

数据库连接池
------

*   数据库连接 – 执行完毕 – 释放 连接 – 释放 十分浪费系统资源
*   池化计数：准备一些预先的资源，过来就连接预先准备好的
*   常用连接数 10 最小连接数 最大连接数
*   排队等待
*   等待超时：100ms

编写连接池，只需要一个接口 DataSource

> 开源数据库实现

DBCP：主流

```java
#连接设置
driverClassName=com.mysql.jdbc.Driver
url=jdbc:mysql://localhost:3306/jdbcstudy?useUnicode=true&characterEncoding=utf8&useSSL=true
username=root
password=123456

#<!-- 初始化连接 -->
initialSize=10

#最大连接数量
maxActive=50

#<!-- 最大空闲连接 -->
maxIdle=20

#<!-- 最小空闲连接 -->
minIdle=5

#<!-- 超时等待时间以毫秒为单位 6000毫秒/1000等于60秒 -->
maxWait=60000
#JDBC驱动建立连接时附带的连接属性属性的格式必须为这样：【属性名=property;】
#注意："user" 与 "password" 两个属性会被明确地传递，因此这里不需要包含他们。
connectionProperties=useUnicode=true;characterEncoding=UTF8

#指定由连接池所创建的连接的自动提交（auto-commit）状态。
defaultAutoCommit=true

#driver default 指定由连接池所创建的连接的只读（read-only）状态。
#如果没有设置该值，则“setReadOnly”方法将不被调用。（某些驱动并不支持只读模式，如：Informix）
defaultReadOnly=

#driver default 指定由连接池所创建的连接的事务级别（TransactionIsolation）。
#可用值为下列之一：（详情可见javadoc。）NONE,READ_UNCOMMITTED, READ_COMMITTED, REPEATABLE_READ, SERIALIZABLE
defaultTransactionIsolation=READ_UNCOMMITTED

```

C3P0

Druid: 阿里巴巴

使用这些数据库连接池之后，在项目开发中就不需要编写连接数据库的代码了

需要导入不同需求的jar包，无论使用什么数据源，DataSoure接口不会变，方法就不会变

MySQL必知必会
=========

第五章 - 排序检索数据
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

第六章-过滤数据
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

第七章 - 数据过滤
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

第八章 - 用通配符进行过滤
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

第九章 - 用正则表达式进行搜索
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

第10章 - 创建计算字段
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

第11章 使用数据处理函数
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

第12章 - 汇总数据
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

第13 - 分组数据
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

14-章使用子查询
---------

```mysql
-- 每个步骤都可以单独作为一个查询来执行。可以把一条SELECT语句返回的结果用于另一条SELECT语句的WHERE子句
-- 子查询是从内向外处理的 在WHERE子句中使用子查询能够编写出功能很强并且很灵活的SQL语句。对于能嵌套的子查询的数目没有限制，不过在实际使用时由于性能的限制，不能嵌套太多的子查询。
-- 不建议使用太多嵌套的子查询

```

15章-联结表
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