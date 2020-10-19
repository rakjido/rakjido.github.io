---
layout: post
title: Python에서 xml을 이용한 mysql 설정하기 
author: "Rooftop Hero"
comments: false
tags: Python

---


> 데이터베이스 설정 정보를 xml로 분리해 보자


Python에서 데이터베이스 설정 정보를 config.xml 파일로 별도로 설정해 보았습니다.

```xml
<?xml version="1.0" encoding="utf-8" ?>
<Config>
    <DATABASE>
        <host>localhost</host>
        <port>3306</port>
        <userid>user</userid>
        <password>password</password>
        <db>db</db>
    </DATABASE>
</Config>
```

---

config.xml에서 데이터베이스 정보를 가져와서 접속하고 query를 실행할 수 있습니다.

```python
import xml.etree.ElementTree as elemTree

import pymysql
import pandas as pd 

def db_connect():
    tree = elemTree.parse('./config.xml')
    root = tree.getroot()
    dbinfo = root.find('./DATABASE')

    host = dbinfo.find('./host').text
    port = int(dbinfo.find('./port').text)
    userid = dbinfo.find('./userid').text
    password = dbinfo.find('./password').text
    db = dbinfo.find('./db').text

    try: 
        conn = pymysql.connect(host=host, port=port, user=userid, 
                            password=password, db=db, charset='utf8',
                            autocommit=True, cursorclass=pymysql.cursors.DictCursor )
    except BaseException:
        print("DB connection Error")

    cursor = conn.cursor(pymysql.cursors.DictCursor)

    return conn, cursor


def db_select(query):
    conn, cursor = db_connect()
    cursor.execute(query)
    result = pd.DataFrame(cursor.fetchall())
    conn.close()

    return result

def db_insert(query):
    conn, cursor = db_connect()
    cursor.execute(query)
    conn.close()


def db_update(query):
    conn, cursor = db_connect()
    cursor.execute(query)
    conn.close()

def db_delete(query):
    conn, cursor = db_connect()
    cursor.execute(query)
    conn.close()


```


다음과 같이 사용할 수 있습니다.

```python
    query = """
            DELETE FROM EQUITY_INFO
            WHERE EQUITY_CODE='AMZN'
            """
    db_delete(query)

    query = """
            INSERT INTO EQUITY_INFO (EQUITY_CODE, EQUITY_NAME, EXCHANGE_CODE, CURRENCY_CODE)
            VALUES('AMZN', 'Kingkong', 'SP500', 'USD')
            """

    db_insert(query)

    query = """
            UPDATE EQUITY_INFO 
            SET EQUITY_NAME = 'Amazon.com Inc'
            WHERE EQUITY_CODE='AMZN'
            """


    db_update(query)

    result = db_select("select * from equity_info")
    print(result.head())

```

