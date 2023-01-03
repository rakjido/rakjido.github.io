---
layout: post
title: Ubuntu 18.04에서 Spring web을 tomcat에서 실행하기 
author: "Rooftop Hero"
comments: false
tags: DevOps Spring

---

<br>

> Spring Web을 git을 통해 받아 maven으로 build한 후, tomcat에서 실행합니다.

<br>

이 글은 Ubuntu 18.04 LTS를 기준으로 작성되었습니다. GCP, Godo Cloud등 클라우드 서비스에 동일하게 적용할 수 있습니다. 또한 [Windows10에 적용된 WSL2하의 Ubuntu 20.04.1 LTS](https://www.44bits.io/ko/post/wsl2-install-and-basic-usage){:target="_blank"}에서도 문제없이 작동합니다. 


### 1. JDK 1.8 설치

default로 JDK 1.7이 설치되어 있을 경우 다음과 같이 제거합니다.

```
sudo apt-get remove openjdk*
sudo apt-get autoremove --purge
sudo apt-get autoclean
```
<br>
오라클이 java 8에 대한 지원을 중단하여 다음과 같이 Open JDK 1.8을 설치합니다.
```
sudo add-apt-repository ppa:openjdk-r/ppa
sudo apt-get update
sudo apt-get install openjdk-8-jdk
```
<br>
### 2. Mavan 설치

```
sudo apt install maven
```
<br>
### 3. tomcat 설치

tomcat도 ```sudo apt-get install tomcat9```와 같이 설치할 수 있으나 여기서는 파일을 다운로드해서 설치하는 방법으로 진행합니다.

```
mkdir apps
chmod 755 apps
mkdir Downloads
chmod 755 Downloads
cd ~/Downloads
wget https://archive.apache.org/dist/tomcat/tomcat-9/v9.0.12/bin/apache-tomcat-9.0.12.tar.gz
gunzip apache-tomcat-9.0.12.tar.gz
tar -xvf apache-tomcat-9.0.12.tar
sudo mv apache-tomcat-9.0.12/ ~/apps
cd ~/apps
sudo ln -s apache-tomcat-9.0.12/ tomcat
```
<br>
```
sudo apt-get install vim
cd ~/
sudo vi .bash_profile
```
<br>
.bash_profile에 다음과 같이 추가합니다.

```
export TOMCAT_HOME=~/apps/tomcat
export PATH=$PATH:$TOMCAT_HOME/bin
```
<br>
```
source .bash_profile
cd apps/tomcat/bin
./startup.sh           	# tomcat 구동
```
<br>

http://[해당cloud의 ip주소]:8080에서 확인합니다.


![tomcat.JPG](/images/posts/2020-01-30/tomcat.JPG){: width="100%" height="100%"}{: .center}

<br>
tomcat을 중단합니다.
```
./shutdown.sh          	# tomcat 중단
```

<br>
### 4. git 설치 

```
sudo apt-get install git​​
```
<br>
respositories폴더를 만든 후 간단한 Spring MVC Framwork 예제인 
[https://github.com/rakjido/testSpring.git](https://github.com/rakjido/testSpring.git){:target="_blank"}을 git clone하여 maven으로 테스트합니다.

```
cd ~
mkdir repositories
chmod 755 repositories/
cd repositories/
git clone https://github.com/rakjido/testSpring.git
cd testSpring
mvn clean package
```
<br>
BUILD SUCESS가 됨을 확인합니다.

![maven.jpeg](/images/posts/2020-01-30/maven.jpeg){: width="100%" height="100%"}{: .center}
<br>
생성된 war파일을 tomcat밑의 webapps에 ROOT.war로 저장합니다.

```
cd target
cp Web-1.0.0-BUILD-SNAPSHOT.war ~/apps/tomcat/webapps/
cd ~/apps/tomcat/webapps/
rm -rf ROOT ROOT.war
mv Web-1.0.0-BUILD-SNAPSHOT.war ROOT.war
cd ../bin/
./startup.sh
```
<br>
http://[해당cloud의 ip주소]:8080에서 확인합니다.

![spring_web.JPG](/images/posts/2020-01-30/spring_web.JPG){: width="100%" height="100%"}{: .center}


---
