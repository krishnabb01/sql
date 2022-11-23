# sql
first program
Enter password: ****
Welcome to the MySQL monitor.  Commands end with ; or \g.
Your MySQL connection id is 19
Server version: 8.0.31 MySQL Community Server - GPL

Copyright (c) 2000, 2022, Oracle and/or its affiliates.

Oracle is a registered trademark of Oracle Corporation and/or its
affiliates. Other names may be trademarks of their respective
owners.

Type 'help;' or '\h' for help. Type '\c' to clear the current input statement.

mysql> create database jspm_barshi;
Query OK, 1 row affected (0.01 sec)

mysql> show databases;
+--------------------+
| Database           |
+--------------------+
| bitbarshi          |
| india_population   |
| information_schema |
| jspm_barshi        |
| mysql              |
| performance_schema |
| sys                |
| tblstudent         |
+--------------------+
8 rows in set (0.00 sec)

mysql> use database jspm
ERROR 1049 (42000): Unknown database 'database'
mysql> use database jspm_barshi;
ERROR 1049 (42000): Unknown database 'database'
mysql> use jspm_barshi;
Database changed
mysql> create table tblempolyee (id int primary key,name varchar(50) not null,age int,mobile_no decimal unique,sallary int,country default ("india"
    -> );
ERROR 1064 (42000): You have an error in your SQL syntax; check the manual that corresponds to your MySQL server version for the right syntax to use near 'default ("india"
)' at line 1
mysql> create table tblempolyee (id int primary key,name varchar(50) not null,age int,mobile_no decimal unique,sallary int,country default ("india");
ERROR 1064 (42000): You have an error in your SQL syntax; check the manual that corresponds to your MySQL server version for the right syntax to use near 'default ("india")' at line 1
mysql> create table tblempolyee (id int primary key,name varchar(50) not null,age int,mobile_no decimal unique,sallary int,country vzrchar(50) default "indi
a");
ERROR 1064 (42000): You have an error in your SQL syntax; check the manual that corresponds to your MySQL server version for the right syntax to use near 'vzrchar(50) default "india")' at line 1
mysql> create table tblempolyee (id int primary key,name varchar(50) not null,age int,mobile_no decimal unique,sallary int,country vzrchar(50) default 'india');
ERROR 1064 (42000): You have an error in your SQL syntax; check the manual that corresponds to your MySQL server version for the right syntax to use near 'vzrchar(50) default 'india')' at line 1
mysql> create table tblempolyee (id int primary key,name varchar(50) not null,age int,mobile_no decimal unique,sallary int,country varchar(50) default 'india');
Query OK, 0 rows affected (0.03 sec)

mysql> desc tblemplyee;
ERROR 1146 (42S02): Table 'jspm_barshi.tblemplyee' doesn't exist
mysql> desc tblempolyee;
+-----------+---------------+------+-----+---------+-------+
| Field     | Type          | Null | Key | Default | Extra |
+-----------+---------------+------+-----+---------+-------+
| id        | int           | NO   | PRI | NULL    |       |
| name      | varchar(50)   | NO   |     | NULL    |       |
| age       | int           | YES  |     | NULL    |       |
| mobile_no | decimal(10,0) | YES  | UNI | NULL    |       |
| sallary   | int           | YES  |     | NULL    |       |
| country   | varchar(50)   | YES  |     | india   |       |
+-----------+---------------+------+-----+---------+-------+
6 rows in set (0.00 sec)

mysql> insert into tblempolyee (id as empolyee_id,name empolyee_name,age,mobile_no,sallary as $sallary,country) values (101,krishna,20,9876543210,100000);
ERROR 1064 (42000): You have an error in your SQL syntax; check the manual that corresponds to your MySQL server version for the right syntax to use near 'as empolyee_id,name empolyee_name,age,mobile_no,sallary as $sallary,country) val' at line 1
mysql> select (id as empolyee_id,name empolyee_name,age,mobile_no,sallary as $sallary,country)
    -> select (id as empolyee_id,name empolyee_name,age,mobile_no,sallary as $sallary,country);
ERROR 1064 (42000): You have an error in your SQL syntax; check the manual that corresponds to your MySQL server version for the right syntax to use near 'as empolyee_id,name empolyee_name,age,mobile_no,sallary as $sallary,country)
sel' at line 1
mysql> insert into tblempolyee (id,name,age,mobile_no,sallary,country) values (101,krishna,20,9876543210,100000);
ERROR 1136 (21S01): Column count doesn't match value count at row 1
mysql> insert into tblempolyee (id,name,age,mobile_no,sallary,country) values (101,krishna,20,9876543210,100000,);
ERROR 1064 (42000): You have an error in your SQL syntax; check the manual that corresponds to your MySQL server version for the right syntax to use near ')' at line 1
mysql> insert into tblempolyee (id,name,age,mobile_no,sallary,country) values (101,krishna,20,9876543210,100000,india);
ERROR 1054 (42S22): Unknown column 'krishna' in 'field list'
mysql> insert into tblempolyee (id,name,age,mobile_no,sallary,country) values (101,"krishna",20,9876543210,100000,india);
ERROR 1054 (42S22): Unknown column 'india' in 'field list'
mysql> insert into tblempolyee (id,name,age,mobile_no,sallary,country) values (101,"krishna",20,9876543210,100000,"india");
Query OK, 1 row affected (0.01 sec)

mysql> select * from tblempolyee;
+-----+---------+------+------------+---------+---------+
| id  | name    | age  | mobile_no  | sallary | country |
+-----+---------+------+------------+---------+---------+
| 101 | krishna |   20 | 9876543210 |  100000 | india   |
+-----+---------+------+------------+---------+---------+
1 row in set (0.00 sec)

mysql> insert into tblempolyee values (102,"krishna",20,9876543210,100000);
ERROR 1136 (21S01): Column count doesn't match value count at row 1
mysql> insert into tblempolyee (id,name,age,mobile_no,sallary,country) values (102,"krishna",20,9876543211,100000,);
ERROR 1064 (42000): You have an error in your SQL syntax; check the manual that corresponds to your MySQL server version for the right syntax to use near ')' at line 1
mysql> insert into tblempolyee (id,name,age,mobile_no,sallary) values (102,"krishna",20,9876543211,100000);
Query OK, 1 row affected (0.01 sec)

mysql> select *from tblempolyee;
+-----+---------+------+------------+---------+---------+
| id  | name    | age  | mobile_no  | sallary | country |
+-----+---------+------+------------+---------+---------+
| 101 | krishna |   20 | 9876543210 |  100000 | india   |
| 102 | krishna |   20 | 9876543211 |  100000 | india   |
+-----+---------+------+------------+---------+---------+
2 rows in set (0.00 sec)

mysql> insert into tblempolyee values(103,'lucy',21,9876543212,2000000,'usa'),(104,"barbi",20,9876543219,30000000,"usa"),(105,'king',27,9876543217,999999999
);
ERROR 1136 (21S01): Column count doesn't match value count at row 3
mysql> insert into tblempolyee values(103,'lucy',21,9876543212,2000000,'usa'),(104,"barbi",20,9876543219,30000000,"usa"),(105,'king',27,9876543217,999999999,india);
ERROR 1054 (42S22): Unknown column 'india' in 'field list'
mysql> insert into tblempolyee values(103,'lucy',21,9876543212,2000000,'usa'),(104,"barbi",20,9876543219,30000000,"usa"),(105,'king',27,9876543217,999999999,'india');
Query OK, 3 rows affected (0.01 sec)
Records: 3  Duplicates: 0  Warnings: 0

mysql> select *from tblempolyee;
+-----+---------+------+------------+-----------+---------+
| id  | name    | age  | mobile_no  | sallary   | country |
+-----+---------+------+------------+-----------+---------+
| 101 | krishna |   20 | 9876543210 |    100000 | india   |
| 102 | krishna |   20 | 9876543211 |    100000 | india   |
| 103 | lucy    |   21 | 9876543212 |   2000000 | usa     |
| 104 | barbi   |   20 | 9876543219 |  30000000 | usa     |
| 105 | king    |   27 | 9876543217 | 999999999 | india   |
+-----+---------+------+------------+-----------+---------+
5 rows in set (0.00 sec)

mysql> select id as empolyee
    ->
    -> l
    -> ';
    '> ,l,;ljuygfhjnbnk;
    '> select id as empolyee;
    '> select *from tblempolyee;
    '> select * from tblempolyoee;
    '> ^C
mysql> select id as empolyee_id,name empolyee_name,age,mobile_no,sallary as By_$M_sallary,country from tblempolyee;
+-------------+---------------+------+------------+---------------+---------+
| empolyee_id | empolyee_name | age  | mobile_no  | By_$M_sallary | country |
+-------------+---------------+------+------------+---------------+---------+
|         101 | krishna       |   20 | 9876543210 |        100000 | india   |
|         102 | krishna       |   20 | 9876543211 |        100000 | india   |
|         103 | lucy          |   21 | 9876543212 |       2000000 | usa     |
|         104 | barbi         |   20 | 9876543219 |      30000000 | usa     |
|         105 | king          |   27 | 9876543217 |     999999999 | india   |
+-------------+---------------+------+------------+---------------+---------+
5 rows in set (0.00 sec)

mysql> delete from tblempolyee where id=102;
Query OK, 1 row affected (0.01 sec)

mysql> select * from tblempolyee;
+-----+---------+------+------------+-----------+---------+
| id  | name    | age  | mobile_no  | sallary   | country |
+-----+---------+------+------------+-----------+---------+
| 101 | krishna |   20 | 9876543210 |    100000 | india   |
| 103 | lucy    |   21 | 9876543212 |   2000000 | usa     |
| 104 | barbi   |   20 | 9876543219 |  30000000 | usa     |
| 105 | king    |   27 | 9876543217 | 999999999 | india   |
+-----+---------+------+------------+-----------+---------+
4 rows in set (0.00 sec)

mysql> update tblempolyee set country='usa' where id=104;
Query OK, 0 rows affected (0.00 sec)
Rows matched: 1  Changed: 0  Warnings: 0

mysql> select * from tblempolyee;
+-----+---------+------+------------+-----------+---------+
| id  | name    | age  | mobile_no  | sallary   | country |
+-----+---------+------+------------+-----------+---------+
| 101 | krishna |   20 | 9876543210 |    100000 | india   |
| 103 | lucy    |   21 | 9876543212 |   2000000 | usa     |
| 104 | barbi   |   20 | 9876543219 |  30000000 | usa     |
| 105 | king    |   27 | 9876543217 | 999999999 | india   |
+-----+---------+------+------------+-----------+---------+
4 rows in set (0.00 sec)

mysql> update tblempolyee set country='india' where id=104;
Query OK, 1 row affected (0.00 sec)
Rows matched: 1  Changed: 1  Warnings: 0

mysql> select * from tblempolyee;
+-----+---------+------+------------+-----------+---------+
| id  | name    | age  | mobile_no  | sallary   | country |
+-----+---------+------+------------+-----------+---------+
| 101 | krishna |   20 | 9876543210 |    100000 | india   |
| 103 | lucy    |   21 | 9876543212 |   2000000 | usa     |
| 104 | barbi   |   20 | 9876543219 |  30000000 | india   |
| 105 | king    |   27 | 9876543217 | 999999999 | india   |
+-----+---------+------+------------+-----------+---------+
4 rows in set (0.00 sec)
