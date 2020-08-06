#数据库
开始学习数据库
1.数据库的基本概念
	存储数据的仓库，是长期存放在计算机内、有组织、可共享的大量数据的集合。 
		数据库中的数据按照一定数据模型组织、描述和存储，具有较小的冗余度，
		较高的独立性和易扩展性，并为各种用户共享，即数据库有永久存储、有
		知识和可共享三个基本特点。
2. MySQL数据库软件
	1. 安装
	2. 卸载
	3. 配置

3. SQL
##数据库的基本概念：
1.数据库的英文单词：DataBase 简称：DB
2.什么数据库：
	*用于存储和管理数据的仓库
	
3.数据库的特点
	1.持久化存储数据的。其实数据库就是一个文件系统
	2.方便存储和管理数据
	3.使用了同一的方式操作数据库-----SQL
4.常见的数据库软件
	* 参见《MySQL基础.pdf》
		
# MySQL数据库软件
1. 安装
	* 参见《MySQL基础.pdf》
2. 卸载
	1. 去mysql的安装目录找到my.ini文件
		* 复制 datadir="C:/ProgramData/MySQL/MySQL Server 5.5/Data/"
	2. 卸载MySQL
	3. 删除C:/ProgramData目录下的MySQL文件夹。
	
3. 配置
	* MySQL服务启动
		1. 手动。
		2. cmd--> services.msc 打开服务的窗口
		3. 使用管理员打开cmd
			* net start mysql : 启动mysql的服务
			* net stop mysql:关闭mysql服务
	* MySQL登录
		1. mysql -uroot -p密码
		2. mysql -hip -uroot -p连接目标的密码
		3. mysql --host=ip --user=root --password=连接目标的密码
	* MySQL退出
		1. exit
		2. quit

	* MySQL目录结构
		1. MySQL安装目录：basedir="D:/develop/MySQL/"
			* 配置文件 my.ini
		2. MySQL数据目录：datadir="C:/ProgramData/MySQL/MySQL Server 5.5/Data/"
			* 几个概念
				* 数据库：文件夹
				* 表：文件
				* 数据：数据
	
# SQL

1.什么是SQL？
	Structured Query Language：结构化查询语言
	其实就是定义了操作所有关系型数据库的规则。每一种数据库操作的方式存在不一样的地方，称为“方言”。
	
2.SQL通用语法
	1. SQL 语句可以单行或多行书写，以分号结尾。
	2. 可使用空格和缩进来增强语句的可读性。
	3. MySQL 数据库的 SQL 语句不区分大小写，关键字建议使用大写。
	4. 3 种注释
		* 单行注释: -- 注释内容 或 # 注释内容(mysql 特有) 
		* 多行注释: /* 注释 */
	
3. SQL分类
	1) DDL(Data Definition Language)数据定义语言
		用来定义数据库对象：数据库，表，列等。关键字：create, drop,alter 等
	2) DML(Data Manipulation Language)数据操作语言
		用来对数据库中表的数据进行增删改。关键字：insert, delete, update 等
	3) DQL(Data Query Language)数据查询语言
		用来查询数据库中表的记录(数据)。关键字：select, where 等
	4) DCL(Data Control Language)数据控制语言(了解)
		用来定义数据库的访问权限和安全级别，及创建用户。关键字：GRANT， REVOKE 等			
## DDL:（操作数据库、表）

1. 操作数据库：CRUD
	1. C(Create):创建
		* 创建数据库：
			* create database 数据库名称;
		* 创建数据库，判断不存在，再创建：
			* create database if not exists 数据库名称;
		* 创建数据库，并指定字符集
			* create database 数据库名称 character set 字符集名;

		* 练习： 创建db4数据库，判断是否存在，并制定字符集为gbk
			* create database if not exists db4 character set gbk;
	2. R(Retrieve)：查询
		* 查询所有数据库的名称:
			* show databases;
		* 查询某个数据库的字符集:查询某个数据库的创建语句
			* show create database 数据库名称;			
		
		
		7.13总结:
			1.简单了解了数据库，学会安装卸载配置MySql
			2.Sql 结构化查询语言
			3.DDl的创建和寻找数据库
			4.并没有动手实践，效率低
7.14 继续学习MySQl中的SQL标准语言 结构化数据语言
	3. U(update) 修改
		*修改数据库的字符集
			*alter datebase 数据库名称 character set 字符集名称
	4.  D(Delete)删除	
		*删除数据库
			*drop database 数据库名称；
		* 判断数据库存在，存在再删除
			* drop database if exists 数据库名称;
	5.使用数据库
		*1.查询当前正在使用的数据库名称
			*select database();
		2.使用数据库
			*use 数据库名称;
		
