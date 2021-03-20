# SQL

结构化查询语言(Structured Query language)，是一种用与数据库查询、存储、更新、管理的编程语言。
更多信息[请点击](https://baike.baidu.com/item/结构化查询语言/10450182?fromtitle=sql&fromid=86007&fr=aladdin)

## SQL下载 ##
要在Windows或Mac上安装MySQL，首先从MySQL官方网站下载最新的MySQL Community Server版本：
下载链接(https://dev.mysql.com/downloads/mysql/)
选择对应的操作系统版本，下载安装即可。在安装过程中，MySQL会自动创建一个root用户，并提示输入root口令。

## 运行MySQL ##

验证MySQL是否安装正确，可以通过在命令提示符（在主界面运行cmd）中输入`mysql -u root -p`，正确安装下会链接到MySQL服务器，同时提示`mysql>`

## SQL的关系模型 ##

### 主键 ###
用于区分每一条记录的差别，每条主键的名称不能相同。（例如每个人的身份证号码）
  
### 外键 ###  
可以链接两张表的数据，把1表的某列值对应2表相同列的对应值，相当于一个映射。可以实现一对多，多对多和一对一的关系。
  
### 索引 ###  
功能：从众多数据中快速获得想要查找的内容。
  
实现方法：
1.对某列进行操作
    `ALTER TABLE 表名`
    `ADD INDEX idx(列名1，列名2...）;`
        
2.唯一索引
    创建唯一索引用的列前提是列下的值不能重复
    `ALTER TABLE 表名`
    `ADD CONSTRAIN uni_name UNIQUE (name）;`

## 基本查询 ##
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
`SELECT 列名1，列名2， 列名3 FROM 表名 ORDER BY 列名1，列名2 (DESC)；`  
将列名123从高到低排序，先比较列名1，相同时比较列2值大小  
加上DESC表示倒序

* 分页查询
`LIMIT M OFFSET N;`  
用于数据量大，想分页显示的时候  
M表示每次显示最大的条数，N表示从第（N+1）条开始  
（例如 `LIMIT 3 OFFSET 0；`表示从第1条数据开始显示，最多显示3条）

* 聚合查询
`SELECT COUNT(*) FROM 表名；`  










   
   
      
  
