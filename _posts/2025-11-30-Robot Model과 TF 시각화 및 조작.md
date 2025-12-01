---
layout: post
title: "Robot Model과 TF 시각화 및 조작"
date: 2025-11-30 20:00:00 +0900
categories: [ROS2]
tags: [Embedded, WSL2, ROS2, Jazzy, Lidar]
---

앞에서 패키지를 설치하였다고 가정하고 이제 로봇을 시각화하고 로봇을 위한 TF에 대해서 알아보겠습니다. 아직 로봇을 만들지 않았기 때문에 기존의 생성되어있는 URDF 튜토리얼 패키지를 설치하여 진행하겠습니다.



### **1. TF(TransForm)**

#### 1.1. 패키지 설치

```bash
sudo apt install ros-jazzy-urdf-tutorial
cd /opt/ros/jazzy
ls
```



다음 명령어를 실행하면 주어진 위치의 파일 목록이 출력될텐데 `share`은 기본적으로 패키지를 생성할 때 구성 파일과 같은 URDF 파일과 실행 파일들을 설치하는 경우 `share` 디렉터리에 재방문하게 될 것입니다.

```bash
cd /opt/ros/jazzy
ls
```

![Screenshot from 2025-12-01 11-12-22](../images/2025-11-30-로봇 시각화 시작하기(1)/TFs_01.png)



### 2. 로봇 시각화

이후 URDF 패키지를 실행시켜 로봇을 rviz 창에서 시각화하여 보겠습니다. `ls` 명령어는 경로 상에 있는 파일 목록들을 출력하는 명령어입니다.

```bash
cd urdf_tutorial
ls
cd urdf
ls
ros2 launch urdf_tutorial display.launch.py model:=urdf/08-macroed.urdf.xacro
```

![TFs_02](../images/2025-11-30-로봇 시각화 시작하기(1)/TFs_02.png)

Rviz2의 Displays의 옵션에는 Grid, RobotModel, TF 등이 존재합니다. 각각의 기능들을 아래에서 살펴보겠습니다.



### 3. Rviz2에서의 로봇 구조(RobotModel)

#### 3.1. 링크(Links)

- 링크 목록: `RobotModel` 항목을 펼쳐서 `links` 항목을 보면 로봇을 구성하는 모든 부품들의 목록을 확인할 수 있습니다.
- 시각화 제어: 특정 링크를 체크 해제하면 그 부품만 화면에서 사라집니다. 이 기능을 사용하여 로봇의 부품 구성을 파악할 수 있습니다.

![image-20251201120852021](../images/2025-11-30-로봇 시각화 시작하기(1)/image-20251201120852021.png)

#### 3.2. 투명도 조절(Alpha)

로봇 모델의 `Alpha` 설정을 조절하여 모델의 투명도를 변경할 수 있습니다.



### 4. 로봇의 관계(TF)

로봇 모델이 부품들을 의미한다면, TF(TransForm)은 로봇 부품들이 어디에 위치하며 어떻게 움직이는지를 좌표계를 통해 정의하는 가장 중요한 정보입니다. 일반적으로 Rviz를 실행하면 빨간색의 `x축`, 초록색의 `y축`, 파란색의 `z축`이 시각화됩니다.

#### 4.1. TF 활성화 및 좌표계

1. Displays 속성의 맨 아래의 `TF` 항목을 체크하여 활성화/비활성화 가능
2. 활성화 시 로봇의 각 링크에 좌표축이 나타나며 각 링크는 자체적인 프레임을 가지고 있음
3. TF의 역할: 프레임들이 서로 연결되어 각 링크의 상대적인 위치와 자세를 규정합니다. 따라서 TF는 로봇을 올바르게 구동하는 데 필수적인 핵심 정보입니다.

#### 4.2. Joints and TF

로봇의 관절(Joints)는 TF를 통해 정의됩니다. 관절의 축이 두 링크 사이의 변환(TF)을 의미하며, 이는 두 부품이 서로 상대적으로 어떻게 움직이는지를 나타냅니다.



### 5. Joint State Publisher GUI로 로봇 조작하기

Joint State Publisher GUI 창으로 로봇의 움직임을 실시간으로 관찰할 수 있습니다.

![Screenshot from 2025-12-01 11-54-35](../images/2025-11-30-로봇 시각화 시작하기(1)/Screenshot from 2025-12-01 11-54-35.png)

1. **슬라이더 조작:** GUI 창에는 로봇의 가동 관절(`right_front_wheel_joint`, `gripper_extension`, `head_swivel` 등)의 이름과 슬라이더가 표시됩니다.

2. **움직임 확인:** 슬라이더를 마우스로 좌우로 움직여 보세요.

- **바퀴 회전:** `right_front_wheel_joint`를 움직이면 바퀴가 **Y축**을 중심으로 회전하는 것을 볼 수 있습니다.
- **그리퍼 확장:** `gripper_extension`을 움직이면 그리퍼가 확장(앞뒤로 이동)하는 것을 볼 수 있습니다.
- **머리 회전:** `head_swivel`을 움직이면 머리 부분이 **Z축**을 중심으로 회전하는 것을 볼 수 있습니다.







```
ros2 run tf2_tools view_frames
```

