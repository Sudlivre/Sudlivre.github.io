---
title: Linux-CentOS7 Install MySQL5.7
date: 2019-10-08 20:27:17
tags: 
- Linux
- Database
categories:
- Linux
---

## Install

```shell
wget 'https://dev.mysql.com/get/mysql57-community-release-el7-11.noarch.rpm'

rpm -Uvh mysql57-community-release-el7-11.noarch.rpm

yum repolist all | grep mysql

yum install -y mysql-community-server
```

## Configuration

### Start mysqld

```shell
systemctl start mysqld
```

### View temporary password

```shell
grep password /var/log/mysqld.log
```

### Login

```shell
mysql -u root -p
# enter password

set password=password("Mysql_123");

exit
```

### Open remote access

```shell
mysql -u root -p
# enter password
use mysql;

update user set host = '%' where user = 'root';

exit
```

### Restart mysqld

```shell
systemctl restart mysqld
```

### Open self-starting

```shell
systemctl enable mysqld
systemctl daemon-reload
```
