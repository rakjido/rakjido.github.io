---
layout: post
title: Tensorflow Korea 3차 오프라인 모임 후기
author: "Rooftop Hero"
comments: false
tags: Trend DeepLearning

---

![tensorflow-3rd.png](/images/posts/2019-10-23/Screenshot_2019-10-20-12-48-01-1.png){: width="70%" height="70%"}{: .center}


펀드매니저들은 수익성이 높은 투자전략을 만들려 합니다. 하지만 자산운용사는 운용자금을 모아서 운용을 하면서 수수료 수입을 얻지요. 위험과 수익률을 고려해서 자산운용사는 펀드매니저에게 자원을 배분합니다. 수많은 펀드매니저들이 진입하고, 퇴출되는 동안 자산운용사는 변함없이 운용자금을 모으고 수수료 수입을 얻습니다.

데이터는 돈, AI는 투자전략과 유사합니다. 투자전략의 최적화도 중요하지만 운용자금을 모으는 것에도 염두에 두어야 한다 생각합니다. ```프로덕션 환경에서 연구하기```에서도 머신러닝이 항상 성과를 내는 것을 아님을 인지하고 제품이나 회사에 어느정도 기여할 수 있는지에 대한 고민이 필요함을 이야기하고 있습니다. 

Edge TPU와 TFLite는 구글이 반도체와 IoT에 진입하기 위한 포석으로 보입니다. [보도](https://www.zdnet.co.kr/view/?no=20180726080217){:target="_blank"}에 의하면 분산처리와 데이터를 클라우드로 보내는 역할을 한다 합니다. AI는 중기적으로는 클라우드에, 장기적으로는 반도체로 수렴할 것으로 예측됩니다. (삼성전자 주식을 사야 할까요?)

딥러닝은 일종의 implicit한 quasi-optimization 방법론이라 볼 수 있기 때문에 수리통계에 대한 지식이 Critical하지는 않지만, 모델링이나 효율성 향상에 중요한 역할을 합니다. 예를 들어 backpropagration 방법론은 computing 시간을 경이롭게 줄여줍니다. 이런 수리적인 이슈들은 어느 정도 현재 나오는 모델들에 이미 반영되어 있기에 주요 이슈들은 프로그래밍이나 computing에서 발생하고 있는 듯 합니다. ```Auto scalable한 DL production을 위한 Service infra 구성 및 AI DevOpts Cycle```에서는 Docker와 Kubernetes 및 CPU를 사용한 Scale up한 사례를 제시했는데 무척 흥미로왔습니다.

텐서플로우를 연구하기 위한 로드맵을 찾기에 오프라인 모임은 매우 유익했습니다.

---

[Deep Learning Tutorial](https://github.com/sjchoi86/dl_tutorials){:target="_blank"}

주요 논문을 파악할 수 잇는 [PR12모임](https://www.youtube.com/watch?v=auKdde7Anr8&list=PLWKf9beHi3Tg50UoyTe6rIm20sVQOH1br){:target="_blank"}. 논문 리뷰가 200편이 넘었다는군요!

3차모임 발표자료는 [이곳](https://m.facebook.com/groups/255834461424286?view=permalink&id=1015286128812445
){:target="_blank"}에 있습니다.

---


![tensorflow-3rd.png](/images/posts/2019-10-23/20191020_130607.jpg){: width="100%" height="100%"}{: .center}

정성 들여 준비해주신 운영진 분들께 감사드립니다.