2.操作表
	1.C()Create 创建
		1.语法：
			create tabal 表名（
				列名1 数据类型，
				列名2 数据类型，
				列名3 数据类型，
				.....
				列名n 数据类型
			）;
			*注意：最后一列，不需要加逗号（，）；
			*数据库类型
			1. int 整数数据类型
				*age int ,
			2. double 小数类型
				* score double(5,2)
			3. date 日期类型 只包含年月日 yyyy-mm-dd
            4.  datetime 日期 包含年月日时分秒	 yyyy-MM-dd HH:mm:ss 		 
		    5. timestamp :时间错类型 包含年月日时分秒  yyyy-MM-dd HH:mm:ss 	
					*如果将来不给这个字段赋值，或者赋值为null,则默认使用系统当前时间来默认赋值
					
			6. varchar :字符串
				name varchar(20);姓名最大20个字符
					* zhangsan 8个字符  张三 2个字符
		
		
	* 创建表
			create table student(
				id int,
				name varchar(32),
				age int ,
				score double(4,1),
				birthday date,
				insert_time timestamp
			);
	* 复制表：
			* create table 表名 like 被复制的表名;		
		
	2.R（Retrieve）查询；
		*查询某个库中所有的表名称
			*show tables;
		*查询表结构
			*desc table 表名;
	3.U(Update):修改
		1.修改表名
			alter table 表名 rename to 新表名；
		2.修改表的字符集
			alter table 表名 character set 字符集名称；
		3.添加一列
			alter table 表名 add 列名 数据类型；
		4.修改列的名称 类型
			alter table 表名 change 列名 新列名 新数据类型；
			alter table 表名 modify 列名 新数据类型；
		5.删除列
			alter table 表名 drop 列名；
	4.D(Delete)删除
		* drop table 表名;
		* drop table  if exists 表名 ;
		
* 客户端图形化工具：SQLYog
##DML:增删改表中的数据
	1.添加数据
		*语法：
			*insert into 表名 （列名1，列名2，..列名n）values)(值1，值2，...值n);
		*注意：
			1.列名和值要一一对应
			2.如果表名不定义列名，则默认为全部；
				insert into 表名 values(值1,值2,...值n);
			3.除了数字类型，其他类型需要使用引号（单双都可以）来包起来
	2. 删除数据：
		* 语法：
			* delete from 表名 [where 条件]
		* 注意：
			1. 如果不加条件，则删除表中所有记录。
			2. 如果要删除所有记录
				1. delete from 表名; -- 不推荐使用。有多少条记录就会执行多少次删除操作
				2. TRUNCATE TABLE 表名; -- 推荐使用，效率更高 先删除表，然后再创建一张一样的表。
	3. 修改数据：
		* 语法：
			* update 表名 set 列名1 = 值1, 列名2 = 值2,... [where 条件];

		* 注意：
			1. 如果不加任何条件，则会将表中所有记录全部修改。		
		
		

## DQL：查询表中的记录
* select * from 表名;			
		
		7.14号总结：
			1.DDl学完了，首先学会了登录MYSQL
			2.知道了增删查改数据库creat，drop，show,set 
			3.使用数据库use ，查询当前正在使用的数据库名称select
			4.知道了增删查改表 creat ，drop，(show,desc,add ,drop,change,modify),drop
			5.DML学完了，首先安装了Solyog
				*1,学会了添加数据（）insert into
				*2,修改数据 uodate
				*3,删除数据，delete from where(条件)；
			SOLyog数据记录： 
						USE db1;
						DESC stu2;
						INSERT INTO stu2 (id,NAME,age,score,birthday) VALUES(1,"卢世伟",19,99.9,'2001-3-2');
						SELECT *FROM stu2;
						INSERT INTO stu2 (id,NAME,age,score,birthday) VALUES(1,"莫宛盈",19,100,'2001-3-2');
						INSERT INTO stu2 (id,NAME,age,score,birthday) VALUES(1,"张哥䢳",19,100,'2001-3-2');
						UPDATE stu2 SET age = 20 WHERE(id=1);
						UPDATE stu2 SET score=20 ;
						DELETE FROM stu2 WHERE(NAME = "张哥䢳");
						TRUNCATE TABLE stu2;


## DQL：查询表中的记录
* select * from 表名;

1. 语法：
	select
		字段列表
	from
		表名列表
	where
		条件列表
	group by
		分组字段
	having
		分组之后的条件
	order by
		排序
	limit
		分页限定


2. 基础查询
	1. 多个字段的查询
		select 字段名1，字段名2... from 表名；
		* 注意：
			* 如果查询所有字段，则可以使用*来替代字段列表。
	2. 去除重复：
		* distinct
	3. 计算列
		* 一般可以使用四则运算计算一些列的值。（一般只会进行数值型的计算）
		* ifnull(表达式1,表达式2)：null参与的运算，计算结果都为null
			* 表达式1：哪个字段需要判断是否为null
			* 如果该字段为null后的替换值。
	4. 起别名：
		* as：as也可以省略
		

