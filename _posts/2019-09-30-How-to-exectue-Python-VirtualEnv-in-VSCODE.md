---
layout: post
title: VSCODE에서 Python VirtualEnv 실행하기
author: "Rooftop Hero"
comments: false
tags: Python

---

<br>

> Visual Studio Code에서 VirtualEnv를 설정하고 Code Runner로 실행합니다.

<br>

프로젝트를 생성하고자 하는 디렉토리를 만든 후 그 디렉토리 내에서 VSCODE를 실행합니다.

VSCODE의 Extension을 클릭하여 Code runner를 설치합니다.


![vscode1.jpeg](/images/posts/2019-09-30/vscode1.jpeg)


```ctrl + alt+ n``` 을 누르면 해당 python 파일을 실행합니다. 이 경우에는 시스템에서 default로 설정된 python으로 실행이 됩니다.


![vscode2.jpeg](/images/posts/2019-09-30/vscode2.jpeg)

---


```Terminal > New Terminal```로 터미널을 연 후 다음과 같이 가상환경을 설정합니다.

```linux
# MacOS/Linux
python3 -m venv .venv

# Windows
pip install virtualenv
virtualenv .venv 
```


![vscode3.jpeg](/images/posts/2019-09-30/vscode3.jpeg)


VSCODE에서 맥에서는 ```command + shift + p```, 윈도에서는 ```ctrl + shift + p```를 눌러 command palette에서 ```Python>Select Interpreter```를 선택합니다.

```(.venv':venv)```인 python을 선택합니다.


![vscode4.jpeg](/images/posts/2019-09-30/vscode4.jpeg)

---

이제 Code Runner에 VirtaulEnv의 python을 설정합니다.

```프로젝트폴더 > .vscode > settings.json```을 다음과 같이 저장한 후, VSCODE를 재실행합니다.

* MacOS/Linux

```json
{
    "python.pythonPath": ".venv/bin/python",
    "git.ignoreLimitWarning": true,
    "code-runner.executorMap": {
        "python":"$pythonPath $fullFileName",
    }
}

```
<br>

* Windows 10

```json
{
    "python.pythonPath": ".venv\\Scripts\\python.exe",
    "git.ignoreLimitWarning": true,
    "code-runner.executorMap": {
        "python":"$pythonPath $fullFileName",
    }
}
```
<br>

test.py에서 ```ctrl + alt+ n``` 을 누르면 virtualenv환경에서 실행되는 것을 확인할 수 있습니다.


![vscode5.jpeg](/images/posts/2019-09-30/vscode5.jpeg)


Terminal옆의 ```+```버튼을 누르면 VirtualEnv으로 전환됩니다. 

```
윈도10에서는 terminal을 powershell이 아닌 cmd를 선택해야 가상환경이 activate됩니다. 
terminal > select default shell > Command prompt
```
<br>
![vscode6.jpeg](/images/posts/2019-09-30/vscode6.jpeg)


이후 ```pip install 패키지명```으로 원하는 패키지를 install하면 됩니다. 

---

