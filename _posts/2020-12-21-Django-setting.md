---
layout: post
title: Django install
author: "Rooftop Hero"
comments: false
tags: Django
---

### Python 가상환경 (VirtualEnv) 설정

<br>

VSCODE가 설치되었다는 가정하에서 Django-Blog 프토젝트 폴더를 만든다.

<br>

```
mkdir Django-Blog
cd Django-Blog
code .
```

<br>

다음과 같이 VirtalEnv를 설정한다.

[VSCODE에서 Python VirtualEnv 실행하기](/2019/09/30/How-to-exectue-Python-VirtualEnv-in-VSCODE){:target="_blank"}

<br>


#### vscode에서 black, pylint 적용

black은 파이썬 코드 스타일(pep8)을 자동으로 적용하게 해주는 패키지이다. 
pylint는 코드 스타일이 맞지 않거나 오류가 있는 경우 알려주는 역할을 한다.  

<br>

```
pip install black
pip install pylint
```

<br>

.vscode 폴더안의 setting.json에 다음을 추가한다.

**.vscode/setting.json**

```json
{
    "python.formatting.provider": "black",
    "python.formatting.blackArgs": [
        "--line-length",
        "100"
    ],
    "editor.formatOnSave": true,
    "python.linting.pylintEnabled": true,
    "python.linting.enabled": true,
    "python.linting.lintOnSave": true,
}
```

<br>

참고로 VSCODE의 Extension에서 Django를 설치했을 때 Django 플러그인 모드에서 VScode에서 [emmet 기능](https://code.visualstudio.com/docs/editor/emmet){:target="_blank"}이 제대로 되지 않을 경우 setting.json에 다음을 추가한다.


```json
    "files.associations": {
        "**/templates/*.html": "django-html"
    },
    "emmet.includeLanguages": {"django-html": "html"},
```

<br>

---

<br>

### Django 설정

<br>

django를 설치한다.

```
pip install django
```

<br>
django project는 다음과 같이 생성한다. 여기서는 blog라는 프로젝트를 생성하였다.

<br>
> django-admin startproject [프로젝트명]

<br>
```
django-admin startproject blog
```

<br>

```
cd blog
python manage.py migrate
```

<br>

관리자를 생성한다. username, email, password를 입력한다

<br>

```
python manage.py createsuperuser
```

<br>
실행해 본다.

<br>
```
python manage.py runserver 127.0.0.1:7000
```

<br>
[http://127.0.0.1:7000/](http://127.0.0.1:7000/)에 접속하면 다음의 화면이 나올 것이다.

<br>

![django_initial.png](/images/posts/2020-12-21/django_initial.png)



---

#### Reference

[black](https://github.com/psf/black){:target="_blank"}

[https://jhyeok.com/python-with-vscode/](https://jhyeok.com/python-with-vscode/){:target="_blank"}