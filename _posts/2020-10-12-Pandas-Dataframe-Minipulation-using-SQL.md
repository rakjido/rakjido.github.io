---
layout: post
title: Pandas Dataframe에서 SQL 사용하기
author: "Rooftop Hero"
comments: false
tags: Python
---

<br>

> pandasql을 이용하여 Pandas Dataframe 데이터를 가공합니다.

<br>

일반 프로그래밍 언어가 아닌 SAS, R과 같은 통계패키지로 시작했습니다. SAS에는 data set이 있고, R에는 data.frame이 있습니다. Java에서는 데이터프레임에 대응되는 개념이 없고 대신 POJO(Plain Old Java Object)를 사용해서 당혹스러웠습니다. 다행히도(?) Python에는 Pandas에서 만든 Dataframe이 있습니다.

Pandas의 Dataframe은 강력하지만 조건이나 집계를 한다든지 하는 기능은 불편합니다. 다소 부족하지만 SAS는 proc sql, R에서는 [sqldf](https://cran.r-project.org/web/packages/sqldf/index.html){:target="_blank"}이라는 데이터프레임을 SQL로 조작하는 기능을 제공합니다.

비슷한 기능을 Pandas Dataframe을 사용해 구현해보았습니다. 본격적으로 SQL문을 parsing 하지 않는 한, 한계가 명확합니다.

```python
import pandas as pd
from typing import List

Vector = List[str]

def pdsql(SELECT: Vector, FROM: Vector, WHERE: Vector = None, ORDER_BY: Vector=None) -> pd.DataFrame:
    """
    Return dataframe with condition of SQL

    Parameters
    ----------
    SELECT : list of columns. ['*'] is all column
    FROM : source dataframe
    WHERE : list of where condition
    ORDER_BY : list of order by

    Returns
    -------
    queried result
"""

    if not isinstance(FROM, pd.DataFrame):
        print("'FROM' type should be Pandas Dataframe")
        return None
    
    FROM.columns = map(str.lower, FROM.columns)

    if(WHERE != None):
        if not isinstance(WHERE, list):
            print("'WHERE' type should be List")
            return None
        else:

            WHERE = [element.lower() for element in WHERE]

            _condition = []

            for i, _str in enumerate(WHERE):
                _keyword =['or','and','>=', '<=', '!=', '>', '<', '=']
                _pair = {'or': '|', 'and': '&'}

                for key in _keyword:
                    if (_str.find(key)>=0):
                        cond = None
                        if(key != 'or' and key != 'and'):
                            cond = _str.split(key)
                            if (key =='='):
                                key='=='
                            cond.insert(1, key)
                            _condition.append("( FROM['" + cond[0].strip() + "']" + cond[1] + cond[2] + ") ") 
                        elif(key == 'or' or key == 'and') :
                            _condition.append(_pair[key] + " ")        
                        
                        break

            FROM = FROM.loc[eval("".join(_condition)),:]

    if(ORDER_BY!= None):
        if not isinstance(ORDER_BY, list):
            print("'ORDER_BY' type should be List")
            return None
        else:
            _sort = {'asc': 'True', 'desc': 'False'}

            ORDER_BY = [element.lower() for element in ORDER_BY]
            if(ORDER_BY[len(ORDER_BY)-1] in _sort):
                FROM = FROM.sort_values(by=ORDER_BY[:len(ORDER_BY)-1], ascending=eval(_sort[ORDER_BY[len(ORDER_BY)-1]]))
            else:
                FROM = FROM.sort_values(by=ORDER_BY[:len(ORDER_BY)], ascending=True)

    if not isinstance(SELECT, list):
        print("'SELECT' type should be List")
        return None
    else:
        SELECT = [element.lower() for element in SELECT]
        if(SELECT[0]=='*'):
            FROM = FROM
        else:
            FROM = FROM[SELECT]

            
    return FROM


if __name__ == '__main__':
    emp = pd.read_csv('emp.csv')

    result = pdsql(SELECT=['*'], FROM=emp)
    print(result)

    result = pdsql(SELECT=['ENAME'], FROM=emp)
    print(result)

    result = pdsql(SELECT=['ENAME','SAL'], FROM=emp)
    print(result)

    result = pdsql(SELECT=['*'], FROM=emp, WHERE=["sal > 1000", "and", "depno=30"])
    print(result)


    result = pdsql(SELECT=['*'], FROM=emp, WHERE=["sal > 1000", "and", "depno=30", "or", "job='SALESMAN'"])
    print(result)


    result = pdsql(SELECT=['*'], FROM=emp, WHERE=["sal > 1000", "and", "depno=30", "or", "job='SALESMAN'"], ORDER_BY=['job','sal','desc'])
    print(result)

```

---

그러다 [pandasql](https://pypi.org/project/pandasql/){:target="_blank"}을 발견했습니다.
<br><br>
[sqlite의 SQL문법](https://www.sqlite.org/lang.html){:target="_blank"}을 지원합니다.
분석을 해보니 원리는 다음과 같습니다.
<br>

> 1. SQLAlchemy에서 sqlite의 메모리 DB를 한시적으로 생성한다
> 2. python envrionment에서 locals()이나 globals()로 해당 dataframe을 찾아 메모리 DB에 테이블로 올린다.
> 3. SQL문으로 데이터를 추출한다.

약간의 트릭을 사용했지만 발상의 전환으로 거의 완전한 SQL로 데이터프레임을 조작할 수 있도록 했습니다. 

* Package를 설치합니다.

```
pip install -U pandasql
```
<br>
* globals()로 환경을 일괄적으로 지정하는 방법은 다음과 같습니다.

```python
from pandasql import sqldf
dfsql = lambda q: sqldf(q, globals())

```
<br>
* 예제

```python

import pandas as pd
from pandasql import sqldf
dfsql = lambda q: sqldf(q, globals())


emp = pd.read_csv('emp.csv')
dept = pd.read_csv("dept.csv")


print(dfsql("select * from emp"))

print(dfsql("select * from emp where sal > 2000"))

print(dfsql("select * from emp where mgr = '7839' order by sal asc"))

print(dfsql("select ename, job, mgr, sal from emp where sal > 2000 order by sal desc, ename asc"))

print(dfsql("""
                select e.job, sum(sal) as sum_sal, avg(sal) as avg_sal, max(sal) as max_sal, min(sal) as min_sal
                from emp e inner join dept d 
                on e.depno = d.deptno
                where d.loc='DALLAS'
                group by e.job
                order by e.job desc
            """))


dfsql("""
                select e.job, sum(sal) as sum_sal, avg(sal) as avg_sal, max(sal) as max_sal, min(sal) as min_sal
                from emp e inner join dept d 
                on e.depno = d.deptno
                where d.loc='DALLAS'
                group by e.job
                order by e.job desc
            """).to_json('sal_job.json', orient='table')
```
<br>
예제와 데이터는 [여기](https://github.com/rakjido/PandasSQL.git){:target="_blank"}에 있습니다.

