# centos安装PHP
- 安装vim：yum install vim 
- 安装：yum install wget
- 下载php文件：wget http://hk1.php.net/get/php-7.0.7.tar.gz/from/this/mirror
- 解压下载文件：tar -zxvf mirror
- php和Nginx工作需要安装FPM：yum install gcc gcc++ libxml2-devel
- ./configure --prefix=/usr/local/php7.0.7 --enable-fpm
- 编译php：make
- 安装php：make install
- 新建php文件：vim test.php
- 打印php信息：\<?php phpinfo()
- 执行php文件：/usr/local/php7.0.7/bin/php test.php   

# centos安装mysql
安装ossec时需要使用到mysql-server，直接安装报错：
[root@ossec-server ]()\# yum install mysql-server
原因是yum安装库里没有直接可以用的安装包，这时候就需要用到MariaDB了，MariaDB是
MySQL社区开发的分支，也是一个增强型的替代品。
1. 安装mariadb
[root@ossec-server Desktop]()\# yum -y install mariadb-server mariadb mariadb-devel
[root@ossec-server Desktop]()\# systemctl start mariadb
[root@ossec-server Desktop]()\# systemctl enable mariadb
[root@ossec-server Desktop]()\# mysql_secure_installation
[root@ossec-server Desktop]()\# firewall-cmd --permanent --add-service mysql
[root@ossec-server Desktop]()\# systemctl restart firewalld.service
[root@ossec-server Desktop]()\# iptables -L -n|grep 3306  

2.  登录数据库查看是否设置成功
[root@ossec-server Desktop]()\# mysql -uroot -p
MariaDB [(none)]()\> show databases;

3. mariadb相关命令：
systemctl start mariadb  #启动MariaDB
systemctl stop mariadb  #停止MariaDB
systemctl restart mariadb  #重启MariaDB
systemctl enable mariadb  #设置开机启动

