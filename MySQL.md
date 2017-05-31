#MySQL

Step 1: Install MySQL
```
brew install mysql
==> Downloading https://homebrew.bintray.com/bottles/mysql-5.7.18_1.el_capitan.bottle.tar.gz
We've installed your MySQL database without a root password. To secure it run:
    mysql_secure_installation

MySQL is configured to only allow connections from localhost by default

To connect run:
    mysql -uroot

To have launchd start mysql now and restart at login:
  brew services start mysql
Or, if you don't want/need a background service you can just run:
  mysql.server start
```
Use the mysqladmin Utility to Obtain Server Status
```
$ mysqladmin --version                                                                                                                                                                                                       ✓  1548  09:45:08 
mysqladmin  Ver 8.42 Distrib 5.7.18, for osx10.11 on x86_64
```

start mysql server 
```
mysql.server start
=> Starting MySQL
.. SUCCESS! 
```
connect to your MySQL server through the MySQL client and by using the mysql command. 
```
$ sudo mysql 
=> Password:
Welcome to the MySQL monitor.  Commands end with ; or \g.
Your MySQL connection id is 4
Server version: 5.7.18 Homebrew

Copyright (c) 2000, 2017, Oracle and/or its affiliates. All rights reserved.

Oracle is a registered trademark of Oracle Corporation and/or its
affiliates. Other names may be trademarks of their respective
owners.

Type 'help;' or '\h' for help. Type '\c' to clear the current input statement.
```
Now, you are connected to the MySQL server and you can execute all the SQL commands at the mysql> prompt as follows 
```
mysql> show databases;
+--------------------+
| Database           |
+--------------------+
| information_schema |
| mysql              |
| performance_schema |
| sys                |
+--------------------+
4 rows in set (0.09 sec)
mysql> 
```
MySQL ships with a blank password for the root MySQL user. As soon as you have successfully installed the database and the client,
```
$ mysqladmin -u root password "xxxx" 
```
Now to make a connection to your MySQL server, you would have to use the following command −
```
$ sudo mysql -u root -p 
Enter password: xxxxx
```
If you want to run the MySQL server at boot time
```
=> To have launchd start mysql now and restart at login:
$ brew services start mysql
```

Step 2:
First check if your MySQL server is running or not.
```
$ ps -ef | grep mysqld 
=> 
501  3352     1   0  9:48AM ttys002    0:00.03 /bin/sh /usr/local/Cellar/mysql/5.7.18_1/bin/mysqld_safe --datadir=/usr/local/var/mysql --pid-file=/usr/local/var/mysql/localhost.pid
501  3451  3352   0  9:48AM ttys002    0:00.76 /usr/local/Cellar/mysql/5.7.18_1/bin/mysqld --basedir=/usr/local/Cellar/mysql/5.7.18_1 --datadir=/usr/local/var/mysql --plugin-dir=/usr/local/Cellar/mysql/5.7.18_1/lib/plugin --log-error=/usr/local/var/mysql/localhost.err --pid-file=/usr/local/var/mysql/localhost.pid
501  5121   390   0 10:09AM ttys002    0:00.00 grep --color=auto --exclude-dir=.bzr --exclude-dir=CVS --exclude-dir=.git --exclude-dir=.hg --exclu
```
if server is not running, then  you can start it by using the following command:
```
mysql.server start
```
If you want to shut down an already running MySQL server, then you can do it using the following command.
```
mysqladmin -u root -p shutdown 
```
**Setting Up a MySQL User Account**
For adding a new user to MySQL, you just need to add a new entry to the user table in the database mysql.
The following program is an example of adding a new user guest with SELECT, INSERT and UPDATE privileges with the password guest123;
You can create MySQL accounts two ways:
  1. By using account-management statements intended for crearting accounts and establishing their privilegers, such as **GREATE USER** and **GRANT**. These statement cause the server to make appropriate modifications to the underlying grant tables.
  2. By manipulating the MySQL grant tables directory with statements such as **INSERT,UPDATE,DELETE**
  
```
$ mysql.server start
$ mysql -u root -p
mysql> create user 'guest'@'localhost' identified by 'guest123';
Query OK, 0 rows affected (0.16 sec)

mysql> grant all privileges on *.* to 'guest'@'localhost' with grant option;
Query OK, 0 rows affected (0.04 sec) 
==> the user name of guest and a password of guest123. both are superuser accounts with full privileges to do anything.The 'guest'@'localhost' account can be used only when connecting from the loadlhost.
==> the 'guest'@'%' account uses the '%' wildcard for the host part.so it can be used to connect from any host. 
```
To see the privileges for an account, use **SHOW GRANTS**
```
mysql> show grants for 'guest'@'localhost';
+----------------------------------------------------------------------+
| Grants for guest@localhost                                           |
+----------------------------------------------------------------------+
| GRANT ALL PRIVILEGES ON *.* TO 'guest'@'localhost' WITH GRANT OPTION |
+----------------------------------------------------------------------+
1 row in set (0.00 sec)

mysql> 
```
To see nonprivilege properties for an account, use **SHOW CREATE USER**
```
mysql> show create user 'guest'@'localhost';
+----------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
| CREATE USER for guest@localhost                                                                                                                                            |
+----------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
| CREATE USER 'guest'@'localhost' IDENTIFIED WITH 'mysql_native_password' AS '*F1573429579994EEA4459170FDAC55DF96C4BBE6' REQUIRE NONE PASSWORD EXPIRE DEFAULT ACCOUNT UNLOCK |
+----------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
1 row in set (0.00 sec)
```
The next example create a account and grant access to specific databases. the account can access the mysql database, but only from the local host.
```
mysql> create user 'custom'@'localhost' identified by 'custom123';
Query OK, 0 rows affected (0.21 sec)
mysql> grant select, insert, update, delete, create,drop on mysql.* to 'custom'@'localhost';
Query OK, 0 rows affected (0.06 sec)
```
NOTE - MySQL does not terminate a command until you give a semicolon(;) at the end of the SQL command.

**The my.cnf File Configuration**
you may want to ensure that mysql is actually loading in whichever my.cnf file you're editing 
On OS X EI Caption, it was set up in "/usr/local/etc/my.cnf" 
```
$ mysql --verbose --help | grep my.cnf
=> order of preference, my.cnf, $MYSQL_TCP_PORT,
/etc/my.cnf /etc/mysql/my.cnf /usr/local/etc/my.cnf ~/.my.cnf 
$ sudo vim /usr/local/etc/my.cnf 
=> /usr/local/etc/my.cnf
# Default Homebrew MySQL server config
[mysqld]
# Only allow connections from localhost
bind-address = 127.0.0.1
```

**Administrative MySQL Command** <br>
**USE Databasename** -- This will be used to select a database in the MySQL workarea<br>
**SHOW DATABASES** -- Lists out the databases that are accessible by the MySQL DBMS.<br>
**SHOW TABLES** -- Shows the tables in the database once a database has been selected with the use command.<br>
**SHOW COLUMNS FROM tablename** -- Shows the attributes, types of attributes, key information, whether NULL is permitted, defaults,and other information for a table.<br>
**SHOW INDEX FROM tablename** -- Presents the details of all indexs on the table, inlcuding the RPIMARY KEY.<br>
**SHOW TABLE STATUS LIKE tablename\G** -- Reports details of the MySQL DBMS performance and statistics.<br>







