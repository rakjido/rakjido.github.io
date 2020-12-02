---
layout: post
title: DEVIEW 2020 후기로 보는 IT 트렌드
author: "Rooftop Hero"
comments: false
tags: Trend
---
<br>
> 2020년 11월 25일부터 11월 27일까지 DEVIEW 2020 온라인 Session을 참관한 후기

<br>

### Digital Transformation

DEVIEW 2020에서 가장 큰 화두는 AI였지만 그 근저에는 Digital Transformation이 깔려있다. 가치사슬에서 계약이나 판매 단계를 디지털화한 기업이 그 가치사슬 안에서 발생한 대부분의 이익을 가져간다. 

<br>
현 시점에서 AI는 그 기능 자체보다는 모든 것을 연결시키는 역할을 하고 있다.
다른 면에서 AI는 Digital Transformation의 빅뱅(Big Bang)에 대한 대의명분을 제공하고 있다. 

<br>
빅데이터(Big Data)는 빅서비스(Big Service)를 정당화한다. 

<br>
그 과정속에서 거대한 정보 비대칭이 발생하고 있는데, 내부가 아니면 어떤 기술이나 모델이 어느 정도의 실현능력이 있는지 파악하기 어렵다.

<br>
이러한 정보 비대칭을 가장 잘 이용하는 사람이 테슬라(Tesla)의 일론 머스크(Elon Musk)이다. 테슬라에 대한 평가가 어느 정도 컨센서스를 이룰 때 즈음이면 머스크는 시장에 Vision을 하나씩 던진다. 그러면 시장은 그런 비전의 실현 가능성에 대해 오징어가 먹물을 뿜은 듯 평가가 엇갈리게 된다. 그런 방법으로 일론 머스크는 시간과 자금을 확보할 수 있었다. 

