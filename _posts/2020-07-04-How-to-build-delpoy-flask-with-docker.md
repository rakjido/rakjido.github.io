---
layout: post
title: Docker로 Flask를 build하고 배포하기
author: "Rooftop Hero"
comments: false
tags: DevOps
---

<br>

> 초간단 Flask 웹서버를 Docker로 빌드하고 실행합니다.

<br>

먼저 가상화 환경을 만듭니다. 
[VSCODE에서 Python VirtualEnv 실행하기](/2019/09/30/How-to-exectue-Python-VirtualEnv-in-VSCODE){:target="_blank"}를 참조하세요.

위의 폴더 안에 ```requirement.txt```를 만듭니다.

```
flask
flask_cors
uwsgi
```
<br>
* flask_cors : flask에서 교차 출처 리소스 공유(Cross-Origin Resourcing Sharing : CORS) 문제를 해결합니다.
* uwsgi : Flask의 내장서버인 werkzeug서버는 단일스레드이며 테스트용도 이외에는 적합하지 않으며 대신 uWSGI서버를 사용할 수 있습니다. 윈도10에서는 현재까지는 사용할 수 없습니다. 


```
pip install -r requirement.txt
```
<br>
__app.py__
```python
from flask import Flask, jsonify
from flask_cors import CORS

app = Flask(__name__)
CORS(app)

@app.route('/')
def home():
    return jsonify(
        text='Hello, world',
        id = 'exharo',
        no = 203
    )
```
<br>
다음과 같이 실행합니다.
<br>
```
export FLASK_APP=app.py
flask run
```
<br>
플라스크에서 애플리케이션의 default name은 ```app```이며, 이 경우 export FLASK_APP 지정을 생략할 수 있습니다.
<br>
```
FLASK_DEBUG=1 flask run
```
<br>
FLASK_DEBUG=1 옵션을 줄 경우 내용을 수정하고 저장할 경우 서버가 자동으로 reload 됩니다
<br>
[http://127.0.0.1:5000/](http://127.0.0.1:5000/){:target="_blank"}에 접속해서 정상적으로 작동하는지 확인합니다.
<br>
<br>
![result.jpeg](/images/posts/2020-07-04/result.jpeg){: width="100%" height="50%"}{: .center}
<br>
__uwsgi.ini__
```
[uwsgi]
http = : 5000
wsgi-file = app.py
single-interpreter = true
enable-threads = true
master = true
```
<br>
port를 5000으로 설정했습니다.
<br>

__app.py__
```python
from flask import Flask, jsonify
from flask_cors import CORS

app = Flask(__name__)
CORS(app)

@app.route('/')
def home():
    return jsonify(
        text='Hello, world',
        id = 'exharo',
        no = 203
    )

application = app
```
<br>
uWSGI에서의 default name은 application입니다. 그래서 마지막줄에 application = app 추가했습니다.
<br>
uWSGI server는 다음과 같이 실행합니다.
<br>
```
uwsgi --ini uwsgi.ini
```
<br>
Dockerfile을 다음과 같이 만듭니다.
<br>
```
FROM python:3.6.4

COPY . /app

WORKDIR /app 

RUN pip install -r requirement.txt

CMD ["uwsgi", "uwsgi.ini"]
```
<br>
정리하면 파일구성은 다음과 같습니다.

![tree.jpeg](/images/posts/2020-07-04/tree.jpeg){: width="100%" height="80%"}{: .center}
```
docker build -t test_flask_docker .
docker container run -p 8080:5000 -it test_flask_docker
```
<br>
[http://127.0.0.1:8080/](http://127.0.0.1:8080/){:target="_blank"}에 접속해서 정상적으로 작동하는 것을 확인합니다.


---

