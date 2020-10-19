---
layout: post
title: AI가 코딩을 하기 시작했다
author: "Rooftop Hero"
comments: false
tags: Trend
---


2020년 기준, 코딩에 AI를 접목하는 사례는 크게 다음과 같이 구분할 수 있습니다.

#### 1. 코드의 자동완성을 제시

>VS Code의 Snippet같은 기능에 AI를 적용해서 개발자의 코드나 Github들의 repository에서 패턴을 학습하여 좀더 적합한 키워드를 제시합니다. 

**[Kite](https://kite.com/){: target="_blank"}**는 VS code, Sublime Text, Pycharm, Atom, Vim에서 플러그인을 통해, 머신러닝을 이용해 파이썬 코드를 완성을 도와주는 툴입니다. 기존의 코드제시(Snippet)와 비슷하지만 차이점은 사용자의 코드에서 사용한 패턴을 탐지해서 가장 관련성이 높은 순으로 제시합니다. 현재는 파이썬만 가능하지만 다른 언어도 사용가능하게 할 예정이라 합니다.

**[DeepCode](https://www.deepcode.ai/){: target="_blank"}**는 open-source 코드에서 학습하여 코드를 개선하는 제안을 하는 AI 소프트웨어입니다. 개발자는 이 플랫폼을 코드리뷰나 검사툴로 사용할 수 있습니다. 사용자에게 코드상의 취약점을 알려줍니다. Visual Studio Code에 [DeepCode extension](https://marketplace.visualstudio.com/items?itemName=DeepCode.deepcode){: target="_blank"}을 추가해 사용할 수 있습니다. 그리고 DeepCode는 Github, Gitlab, Bitbucket과 같은 플랫폼과 결합하여 사용할 수 있습니다. 

**[PyCharm](https://www.jetbrains.com/pycharm/){: target="_blank"}**은 널리 사용되는 있는 파이쎤 IDE로, 코드 자동완성, 코드 검사, 자동화된 코드 리팩토링 등을 제공합니다. 



#### 2. DevOps에 적용

>DevOps에서 테스트 , 이슈탐지등에 우선 주력하면서 점차 DevOps 전반으로 확장 적용될 것으로 예상됩니다.

**[Embold](https://www.embold.io/){: target="_blank"}**는 Github등의 respositry내의 소스코드를 스캔하여 소프트웨어 품질, 이슈 탐지 및 솔루션 제시를 하는 다차원 분석툴입니다.

**[mabl](https://www.mabl.com/){: target="_blank"}**은 머신러닝 기반의 테스트 자동화를 수행하는 통합 DevTestOps 플랫폼입니다. 이 서비스는 Sass(Software-as-a-Service)의 형태로 제공됩니다.

**[Run.ai](https://www.run.ai/){: target="_blank"}**은 딥러닝 가상화 및 가속화 툴입니다. 값비싼 GPU 자원을 최대한 사용할 수 있도록, 컴퓨팅 자원을 가상자원풀(virtual pool)로 특정 인프라에만 과부하가 걸리지 않도록 데이터와 모델을 자동으로 분산하여 트레이닝을 합니다. 그 상태 및 성과를 시각적으로 확인할 수 있어 사용자가 적은 비용으로 보다 빠르게 컴퓨팅 작업을 수행할 수 있도록 합니다. 2019년 1300만불의 시리즈 A 투자를 받았습니다.

이런 형태는 쿠버네티스에서 컨테이너(또는 Pod)를 마이크로서비스로 배포하면서 그 자원을 로드밸런싱하는 하는 등, 쿠버네티스의 전반적 관리에도 적용할 수 있을 듯 합니다.  


#### 3. 화면생성

**[Sketch2Code](https://sketch2code.azurewebsites.net/){: target="_blank"}** 마이크로소프트의 웹기반 솔루션으로, 유저 인터페이스를 그린 종이를 사진을 찍어 업로드 하면 자동으로 디자인 패턴을 탐지하여 해당 HTML 컴퍼넌트로 변환해 줍니다. 사용자는 그 HTML코드를 다운로드할 수 있습니다. 

화면을 만들 수 있으면 데이터베이스 테이블도 만들 수 있습니다. 개발자가 테이블 컬럼을 조금 수정하는 형태로 기본적인 웹 마이크로서비스 CRUD는 생성하는 단계까지 예상보다 이른 시일내에 가능하리라 예상됩니다.