<br>
개인적으로는 [언택트 시대의 라이브 오디오기술 - “Being There” for Everyone](https://deview.kr/2020/sessions/357){:target="_blank"}이 흥미로왔다. 콘서트등 현장에서의 공간감이나 관객반응등을 직접 녹음하는 것에는 한계가 있다. 소리를 Object화 하여 공간감과 같은 메타데이터를 반영하면 그에 맞는 공간감이 소리에 반영된다. 쉽게 말하면 소리에 공간감 등을 느끼도록 메이크업을 한다. 소리에 메타데이터를 더하여 object화 한다는 개념은 python이나 node.js 등 프로그래밍만으로 작곡과 프로듀싱이 가능한 DAW(Digital Audio workstation)으로 발전할 수 있지 않을까?

<br>

---

### AI

네이버는 다양한 분야에 AI를 적용해보며 체계를 만들어 가고 있는 것으로 보인다. 

<br>
AI는 최적의 대안을 제시하기보다는 빠른 Reaction을 가능하게 한다. 

<br>
축구에 비유하자면 AI는 아직 메시나 호날두 급은 아니다. 중학교 축구선수 수준일 수도 있다. 하지만 그런 미드필더가 100명이 있다 생각해보라. 우리 팀은 11명. 상대 팀은 100명! 게다가 조금씩 스킬이 향상되고 있다. 100명의 미드필더들이 고객의 Needs가 발생한 순간 이를 감지하고 대안을 제시한 후, 바로 결과를 확인할 수 있다. 정작 우리 팀은 골을 먹었는지조차 모르게 될 것이다. 

<br>
Algorithmic Marketing이 기존 마케팅을 빠른 속도로 대체할 것으로 예상된다. [추천시스템 3.0: 딥러닝 후기시대에서 바이어스, 그래프, 그리고 인과관계의 중요성](https://deview.kr/2020/sessions/356){:target="_blank"}에서는 A/B Test를 A/B/...N개의 Test로 확장, 적용한 후 가장 좋은 모델에게 트래픽을 몰아주는 방식을 취한다. [눈치까지 챙긴 D.I.A.+ 시스템, 싹 다 찾아드립니다. (검색어 의도 분석과 문서 이해 기술, 네이버 검색에 적용하기)](https://deview.kr/2020/sessions/381){:target="_blank"}에서 검색어의 의도 파악은 곧 Needs의 파악이 될 것이다.

AI를 적용할 때 발생하는 이슈 중 하나는 데이터 레이블링(Data Labeling)이다. 지도학습에 필요한 데이터에 대한 레이블링은 아직까지는 사람이 수작업으로 해주어야 하는 상황이어서 많은 비용이 소요되고 있고, 관련 작업을 아웃소싱하는 스타트업들이 늘고 있다. [Low Price, High Quality: 적은 비용으로 모델 성능 높이기!](https://deview.kr/2020/sessions/353){:target="_blank"}와 [데이터 라벨링 너무 귀찮아요: 컨센서스 라벨링 도입기](https://deview.kr/2020/sessions/334){:target="_blank"}에서 관련 이슈의 대안을 제시하였다.

[우리가 볼 수 없는 데이터로 모델을 학습시킬 수 있을까?](https://deview.kr/2020/sessions/328){:target="_blank"}에서는 데이터를 암호화해도 딥러닝 학습을 할 수 있음을 보여주었다. 

최근 딥러닝 관련 발표를 보면서 전반적으로 parameter가 많아지고, 좀 더 많은 computing을 소요하지만 performance는 그리 많이 상승하지 않는 경향이 나타나고 있다는  느낌을 갖게 되었다. 

<br>
만약 그렇다면 현재의 방법론에서는 딥러닝 모델의 성능 향상이 둔화되고 있을 수도 있다.

<br>

---

### 성능개선


Front End에서는 React, Vue등이 SPA(Single Page Application)으로 인한 비약적인 성능개선, 기존 웹의 제약을 넘는 Application 개발이 가능하다는 점에서 채택하는 사이트들이 빠르게 증가하고 있다. 

<br>
Component기반 개발은 어느 정도 Visual Basic의 GUI 제작방법과 비슷한 면이 있다. 

<br>
REST API는 MVC 모델에서 V(View)가 분리될 때 legacy 시스템을 가장 효과적으로 사용하는 대안이 되었다.  

[GraphQL이 가져온 에어비앤비 프론트앤드 기술의 변천사(부제: REST환경에서 GraphQL 기반 UI 설계하기)](https://deview.kr/2020/sessions/337){:target="_blank"}에서는 REST환경에서 GraphQL으로 전환하게 된 배경을 설명한 후 장단점을 발표하였다. 

<br>
[어서와, SSR은 처음이지? (네이버 블로그 Node.js 기반의 Server-Side Rendering 적용기)](https://deview.kr/2020/sessions/403){:target="_blank"}은 Front End에서 Server Side Rendering을 적용할 때 Performance, QA등의 향상등이 있음을 보여주었다. Server Side Rendering을 한다면, (Legacy 시스템이 아니라면) Back End인 Spring Boot나 Django 등이 과연 필요한가에 대한 의문이 들었다.

<br>
[비동기 서버 그까이꺼, Request Scoping만 알면 끝!](https://deview.kr/2020/sessions/330){:target="_blank"}에서는 LINE Sticker store에 비동기 서버인 [Ameria](https://github.com/line/armeria){:target="_blank"}를 적용한 결과 Tomcat 서버보다 평균반응속도가 현격히 빨라진 사례를 소개하였다.

<br>

---


### 로봇    

드론은 비행하는 로봇이다. 앞으로 자동차는 달리는 로봇이 될 것이다. Robotics는 배터리와 수소연료전지, 제어, 반도체, 그리고 AI와 big data등을 모두 견인할 수 있는 산업이다. 

<br>
 [Learning to learn: the challenges of robot task learning](https://deview.kr/2020/sessions/327){:target="_blank"}와 같은 훌륭한 발표가 있었지만, 우선 진입장벽이 높은 로봇생태계에 개발자가 입문할 수 있는 로드맵과 교육환경이 필요해 보인다.