3. 条件查询
	1. where子句后跟条件
	2. 运算符
		* > 、< 、<= 、>= 、= 、<>
		* BETWEEN...AND  
		* IN( 集合) 
		* LIKE：模糊查询
			* 占位符：
				* _:单个任意字符
				* %：多个任意字符
		* IS NULL  
		* and  或 &&
		* or  或 || 
		* not  或 !	
		
	2.聚合函数：将一列数据作为一个整体，进行纵向的计算。
		1.count
		2.max
		3.min 
		4.sum
		5.avg
		
		**注意：聚合函数的计算，排除null值
		解决方案：1.选择不包含非空的列进行计算
				  2.ifnull函数
	3.分组查询：
		1.语法：group by 分组字段
		2.注意：	
			1.分组之后查询的子段，聚合函数
			2.where和having的区别？
			 1. 分组之后查询的字段：分组字段、聚合函数
			2. where 和 having 的区别？
			1. where 在分组之前进行限定，如果不满足条件，则不参与分组。having在分组之后进行限定，如果不满足结果，则不会被查询出来
			2. where 后不可以跟聚合函数，having可以进行聚合函数的判断。
		-- 按照性别分组。分别查询男、女同学的平均分

	4. 分页查询
		1. 语法：limit 开始的索引,每页查询的条数;
		2. 公式：开始的索引 = （当前的页码 - 1） * 每页显示的条数
		-- 每页显示3条记录 

		SELECT * FROM student LIMIT 0,3; -- 第1页
		
		SELECT * FROM student LIMIT 3,3; -- 第2页
		
		SELECT * FROM student LIMIT 6,3; -- 第3页

		3. limit 是一个MySQL"方言"
		
##7.19号总结
	1.DDL数据库的，表的curd
	2.DML修改表中的数据
	3.DQL：查询表中的记录
	基础查询
	2.条件查询
			排序查询（where，having）
	3.分组查询 
		group by			
	4.分页查询
		limit方言
		
/*
 7.21号学习开始
*/		
##约束
	*对表中的数据进行限定，保证数据的正确性，有效性和完整性。
	*分类：
		1.主键约束 primary key;
		2.非空约束 not null
		3.唯一约束 unique
		4.外键约束 foreign key
	#非空约束 ：not null,某一列的值不能为空
		1.创建时添加约束
			CREATE TABLE stu (
			id INT ,
			NAME VARCHAR(20) NOT NULL -- 非空约束
		);
		2.创建完表后，添加约束
		ALTER TABLE stu MODIFY NAME VARBINARY(20) NOT NULL;
		3.删除name的非空约束
		ALTER TABLE stu MODIFY NAME VARBINARY(20);
	#唯一约束 ：unique 某一类的值不能重复
		1.注意：
			*唯一约束可以有null值，但是只能有一条记录为null值
		2.在创建表时添加唯一约束
			CREATE TABLE stu (
			id INT ,
			phone_number VARBINARY(20) UNIQUE-- 添加唯一约束
		);

		3.删除唯一约束
			-- 删除唯一约束
			ALTER TABLE stu DROP INDEX phone_number; 
		4.在创建完表后添加唯一约束
			ALTER TABLE stu MODIFY phone_number VARBINARY(20) UNIQUE;-- 添加唯一约束

	#主键约束 primary key;
		1.注意：
			1.含义：非空且唯一
			2.一张表只能有一个字段为主键
			3.主键就是表中记录的唯一标识
		2.在创建表时添加主键约束
			CREATE TABLE stu (
				id INT PRIMARY KEY,-- 添加主键标识
				phone_number VARBINARY(20) 
			);
		3.在创建完表后添加主键标识
			ALTER TABLE stu MODIFY id INT  PRIMARY KEY;
			ALTER TABLE stu ADD PRIMARY KEY(id);
		4.删除主键标识
			ALTER TABLE stu DROP PRIMARY KEY;
			ALTER  TABLE stu MODIFY id INT;
		5.自动增长
			1.概念：如果某一列是自动数值类型，使用 auto_increment 可以来完成值得自动增长
			
			2.在创建表添加主键约束，并且完成主键自增长
				CREATE TABLE stu (
					id INT PRIMARY KEY AUTO_INCREMENT,-- 添加主键标识
					phone_number VARBINARY(20) 
				);

				ALTER TABLE stu MODIFY id INT AUTO_INCREMENT;
			3.删除自动增长
				ALTER TABLE stu MODIFY id INT;

			4. 删除自动增长	
				ALTER TABLE stu MODIFY id INT AUTO_INCREMENT;


#外键约束：foreign key,让表于表产生关系，从而保证数据的正确性。
	1.在创建表时可以添加外键
		CREATE TABLE employee(
			id INT PRIMARY KEY AUTO_INCREMENT,
			NAME VARCHAR(20),
			age INT,
			dep_id INT,-- 外键对应主表的主键
			-- 创建外键约束
			CONSTRAINT emp_depid_fk FOREIGN KEY (dep_id) REFERENCES department (id)
		);
	2.删除外键
		ALTER TABLE employee DROP FOREIGN KEY emp_depid_fk;
	3.创建表之后，添加外键
		ALTER TABLE employee ADD CONSTRAINT emp_depid_fk FOREIGN KEY (dep_id) REFERENCES department (id);
	4.级联操作：
		1.添加级联操作：
					语法：ALTER TABLE 表名 ADD CONSTRAINT 外键名称 
					FOREIGN KEY (外键字段名称) REFERENCES 主表名称(主表列名称) ON UPDATE CASCADE ON DELETE CASCADE  ;			
		2.分类：
					1. 级联更新：ON UPDATE CASCADE 