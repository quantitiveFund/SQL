# SQL

![image](https://user-images.githubusercontent.com/73262817/113993950-88ea5e80-9887-11eb-8361-fe91d368454f.png)


结构化查询语言(Structured Query language)，是一种用与数据库查询、存储、更新、管理的编程语言。

## 数据库本质

按照特定格式储存数据的文件系统

![image](https://user-images.githubusercontent.com/73262817/114022733-aaa60e80-98a4-11eb-82c9-6f7ce4f61309.png)

## 运行MySQL ##

验证MySQL是否安装正确，可以通过在命令提示符（在主界面运行cmd）中输入`mysql -u root -p`，正确安装下会链接到MySQL服务器，同时提示`mysql>`

## 定义数据对象语句 ##
### 数据库和列表的创建 ###
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
  
  * `alter table hero_1 add position VARCHAR(20);`  

![image](https://user-images.githubusercontent.com/73262817/111870597-9dda7d00-89c0-11eb-9741-e47dbb1f8ad6.png)

* 修改列类型    

`ALTERT TABLE 表名 MODIFY 列名 类型;`  

* 删除列  

`ALTER TABLE 表名 DROP 列名;`  
  
  * `alter table hero_1 drop position;`  

![image](https://user-images.githubusercontent.com/73262817/111870907-463d1100-89c2-11eb-8fdb-a1ad0c7f2fa5.png)

* 修改表名   

`REANME TABLE 表名 TO 新表名;`  


## 数据操作语言 ##
* 插入段名  

`INSERT INTO 表名 (字段1，字段2，字段3，...) VALUES (值1，值2，值3...);`  
   
   * 输入数据 
```
   insert into hero_1(hero_id,hero_name,profession) VALUES
    (1,'李白','刺客'),   
    (2,'鲁班七号','射手'),
    (3,'吕布','战士'),
    (4,'安琪拉','法师'),   
    (5,'马超','战士'),
    (6,'马可波罗','射手'),  
    (7,'露娜','刺客'),  
    (8,'诸葛亮','法师 ),  
    (9,'司马懿','法师'),  
    (10,'澜','刺客');
 
 ```

![image](https://user-images.githubusercontent.com/73262817/111871084-5dc8c980-89c3-11eb-9984-ee92ae2a004c.png)

* 更新数据  
 
 `UPDATE <表名> SET 字段1=值1, 字段2=值2, ... WHERE ...;`   
  
  * `update hero_1 SET profession = '法师' where hero_name = '露娜';`
 
 ![image](https://user-images.githubusercontent.com/73262817/111872942-ed24ab80-89c8-11eb-8899-a496009edf56.png)
  
  * tips  
  
  1.利用where语句可以同时更新多条记录  
  2.SET之后的赋值语句可以在原来的基础上改动    

* 删除数据  

`DELETE FROM 表名 WHERE 字段 = 值;`  
  
  * `delete from hero_1 where hero_name = '露娜';  
 
 ![image](https://user-images.githubusercontent.com/73262817/111873124-bf8c3200-89c9-11eb-8ea5-d440ec0fafce.png)
## 数据查询语言SELECT ##

以下图的movie_data表格为例

![image](https://user-images.githubusercontent.com/73262817/113719991-c84a6b00-9720-11eb-8f9c-17449ae66fce.png)

* 全部查询  

`SELECT * FROM 表名;`
  
  * `SELECT * FROM movie_data;`  

 ![image](https://user-images.githubusercontent.com/73262817/113720011-cc768880-9720-11eb-974c-35b00db7e98c.png)

* 条件查询  

`SELECT * FROM 表名 WHERE 列名1 >= n AND 列名2 <= m;`    

用来查找列1值大于等于n且列2值小于等于m的记录  
注意where要直接接在from后面  
逻辑连接词还有`NOT`,`OR`。如果不加括号，优先级为not>and>or  
  
  * `SELECT * FROM movie_data WHERe Director = 'Christopher Nolan';`  
 
  ![image](https://user-images.githubusercontent.com/73262817/113714915-7f43e800-971b-11eb-8019-924e8d9d5a3b.png)

* 去除值重复  
  
  ` SELECT DISTINCT 列名 FROM 表名;`
  
  * `SELECT DISTINCT Director from movie_data;`  
  查询数据库中所有存在的导演  
  
  ![image](https://user-images.githubusercontent.com/73262817/113715137-bc0fdf00-971b-11eb-9f25-21804e2a3b46.png)

* 投影查询  
`SELECT 列名1 别名1，列名2，列名3 FROME 表名；`  
返回结果为只包括所选取的三列的二位表结构，其中列名1被别名替代（不用改别名可以空着。查询结果中列的顺序和select中子句中的顺序相同
  
  * `SELECT Director '导演', Actors '演员' FROM movie_data;`   

    ![image](https://user-images.githubusercontent.com/73262817/113715537-2fb1ec00-971c-11eb-841a-c4bad88b566b.png)

* 排序  

`SELECT 列名1，列名2， 列名3 FROM 表名 ORDER BY 列名1，列名2 (DESC);`  
将列名123从高到低排序，先比较列名1，相同时比较列2值大小  
加上DESC表示倒序
  
  * `select * from movie_data ORDER BY Rating desc;`  
 
   ![image](https://user-images.githubusercontent.com/73262817/113720338-1cede600-9721-11eb-9a66-a3aec0cf71b9.png)

* 聚合查询  

`SELECT COUNT(*) FROM 表名；`  
查询表的全部行数  

`SELECT COUNT(列名1) 别名 FROM 表名 WHERE 列名1 >= n ;`  
带条件的聚合查询，同时命名新的列名为别名  
  
  * `select count(*) total from movie_data where Rating > 8;`  
 
 ![image](https://user-images.githubusercontent.com/73262817/113720555-5cb4cd80-9721-11eb-87e4-379a5405d707.png)

  * group by  
  
  `SELECT 列名1,列名2,列名3,.. FROM 表名 GROUP BY 列名1,列名2,...`  
   group by可以把聚合查询的结果进一步切分  
  
    * `SELECT `Year` , AVG(Rating) FROM movie_data GROUP BY `Year` ;`  
    * 查询每年投票数大于10000的全部电影的平均分数   
    
   ![image](https://user-images.githubusercontent.com/73262817/113723423-ebc2e500-9723-11eb-8f50-cb9abb5d183a.png) 
       
  * HAVING  
  
  由于group by 一般用于 select where from 之后，再需要分类就要用到having函数来判断  
  
  语法  
  ```
  SELECT <列名1>,<列名2><列名3>...  
    FROM <表名>  
    GROUP BY <列名1>,<列名2><列名3>...   
  HAVING <分组结果对应条件>；  
  ```
    * `SELECT `Year` , AVG(Rating) FROM movie_data  where Votes > 10000 GROUP BY `Year` HAVING AVG(Rating)>7;`
   ![image](https://user-images.githubusercontent.com/73262817/113723324-d2219d80-9723-11eb-9246-f307ef4b170c.png)

  
  * 其他查询法    
    `SUM` 计算列合计值，该列必须为数值类型  
    `AVG` 计算列平均值，同样要求数值类型   
    `MAX` 计算列最大值    
    `MIN` 计算列最小值    
    
* 模糊查询  
语法  
`SELECT * FROM <表名> WHERE <字段名> LIKE '通配符字符串';`  

mysql的通配符有两种  
  * %：表示0个或多个字符
  * _:表示一个字符
  
  `SELECT * FROM movie_data WHERE Director LIKE '%James%';`
  
  ![image](https://user-images.githubusercontent.com/73262817/113725730-2fb6e980-9726-11eb-86e4-a15a6292f9e1.png)

   
## SQL实用语句 ##
* 插入或替换  
`REPLACE INTO 表名 (列名1，列名2...) VALUES (值1，值2,...);`  
如果原记录存在，就会删除原记录替换为新记录

* 插入或更新  
`INSERT INTO 表名 (列名1，列名2...) VALUES (值1，值2,...) ON DULICATE KEY UPDATE 列名1 = 值1，列名2 = 值2...;`  
若记录不存在，则插入新记录，否则，字段1为值1的记录会被update之后的内容更新  

* 插入或忽略  
`INSERT IGNORE INTO students (字段1，字段2...) VALUES (值1，值2,...);`  
若记录存在，则忽略，什么也不会发生

* 快照  
`CREATE TABLE 新表名 SELECT * FROM 原表名 WHERE 字段1 = 1;`   
用于复制当前表的部分或全部数据到新表

* 强制使用锁定指引  
`SELECT * FROM 表名 FORCE INDEX （字段名）;`  
强制系统使用（列名）进行索引，前提是索引必须存在


## SQL高级处理 
### 窗口函数
也称为OLAP函数（Online analytical processing），可以对数据库进行实时处理。 
* 语法   
```
<窗口函数> OVER ([partition by <列清单>])
ORDER BY <排序列清单>;
```

* 用法  
  1.作为窗口函数用的聚合函数（SUM,AVG,COUNT,MAX,MIN）  
  2. RANK,DENSE_RANK,ROW_NUMBER 等专用窗口函数  
  
  * Rank 函数  
在有相同位次的记录，会跳过后面的位次    
例如：1位，1位，1位，4位  
  
  * DENSE_RANK 函数  
 在有相同位次的记录，不会跳过后面的位次  
 例如：1位，1位，1位，2位  
  
  * ROW_NUMBer  
 赋予唯一的连续位次   
 例如在3条记录并列时：1位，2位，3位，4位   
    
    * 一个rank函数的例子
      先以电影类别分类，再以rating高低排序
 ```
 select Title,Genre,Director,Actors,Year,`Runtime (Minutes)`,Rating, RANK() 
		OVER (partition by Genre order by Rating)as rating 
		from movie_data;` 
 ```
PARTITION BY 能够设定排序的对象范围，横向划分表格。  

ORDER BY 能够指定按照哪一列、何种顺序进行排序，纵向决定表的排序。  

![image](https://user-images.githubusercontent.com/73262817/113894848-fa300000-97fa-11eb-97c5-685d58893a6f.png)

   * 一个sum函数作为窗口函数使用的例子  

```
select `Rank`,Title,Votes,
	SUM(Votes) OVER (order by `Rank`) as total_votes
	from movie_data;
```

![image](https://user-images.githubusercontent.com/73262817/114830950-63b59d00-9dff-11eb-9bf8-2601ecb3fd4a.png)

### GROUPING函数
包括了三种用法：ROLLUP，CUBE，GROUPING SETS
* ROLLUP  

ROLLUP是GROUP BY子句的扩展。 ROLLUP选项允许包含表示小计的额外行，通常称为超级聚合行，以及总计行。 

```
select `Year` , Genre ,sum(Votes) as total_votes
	from movie_data
	group by  `Year`,Genre with rollup;
```

![image](https://user-images.githubusercontent.com/73262817/115114464-26e5d380-9fc2-11eb-96b1-3b294115dead.png)
![image](https://user-images.githubusercontent.com/73262817/115114478-39f8a380-9fc2-11eb-895e-bcf5499ddb1b.png)


查询每年每种电影的总投票，在最后一行会显示键值为NULL的超级聚合行，数值是该年全部总票数的加和，可以理解为小计。最后一行是总计。  

* CUBE  






## python与SQL 
### PyMySQL 
调出cmd面板 `WIN键 + R, 输入cmd 回车'`  
* 安装  
  `pip install PyMySQL`
  
  ![image](https://user-images.githubusercontent.com/73262817/111891856-0e20e700-8a31-11eb-8ce8-84e8b5c30d9c.png)

* 利用PyMySQL连接数据库
```import pymysql
   conn=pymysql.connect(host = '127.0.0.1',
   ,user = 'root' 
   ,passwd='password'
   ,port= 3306
   ,db='test'
   ,charset='utf8')
   cur = conn.cursor()  #生成游标对象  
   cur.close() # 关闭游标  
   conn.close() # 关闭连接  
   ```
 * 插入  
 `sql= "INSERT INTO 表名 VALUES (值1，值2，值3)`

 *  查询  
  `sql= "SELECT * FROM 表名 WHERE <判断语句>`

 * 删除  
`sql = "DELETE FROM 表名 WHERE <判断语句>`

 * 改  
`sql = UPDATE 表名 SET 字段1 = 值1`

 * 执行  
```   
   cur.execute(sql)   # 执行插入的sql语句    
   data = cur.fetchfall() # 通过fetchfall方法获取数据
```
   data是一个可迭代对象。

### mysql.connector
```
import mysql.connector
conn=mysql.connector.connect(host = '127.0.0.1' # 连接名称，默认127.0.0.1 
,user = 'root' 
,passwd='password' 
,port= 3306 
,db='test' 
,charset='utf8' 
)
```
与PyMySQL相比较而言，最大的区别在于连接数据库时的语法不同，其余部分大同小异。

# 参考资料 #
[1]廖雪峰.廖雪峰SQL教程[EB/OL].https://www.liaoxuefeng.com/wiki/1177760294764384,2021-3-20.  
[2][日]MICK.SQL基础教程[M].人民邮电出版社:北京,2013:1-102.
