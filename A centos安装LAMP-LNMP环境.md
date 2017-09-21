# centos安装PHP
安装vim：yum install vim 
安装：yum install wget
下载php文件：wget http://hk1.php.net/get/php-7.0.7.tar.gz/from/this/mirror
解压下载文件：tar -zxvf mirror
php和Nginx工作需要安装FPM：yum install gcc gcc++ libxml2-devel
./configure --prefix=/usr/local/php7.0.7 --enable-fpm
编译php：make
安装php：make install
新建php文件：vim test.php
打印php信息：\<?php phpinfo()
执行php文件：/usr/local/php7.0.7/bin/php test.php   

# centos安装mysql
- 方式一（暂未成功）
查看自己是否安装了MySQL数据库：rpm -qa | grep mysql
卸载过程：rpm -e mysql 和rpm -e --nodeps mysql
查看yum上提供的数据库可下载版本：yum list | grep mysql
选择安装 mysql.i686，mysql-devel.i686，mysql-server.i686就行：yum -y install mysql mysql-server mysql-devel
启动方式：service mysqld start

- 方式二（暂未成功）
下载mysql：wget http://dev.mysql.com/get/Downloads/MySQL-5.7/mysql-5.7.13.tar.gz
解压mysql：tar -zxvf mysql-5.7.13.tar.gz
安装mysql扩展：yum install cmake gcc-c++ ncurses-devel perl-Data-Dumper boost boost-doc boost-devel
进入mysql：cd mysql-5.7.13
cmake \\
-DCMAKE_INSTALL_PREFIX=/usr/local/mysql \\
-DMYSQL_DATADIR=/mydata/mysql/data \\
-DSYSCONFDIR=/etc \\
-DMYSQL_USER=mysql \\
-DWITH_MYISAM_STORAGE_ENGINE=1  \\
-DWITH_INNOBASE_STORAGE_ENGINE=1 \\
-DWITH_ARCHIVE_STORAGE_ENGINE=1 \\
-DWITH_MEMORY_STORAGE_ENGINE=1 \\
-DWITH_READLINE=1 \\
-DMYSQL_UNIX_ADDR=/var/run/mysql/mysql.sock \\
-DMYSQL_TCP_PORT=3306 \\
-DENABLED_LOCAL_INFILE=1 \\
-DENABLE_DOWNLOADS=1 \\
-DWITH_PARTITION_STORAGE_ENGINE=1 \\
-DEXTRA_CHARSETS=all \\
-DDEFAULT_CHARSET=utf8 \\
-DDEFAULT_COLLATION=utf8_general_ci \\
-DWITH_DEBUG=0 \\
-DMYSQL_MAINTAINER_MODE=0 \\
-DWITH_SSL:STRING=bundled \\
-DWITH_ZLIB:STRING=bundled_
编译：make
安装：make install
