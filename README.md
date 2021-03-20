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

主键  
    用于区分每一条记录的差别，每条主键的名称不能相同。（例如每个人的身份证号码）
  
外键  
    可以链接两张表的数据，把1表的某列值对应2表相同列的对应值，相当于一个映射。可以实现一对多，多对多和一对一的关系。
  
索引  
    功能：从众多数据中快速获得想要查找的内容。
  
    实现方法：
    1.对某列进行操作
      `ALTER TABLE 表名`
      `ADD INDEX idx(列名1，列名2...）;`
    
    2.唯一索引
      创建唯一索引用的列前提是列下的值不能重复
      `ALTER TABLE 表名`
      `ADD CONSTRAIN uni_name UNIQUE (name）;`

   
   
      
  
