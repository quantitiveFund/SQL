# SQL

![image](https://user-images.githubusercontent.com/73262817/111874398-0da43400-89d0-11eb-8382-8d95b8453b8c.png)

结构化查询语言(Structured Query language)，是一种用与数据库查询、存储、更新、管理的编程语言。

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
   * `insert into hero_1(hero_id,hero_name,profession) VALUES`   
    `(1,'李白','刺客'),`       
    `(2,'鲁班七号','射手'),`   
    `(3,'吕布','战士'),`   
    `(4,'安琪拉','法师'),`   
    `(5,'马超','战士'),`
    `(6,'马可波罗','射手'),`  
    `(7,'露娜','刺客'),`  
    `(8,'诸葛亮','法师 ),`  
    `(9,'司马懿','法师'),`  
    `(10,'澜','刺客');`    

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


## 数据查询语言 ##

以下图的hero_1表格为例

![image](https://user-images.githubusercontent.com/73262817/111873673-683b9100-89cc-11eb-94d4-bd11b3a5c602.png)

* 全部查询  
`SELECT * FROM 表名;`
  * `SELECT * FROM hero_1;`  

    ![image](https://user-images.githubusercontent.com/73262817/111873677-6bcf1800-89cc-11eb-9434-104d0f8dc2ee.png)


* 条件查询  
`SELECT * FROM 表名 WHERE 列名1 >= n AND 列名2 <= m;`    
用来查找列1值大于等于n且列2值小于等于m的记录  
逻辑连接词还有`NOT`,`OR`。如果不加括号，优先级为not>and>or  
  * `SELECT * FROM hero_1 WHERe profession = '法师';`  
 
    ![image](https://user-images.githubusercontent.com/73262817/111873723-b6e92b00-89cc-11eb-8d57-b233c4e868d5.png)


* 投影查询  
`SELECT 列名1 别名1，列名2，列名3 FROME 表名；`
返回结果为只包括所选取的三列的二位表结构，其中列名1被别名替代（不用改别名可以空着） 
  * `SELECT hero_id id_hero, hero_name name_hero FROM hero_1;;`   

    ![image](https://user-images.githubusercontent.com/73262817/111873785-10e9f080-89cd-11eb-84ae-a2f0823ed036.png)


* 排序  
`SELECT 列名1，列名2， 列名3 FROM 表名 ORDER BY 列名1，列名2 (DESC);`  
将列名123从高到低排序，先比较列名1，相同时比较列2值大小  
加上DESC表示倒序
  * `select * from hero_1 order by ban_rate desc;`  
 
    ![image](https://user-images.githubusercontent.com/73262817/111873841-48f13380-89cd-11eb-92d6-f468d9133e42.png)


* 聚合查询  
`SELECT COUNT(*) FROM 表名；`  
查询表的全部行数  
`SELECT COUNT(*) 别名 FROM 表名 WHERE 列名1 >= n ;`  
带条件的聚合查询，同时命名新的列名为别名  
  * `select count(*) total_heronumber from hero_1 where ban_rate > 0.5;`  
    ![image](https://user-images.githubusercontent.com/73262817/111873901-a1c0cc00-89cd-11eb-9674-fcb324925941.png)

  * 其他查询法   
    `SUM` 计算列合计值，该列必须为数值类型  
    `AVG` 计算列平均值，同样要求数值类型   
    `MAX` 计算列最大值    
    `MIN` 计算列最小值    

   
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

## python与SQL ##
### PyMySQL ###
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
   cur = conn.cursor() # 生成游标对象
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
```try:   
     cur.execute(sql)   # 执行插入的sql语句    
     conn.commit()    # 提交到数据库执行
   except:    
     coon.rollback()# 如果发生错误则回滚 
     conn.close()    # 关闭数据库连接
```
# 参考资料 #
[1]廖雪峰.廖雪峰SQL教程[EB/OL].https://www.liaoxuefeng.com/wiki/1177760294764384,2021-3-20.
