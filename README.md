### Introduction

DNS 64
 
### Test

Start SimpleDNS 64:
```
$./main
Listening on port 9000.
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
sqlite3 database.db
CREATE TABLE ARecords(domain_name text,ip1 integer,ip2 integer,ip3 integer,ip4 integer)
CREATE TABLE AAAARecords(domain_name text,ip1 integer,ip2 integer,ip3 integer,ip4 integer,ip5 integer,ip6 integer,ip7 integer,ip8 integer,ip9 integer,ip10 integer,ip11 integer,ip12 integer,ip13 integer,ip14 integer,ip15 integer,ip16 integer)
gcc -o main main.c -lsqlite3
```
