---
layout: post
title: Ubuntu 18.04에 mysql 설치  
author: "Rooftop Hero"
comments: false
tags: DevOps Mysql Ubuntu

---

<br>

> Ubuntu 18.04 LTS에 mysql을 설치한다.

<br>

* Ubuntu 18.04에서 설치되는 mysql version은 5.7.4가 default이다. 

<br>
```
sudo apt install mysql-server
service mysql start
```
<br>

위의 버전에서는 root는 처음에는 다음과 같이 접속한다.

<br>

```
sudo mysql
```
<br>

다음과 같이 비밀번호를 변경한다.

```sql
alter user 'root'@'localhost' identified with mysql_native_password by '1234';
```


### UTF-8 설정

my.cnf를 찾기 위해서 다음의 명령어를 사용한다.

```
mysqld --verbose --help | grep -A 1 'Default options'
```
찾은 my.cnf 중 /etc/mysql/my.cnf 에 UTF-8를 다음과 같이 설정한다.

```
sudo vi /etc/mysql/my.cnf
```
```
[client]
default-character-set = utf8
 
# mysqld 부분밑에 추가
[mysqld]

port = 3306

init_connect = SET collation_connection = utf8_general_ci
init_connect = SET NAMES utf8
character-set-server = utf8
collation-server = utf8_general_ci
 
max_allowed_packet = 50M

# 1: 테이블 명 대소문자 구분하지 않음
# 2: 테이블 명 대소문자 구분함
lower_case_table_names=1
 
# 외부접속 허용
#bind-address = 0.0.0.0
 
# 파일 업로드 위치 지정 
# secure-file-priv="/var/lib/mysql-files/"
secure-file-priv=""


# mysqldump 부분밑에 추가
[mysqldump]
default-character-set = utf8
 
# mysql 부분밑에 추가
[mysql]
default-character-set = utf8
```
<br>

### 포트 설정 

<br>

ubuntu에 mysql을 설치할 경우 포트가 기본으로 3306으로 설정되어 있다. 클라우드에 데이터베이스를 설치하거나 온프레미스에 설치된 데이터베이스의 외부접속을 허용할 경우 포트번호를 3306이나 3307로 할 경우 해커들의 놀이터가 된다. 포트는 [mysqld]아래에 다음과 같이 설정한다. 외부접속을 허용하려면 bind-address를 0.0.0.0으로 설정한다.

<br>

```
[mysqld]

port = 42786
bind-address = 0.0.0.0
```

<br>

mysql을 재시작한다.

```
service mysql restart
```

root로 접속하여 

```
mysql -u root -p
```
<br>
staus를 보면 utf-8로 설정되었음을 확인할 수 있다.
```
mysql> status
```

```
mysql> status
--------------
mysql  Ver 14.14 Distrib 5.7.40, for Linux (x86_64) using  EditLine wrapper

Connection id:          2
Current database:       
Current user:           root@localhost
SSL:                    Not in use
Current pager:          stdout
Using outfile:          ''
Using delimiter:        ;
Server version:         5.7.40-0ubuntu0.18.04.1 (Ubuntu)
Protocol version:       10
Connection:             Localhost via UNIX socket
Server characterset:    utf8
Db     characterset:    utf8
Client characterset:    utf8
Conn.  characterset:    utf8
UNIX socket:            /var/run/mysqld/mysqld.sock
Uptime:                 1 min 23 sec
```

