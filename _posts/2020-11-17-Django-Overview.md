---
layout: post
title: Django 개요와 장단점
author: "Rooftop Hero"
comments: false
tags: Django
---
<br>

> Django에 대한 개요와 장·단점에 대한 견해

<br>

### 개요 

Django는 Python을 사용한 서버사이드 웹프레임워크이다.

<br>

개인적으로 볼 때, Django는 Agile한 개발과 분업에 용이하도록 설계된 프레임워크이다.

<br>
최소기능제품(MVP : Minimum Viable Product)를 만든 후 타겟의 반응을 보면서 계속 수정해야 할 상황이지만 개발자원은 한정되어 있을 때 적합하다.

<br>

2019년 12월 기준, Github에서 가장 인기있는 백엔드 프레임워크 순위에서 Laravel, Flask, ExpressJS에 이어 4위에 랭크되어 있다.

<br>

![popular_framework.png](/images/posts/2020-11-17/popular_framework.png)

<br>

---

### 장점

#### 1. Django Admin을 이용한 빠른 요건 구현

Django Admin을 이용하여 빠르게 요건을 구현한 후 수정해 나갈 수 있다는 점은 Django의 최대 장점 중 하나이다. 

[날로 먹는 Django admin 활용](https://www.slideshare.net/hannal.cha/django-admin-81652288){:target="_blank"}을 참고하면 이러한 장점을 잘 이해할 수 있다.

<br>

#### 2. App 단위의 독립적인 구성 

Django의 프로젝트는 ```App```이라는 단위들로 구성된다.

쇼핑몰을 예를 든다면 다음과 같은 기능들이 필요하다.
```
Shop
    - Account 
    - Product
    - Order
    - Delivery
    - Admin_account
```

Django에서는 Account, Product등을 별도의 App으로 구성한다. 

App내에서는 가능한 한 독립적인 환경을 구성한다.

하나의 App은 각각 별도의 모델(Model), 템플릿(Template), 뷰(View)를 가진다. 이런 설정은 개발에서 분업을 용이하게 한다.
Account는 프로그래머 A, Order는 프로그래머 B와 같이 배분한 후 완성하면 합체하기 편리하다. 
이럴 때 흩어져 있는 static 파일을 모으기 위해 ```collectstatic```을 사용한다.

이러한 기능들이 점점 커지고 복잡해 질 경우 App을 MSA(Micro Services Architecture)로 전환할 수 있다.

<br>

#### 3. 보안 

또 다른 장점은 보안을 들 수 있다. 최근 많은 사람들이 선호하는 Flask는 직관적이고 간결하며 이해하기 용이하지만 (미처 생각이 미치지 않는) 보안의 문제점이 발생할 여지가 있다. 
Django는 다양한 공격을 방지할 수 있는 기능들이 이미 구현되어 있다.

<br>
<br>

### 단점


1. Django는 예상보다 러닝커브가 낮다. Spring Boot와 비교해도 아주 쉽다고 볼 수는 없다. 

2. Django의 모델은 빠른 기능 구현이 가능하지만 성능 이슈를 야기할 수 있다. Transaction이 많지 않은 도메인에 적합해 보인다. 

<br>


**다음** : [Django Blog 로드맵](/2020/12/14/Django-Blog-Minimal-Requirement-Specification)  

---

#### Reference

[Django 소개](https://developer.mozilla.org/ko/docs/Learn/Server-side/Django/Introduction){:target="_blank"}

[Most Popular Backend Frameworks 2012-2019](https://www.youtube.com/watch?v=8FQ4zW_F_Iw){:target="_blank"}


