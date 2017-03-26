DBMS分类
1. 基于共享文件系统的DBMS
    1. 例如 Microsoft Access FileMaker，用于桌面用途，通常不用于高端火关键应用
2. 基于客户机-服务器的DMBS
    1. MySQL

## 链接MySQL
登陆：mysql -uusername -ppassword -hlocalhost -Pport

几个常用命令：
show databases;// 显示数据库
use database;

show tables like “%%”
describe table;
show create table;

show status;//显示所有系统信息
show status like “T%”;

show grants;//显示所用户的授权信息
show warnings；
show errors;// 显示报错信息

