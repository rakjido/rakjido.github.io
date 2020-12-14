---
layout: post
title: Django Blog 로드맵
author: "Rooftop Hero"
comments: false
tags: Django
---
<br>

> Django 웹 프레임워크 최소 기능을 정의하고 어떻게 구현할 것인가에 대한 로드맵을 그린다.

<br>

웹프레임워크를 빨리 파악하는 방법은 무엇일까.

우선 어떤 웹페이지의 CRUD, 즉 생성(Create), 읽기(Read), 업데이트(Update), 삭제(Delete)를 어떻게 하는지 만들어 보고
보안이 된 회원가입 기능(authentication)을 구현해보는 것이다.

검색에서 상위 순위에 오르는 것은 효율적인 마케팅 수단이 되므로 검색엔진 최적화를 위해 Meta 태그와 Sitemap을 추가한다.

로그파일은 장애를 파악할 수 있도록 text 파일로 저장한다. 

이 정도면 웹프레임워크의 [최소기능제품(Minimum Viable Product)](https://brunch.co.kr/@jjollae/7){:target="_blank"}라 볼 수 있다.

위의 기능을 Django와 Mysql 데이터베이스를 조합하여 구현할 것이다. 

<br>
2020년 12월 11일 기준 기업가치가 470억 달러로 평가되는 AirBnB도 최초의 MVP는 이랬다 한다. 용기를 내자(?)


![airbnb.png](/images/posts/2020-12-14/airbnb.png)


Agile한 개발을 위해서는 처음부터 [DevOps](https://brunch.co.kr/@jowlee/120){:target="_blank"}를 구축해야 한다.
PEP8 코드스타일을 따르고 비전관리툴로 Git과 Github를 사용할 것이고 Git 사용규칙을 정할 것이다. 테스트용 배포에서는 편의를 위해 Docker를 사용하고 Unittest로 단위테스트와 통합테스트를 하며, Selenium으로 기능 테스트를 할 것이다. Travis CI로 테스트를 자동화 한다. 최종 배포는 Nginx와 uWSGI로 할 것이다.

이런 내용을 정리하면 아래와 같은데

일종의 간단한 [요구사항명세서(Software Requirements Specification)](https://medium.com/@dnjswbf/%EC%9A%94%EA%B5%AC%EC%82%AC%ED%95%AD-%EC%A0%95%EC%9D%98%EC%84%9C-%EA%B8%B0%EC%88%A0%EC%84%9C-%EB%AA%85%EC%84%B8%EC%84%9C-b8d47599ab64){:target="_blank"} 이다.


### 기능


#### 필수 기능


```
    * 회원 기능
        - authentication
            email

    * 블로그 기능
        - CRUD
        - pagination
    * SEO
        - Sitemap
        - meta
    * Log
        - log text file
```


#### 필수 기술


```
    * PEP8
    * Django
    * MySQL
    * 단위 테스트, 통합 테스트
    * Git & Github, Git Flow
    * uWSGI
    * Docker
    * Travis CI
```


#### 선택 조건


```
    * Setting은 config.py에서 개발, 운용을 구분하여 설정
```

<br>
<br>

---

### ERD (Entity-Relationship Diagram)

[MySQL Workbench](https://dev.mysql.com/downloads/workbench/){:target="_blank"}를 이용하여 ERD 모델링을 하였다. 

참고로 id (ERD에서는 idx)는 INT가 아닌 BIGINT로 설정해야 한다. 서비스가 커질 경우 INT는 한계값에 도달하게 된다. 

<br>

![django_blog_erd.jpg](/images/posts/2020-12-14/django_blog_erd.JPG)

<br>

---

### git 생성

Github 또는 Gitlab에서 git을 생성한다.

[https://github.com/rakjido/Django-Blog.git](https://github.com/rakjido/Django-Blog.git){:target="_blank"}

<br>

### git commit 분류코드

<br>
git-flow 전략은 [이곳](https://woowabros.github.io/experience/2017/10/30/baemin-mobile-git-branch-strategy.html){:target="_blank"}을 참조한다.

여기서는 git commit 분류코드만을 적용하기로 한다.

```
ENH: (Enhancement) 개선하거나 신기능 추가
BUG: 버그 수정
DOC: (Documentation) 문서화 관련된 작업
TST: (Test) 새로운 유닛테스트를 추가하거나 기존 테스트를 수정
BLD: (Build) 빌드 프로세스 관련 코드 혹은 스크립트를 수정
PERF: (Performance) 계산 속도의 개선과 관련된 작업
CLN: (Cleanup) 코드를 정리하거나 리팩토링한 작업
```

<br>
git commit을 할 때 다음과 같이 커밋 메시지를 작성한다.

<br>
예시 

> [ENH] board의 view.py에서 board_list에 pagination 추가  

> [TST] test_unit에 test_board_urls 추가


<br>

---


#### Reference


[git commit 분류코드](http://story.haezoom.com/?p=936){:target="_blank"}

