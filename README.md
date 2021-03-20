# SQL

结构化查询语言(Structured Query language)，是一种用与数据库查询、存储、更新、管理的编程语言。

## 运行MySQL ##

验证MySQL是否安装正确，可以通过在命令提示符（在主界面运行cmd）中输入`mysql -u root -p`，正确安装下会链接到MySQL服务器，同时提示`mysql>`

## 定义数据对象语句 ##
### 创建 ###
* 创建数据库  
`CREATE DATABASE 数据库名;`
  *  `CREATE DATABSE 王者荣耀;`  
   
   ![1](https://user-images.githubusercontent.com/73262817/111869273-8946b680-89b9-11eb-960d-bb23bf6188d5.PNG)
 
 * 创建列表  
  `CREATE TABLE 列表名(字段1，字段2...);`  
   * `CREATE TABLE hero_1( 
     hero_id INT,
     hero_name VARCHAR(20),
     profession VARCHAR(20)
     );`  
     * int 整数  
     * double 双精度
     * varchar 字符串  
     * data 时间  

![捕获123](https://user-images.githubusercontent.com/73262817/111870245-84383600-89be-11eb-9a52-fb414f7d2c75.PNG)

### 数据库和列表的删除 ###
 * 删除表  
  `DROP TABLE IF EXISXS 表名;`  
  如果表名存在就删除，也可以不加if exist  
  
 * 删除数据库  
  `DROP DATABASE 库名;`  
  
### 修改列表结构 ###
* 添加列名  
 `ALTER TABLE 表名 ADD 列名 类型;`  
 `alter table hero_1 add position VARCHAR(20);`  

![image](https://user-images.githubusercontent.com/73262817/111870597-9dda7d00-89c0-11eb-9741-e47dbb1f8ad6.png)

* 修改列类型  
`ALTERT TABLE 表名 MODIFY 列名 类型;'  

* 删除列 
`ALTER TABLE 表名 DROP 列名;`  

* 修改表名  
`REANME TABLE 表名 TO 新表名;'  


## 数据操作语言 ##



* 全部查询  
`SELECT * FROM 表名;`
*表示所有列  

* 条件查询  
`SELECT * FROM 表名 WHERE 列名1 >= n AND 列名2 <= m;`    
用来查找列1值大于等于n且列2值小于等于m的记录  
逻辑连接词还有`NOT`,`OR`。如果不加括号，优先级为not>and>or

* 投影查询  
`SELECT 列名1 别名1，列名2，列名3 FROME 表名；`
返回结果为只包括所选取的三列的二位表结构，其中列名1被别名替代（不用改别名可以空着） 

* 排序  
`SELECT 列名1，列名2， 列名3 FROM 表名 ORDER BY 列名1，列名2 (DESC);`  
将列名123从高到低排序，先比较列名1，相同时比较列2值大小  
加上DESC表示倒序

* 分页查询  
`LIMIT M OFFSET N;`  
用于数据量大，想分页显示的时候  
M表示每次显示最大的条数，N表示从第（N+1）条开始  
（例如 `LIMIT 3 OFFSET 0；`表示从第1条数据开始显示，最多显示3条）

* 聚合查询  
`SELECT COUNT(*) FROM 表名；`  
查询表的全部行数  
`SELECT COUNT(*) 别名 FROM 表名 WHERE 列名1 >= n ;`  
带条件的聚合查询，同时命名新的列名为别名  
  * 其他查询法   
    `SUM` 计算列合计值，该列必须为数值类型  
    `AVG` 计算列平均值，同样要求数值类型   
    `MAX` 计算列最大值    
    `MIN` 计算列最小值    

  * 分组聚合    
    `SELECT 列名1，COUNT（*） num FROM 表名 GROUP BY 列名1;`  
    把列名1中值相同的项数量加总，显示为num

* 多表查询    
`SELECT * FROM 表名1，表名2;`  
结果为一个二维表，行是表1表2行数的乘积，列是表1表2列并列。   

## 修改数据 ##
* INSERT  
`INSERT INTO <表名> (字段1, 字段2, ...) VALUES   
(值1, 值2, ...),  
(值1,值2,...);`
在表中插入新记录，值123分别对应字段123的位置，一次可以添加多个。。

* UPDATE
`UPDATE <表名> SET 字段1=值1, 字段2=值2, ... WHERE ...;`
更新字段1为值1..，条件为WHERE之后的语句（例如ID = 1）    
  * tips  
  1.利用where语句可以同时更新多条记录  
  2.SET之后的赋值语句可以在原来的基础上改动    
  例如`UPDATE students SET score=score+10 WHERE score<80;`  

* DELETE  
`DELETE FROM <表名> WHERE ...;`
从表中删除WHERE之后的判断内容

## MySQL语句 ##
* 列出所有表  
`SHOW TABLES;`

* 查看表的结构命令  
`DESC 表名；`

* 创建表  
  `CREATE TABLE 表名;`
* 删除表  
  `DROP TABLE 表名;`
* 删除列  
  `ALTER TABLE 表名 DROP CULUMN 列名;`
* 退出  
   `EXIT`
   
## SQL实用语句 ##
* 插入或替换  
`REPLACE INTO students (字段1，字段2...) VALUES (值1，值2,...);`  
如果原记录存在，就会删除原记录替换为新记录
* 插入或更新  
`INSERT INTO students (字段1，字段2...) VALUES (值1，值2,...) ON DULICATE KEY UPDATE 字段名1 = 值1，字段名2 = 值2...;`  
若记录不存在，则插入新记录，否则，字段1为值1的记录会被update之后的内容更新  

* 插入或忽略  
`INSERT IGNORE INTO students (字段1，字段2...) VALUES (值1，值2,...);`  
若记录存在，则忽略，什么也不会发生
* 快照  
`CREATE TABLE 新表名 SELECT * FROM 原表名 WHERE 字段1 = 1;`   
用于复制当前表的部分或全部数据到新表

* 强制使用锁定指引  
`SELECT * FROM 表名 FORCE INDEX （字段名）;`  
强制系统使用（字段名）进行索引，前提是索引必须存在

# 参考资料 #
[1]廖雪峰.廖雪峰SQL教程[EB/OL].https://www.liaoxuefeng.com/wiki/1177760294764384,2021-3-20.
