---
layout: post
title: "[ROS2 Setup #1]WSL2(Ubuntu 24.04) 설치 및 환경구축"
date: 2025-11-23 20:00:00 +0900
categories: [Embedded System, Robotics]
tags: [Embedded, WSL2, ROS2, Jazzy, Lidar]
---

## **WSL2 설치 과정**

#### 🛠 **개발 환경**

- **OS:** Windows 11 + WSL2 (Ubuntu 24.04)
- **ROS Version:** ROS 2 Jazzy Jalisco
- **Hardware:** YDLidar X3

### **1. Windows 기능 켜기/끄기**

![Windows 기능 켜기 및 끄기](../images/2025-11-23-[ROS2 Setup #1]WSL2(Ubuntu 24.04) 설치 및 환경구축/Windows 기능 켜기 및 끄기.png)

제어판에서 **'프로그램 추가/제거 → Windows 기능 켜기/끄기'**에서 Linux용 Windows 하위 시스템과 Virtual Machine Platform 체크가 해제되어 있으면 체크한 이후 재부팅한다.



### **2. Windows 기능 활성화 후 Ubuntu 설치**

![스크린샷 2025-11-23 202132](../images/2025-11-23-[ROS2 Setup #1]WSL2(Ubuntu 24.04) 설치 및 환경구축/스크린샷 2025-11-23 202132.png)

이후 cmd 및 PowerShell로 Ubuntu를 설치한다.

1번째 줄의 명령어를 통해 설치할 수 있는 버전을 확인하고, 다음 라인의 명령어로 필요한 버전을 설치한다.

```powershell
wsl --list --online → 온라인에서 설치 가능한 버전 확인
wsl --install -d "설치하고자 하는 Ubuntu 버전"
```



