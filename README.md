### Introduction

DNS 64 binary
 
### Use

Start SimpleDNS 64:
```
# 前台運行
$./main
# 後台運行
$nohup ./main 2>&1 >dns64.log &
Listening on port 5353.
```


```
$ dig @127.0.0.1 -p 5353 www.google.com AAAA
```

### Install
```sh
# Ubuntu
apt install sqlite3
apt install libsqlite3-dev
# Centos
yum install sqlite
yum install sqlite-devel
---
sqlite3 database.sqlite
CREATE TABLE ARecords(domain_name text,ip1 integer,ip2 integer,ip3 integer,ip4 integer);
CREATE TABLE AAAARecords(domain_name text,ip1 integer,ip2 integer,ip3 integer,ip4 integer,ip5 integer,ip6 integer,ip7 integer,ip8 integer,ip9 integer,ip10 integer,ip11 integer,ip12 integer,ip13 integer,ip14 integer,ip15 integer,ip16 integer);
.tables
gcc -o main main.c -lsqlite3
```

### ipv4->ipv6
```
237
284
378
418
1147
```

### Performance testing
```shell
# test.sh
# !/bin/bash
num=$1
for((i=num;i<=num+100;i++))
do
dig @127.0.0.1 -p 53533 www.google.com$i AAAA &
done

$ bash -x test.sh 1
```
本项目使用单线程处理udp请求，recvfrom一次处理一个请求，如果udp请求过多，可能会导致缓冲区满，导致后面的请求失效。
