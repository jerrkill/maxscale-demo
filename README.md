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
mysql -h127.0.0.1 -P4006 -utest -p'test'

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
