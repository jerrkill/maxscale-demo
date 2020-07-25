## maxscale-demo

## usage

```
docker-compose up -d
```

## doc

[maxscal文档](https://mariadb.com/kb/en/maxscale-24-reference/)

[maxscal-github](https://github.com/mariadb-corporation/MaxScale)

[maxscal-gitee](https://gitee.com/mirrors/maxscale)

## test

```
# 查看端口
netstat -ntelp
# 连上maxscal
mysql -h172.17.0.1 -P4006 -utest -p'test'

```

```
# sql测试
select @@hostname;
start transaction;
select @@hostname;
commit;
select @@hostname;
```

执行结果如下

```
MariaDB [(none)]> select @@hostname;
+--------------+
| @@hostname   |
+--------------+
| 14b68c87afdf |
+--------------+
1 row in set (0.00 sec)

MariaDB [(none)]> start transaction;
Query OK, 0 rows affected (0.01 sec)

MariaDB [(none)]> select @@hostname;
+--------------+
| @@hostname   |
+--------------+
| 0022ab9d5fa2 |
+--------------+
1 row in set (0.01 sec)

MariaDB [(none)]> commit;
Query OK, 0 rows affected (0.01 sec)

MariaDB [(none)]> select @@hostname;
+--------------+
| @@hostname   |
+--------------+
| 14b68c87afdf |
+--------------+
1 row in set (0.00 sec)
```

`docker ps`

```
CONTAINER ID        IMAGE                                            COMMAND                  CREATED             STATUS              PORTS                                                      NAMES
14b68c87afdf        mariadb:10.5.3                                   "docker-entrypoint.s…"   2 hours ago         Up 2 hours          3306/tcp                                                   mariadb-slave1
6bb16cdd46e7        maxscale:latest                                  "/start"                 2 hours ago         Up 2 hours          172.17.0.1:4006->4006/tcp, 172.17.0.1:4008->4008/tcp, 6603/tcp   maxscale
559164dfe84c        mariadb:10.5.3                                   "docker-entrypoint.s…"   2 hours ago         Up 2 hours          3306/tcp                                                   mariadb-slave2
0022ab9d5fa2        mariadb:10.5.3                                   "docker-entrypoint.s…"   2 hours ago         Up 2 hours          3306/tcp                                                   mariadb-master
```
