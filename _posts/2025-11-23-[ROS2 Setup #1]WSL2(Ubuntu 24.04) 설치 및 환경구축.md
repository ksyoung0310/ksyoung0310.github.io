---
layout: post
title: "[ROS2 Setup #1]WSL2(Ubuntu 24.04) 설치 및 환경구축"
date: 2025-11-23 20:00:00 +0900
categories: [ROS]
tags: [Embedded, WSL2]
---

## **WSL2 설치 과정**

#### 🛠 **개발 환경**

- **OS:** Windows 11 + WSL2 (Ubuntu 24.04)
- **ROS Version:** ROS 2 Jazzy Jalisco
- **Hardware:** YDLidar X3

### **1. Windows 기능 활성화 및 비활성화**

![WSL2_01](../images/2025-11-23-WSL2(Ubuntu 24.04) 설치 및 환경구축/WSL2_01.png)

제어판에서 **'프로그램 추가/제거 → Windows 기능 켜기/끄기'**에서 Linux용 Windows 하위 시스템과 Virtual Machine Platform 체크가 해제되어 있으면 체크한 이후 재부팅합니다.



### **2. Windows 기능 활성화 후 Ubuntu 설치**

![WSL2_02](../images/2025-11-23-WSL2(Ubuntu 24.04) 설치 및 환경구축/WSL2_02.png)

이후 **명령 프롬프트(cmd) 또는 PowerShell**을 사용하여 Ubuntu를 설치합니다.

먼저 **`wsl --list --online`** 명령어를 통해 온라인에서 설치 가능한 Ubuntu 버전을 확인합니다. 

```powershell
wsl --list --online
```

그다음, 아래 명령어를 사용하여 원하는 버전을 설치합니다.

```powershell
wsl --install -d Ubuntu-24.04
```



![WSL2_03](../images/2025-11-23-WSL2(Ubuntu 24.04) 설치 및 환경구축/WSL2_03.png)

설치가 완료되면, 그림과 같이 **새로운 Linux 계정의 사용자 이름(Username)과 비밀번호(Password)**를 설정해야 합니다. 이때, 패스워드는 간단하게 설정하는 것을 추천 드립니다.



## **VSCode를 통한 WSL 사용법**

이제 **VSCode를 활용한 WSL 사용법을 알아보겠습니다.**

설치된 WSL 환경에 접근하는 방법은 터미널에서 `wsl` 명령어를 직접 사용하는 방법과 VSCode의 원격 개발 기능(SSH/Remote Development)을 활용하는 방법이 있습니다. 

이 섹션에서는 **VSCode를 통해 더욱 편리하게 WSL 환경을 사용하는 방법**을 중점적으로 다루겠습니다.



![WSL2_05](../images/2025-11-23-WSL2(Ubuntu 24.04) 설치 및 환경구축/WSL2_05.png)



이 명령어는 **Windows PowerShell (관리자 권한)**에서 실행해야 합니다. 

명령을 실행하면 WSL 환경 내에 VS Code 서버가 자동으로 설치되며, 설치 완료 후 VS Code 창이 **WSL 환경에 연결된 상태**로 열립니다.



![WSL2_06](../images/2025-11-23-WSL2(Ubuntu 24.04) 설치 및 환경구축/WSL2_06.png)

좌측 하단의 파란색의 WSL 버튼을 클릭하면 WSL 원격 연결 해제 및 연결 버튼이 활성화되며 아래의 터미널에서 필요한 명령어를 실행하여 우분투를 사용할 수 있습니다.



오늘 포스팅에서는 ROS 2 개발 환경 구성을 위한 **WSL2 설치 과정과 VSCode 연동 사용법**까지 알아보았습니다. 다음 시간에는 **본격적으로 ROS 2를 설치**하고, 구축된 환경에서 실습하는 내용을 다루겠습니다.



## **References**

- [ASH_blog](https://velog.io/@tbvjvsladla/posts)
