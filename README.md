# ROS2 LIMO

ROS 2 기반 LIMO 자율주행 로봇 학습 및 개발 프로젝트입니다.

## 1. Project Overview

본 프로젝트는 ROS 2 환경에서 LIMO 이동로봇의 구조와 제어 방법을 학습하고,
센서, ROS 2 통신, 로봇 모델링, Gazebo 시뮬레이션, 원격 제어 기능을 단계적으로
구현하는 것을 목표로 합니다.

주요 개발 환경은 Oracle Cloud Ubuntu 서버와 웹 기반 VS Code(code-server)이며,
GitHub를 통해 소스 코드와 프로젝트 이력을 관리합니다.

## 2. Architecture

```
Local PC
   │
   │ Chrome / Edge
   ▼
Tailscale Funnel
   │ HTTPS
   ▼
127.0.0.1:8080
   │
   ▼
code-server
   │
   ▼
Oracle Cloud Ubuntu
   │
   └── ROS 2 / LIMO
```

서버 내부에서는 AI Knowledge Hub도 별도로 운영합니다.

```
Oracle Cloud
├── code-server
│   └── 127.0.0.1:8080
│
├── AI Knowledge Hub
│   └── 127.0.0.1:8000
│
└── PostgreSQL / pgvector
```

## 3. Package Structure

```
ros2-limo/
├── README.md
├── .gitignore
│
├── scripts/
│   └── remote_teleop_node.py
│
└── src/
    └── limo_ros2/
        ├── limo_base/
        ├── limo_car/
        ├── limo_description/
        └── limo_msgs/
```

### limo_base

LIMO의 기본 드라이버와 하드웨어 인터페이스를 담당합니다.

주요 구성:
- C++ LIMO driver
- Serial communication
- TF publishing
- LIMO base launch files
- YDLIDAR 관련 launch

### limo_car

LIMO Ackermann 모델과 Gazebo 시뮬레이션 관련 구성을 담당합니다.

주요 구성:
- Ackermann model
- Gazebo launch
- RViz configuration
- URDF / Xacro

### limo_description

LIMO 로봇 모델의 URDF/Xacro 및 시각화 구성을 관리합니다.

주요 구성:
- URDF
- Xacro
- Gazebo model description
- RViz configuration

### limo_msgs

프로젝트에서 사용하는 사용자 정의 ROS 2 메시지를 관리합니다.

예: `LimoStatus.msg`

## 4. Remote Teleoperation

`scripts/remote_teleop_node.py`를 이용하여 LIMO 원격 제어 기능을 실험합니다.

향후에는 다음 기능을 단계적으로 추가할 예정입니다.
- Keyboard teleoperation
- Velocity command
- Sensor feedback
- Autonomous driving control integration

## 5. ROS 2 Topics and Concepts

본 프로젝트에서 중점적으로 학습하는 ROS 2 개념:
- Node
- Topic
- Publisher / Subscriber
- Service
- Action
- Parameter
- QoS
- TF / TF2
- Launch system

## 6. Simulation

Gazebo와 RViz를 이용하여 LIMO의 동작과 센서 데이터를 확인합니다.

주요 실습:
- LIMO model visualization
- Ackermann simulation
- Sensor simulation
- RViz visualization
- TF 확인
- Robot state 확인

## 7. Cloud-Based Development Environment

본 프로젝트는 Oracle Cloud 기반의 원격 개발 환경을 사용합니다.

```
Chrome / Edge
      │
      ▼
Tailscale Funnel
      │ HTTPS
      ▼
code-server
      │
      ▼
Oracle Cloud Ubuntu
      │
      └── ROS 2 / LIMO workspace
```

장점:
- 로컬 PC에 별도 VS Code 설치 없이 접근 가능
- 장소와 장치에 관계없이 동일한 개발 환경 사용
- ROS 2 환경과 프로젝트 파일의 중앙 관리
- GitHub와 연계한 버전 관리

## 8. Security

웹 IDE는 다음과 같은 방식으로 보호합니다.

**code-server**
```
bind-addr: 127.0.0.1:8080
auth: password
```
code-server는 외부 네트워크 인터페이스가 아닌 localhost에만 바인딩합니다.

**Tailscale Funnel**

외부 브라우저 접근은 Tailscale Funnel을 통해 HTTPS로 전달합니다.
```
Internet
   ↓
Tailscale Funnel
   ↓
127.0.0.1:8080
   ↓
code-server
```

**Fail2Ban**

code-server 전용 Fail2Ban 정책을 사용합니다.
```
maxretry = 5
findtime = 600 seconds
bantime  = 3600 seconds
```
즉, 10분 안에 로그인 5회 실패 → 1시간 차단 구조입니다.

## 9. Large Mesh Assets

LIMO 본체 모델에는 용량이 큰 `.dae` / `.stl` mesh 파일이 포함되어 있습니다.

Git 저장소 크기와 관리 효율을 위해 대형 본체 mesh 일부는 GitHub 저장소에서 제외하고,
실제 Oracle Cloud ROS 2 workspace에는 원본을 유지합니다.

따라서 GitHub 저장소는 다음과 같은 핵심 요소를 중심으로 관리합니다.
- Source code
- CMake
- package.xml
- Launch files
- URDF / Xacro
- RViz configuration
- ROS 2 messages
- Scripts
- Documentation

## 10. Development Environment

- OS: Ubuntu 22.04 LTS
- ROS 2: Humble
- Robot: LIMO
- Language: C++ / Python
- Simulation: Gazebo
- Visualization: RViz
- IDE: VS Code / code-server
- Cloud: Oracle Cloud Infrastructure
- Network: Tailscale
- Version Control: Git / GitHub

## 11. Development Progress

- [x] Oracle Cloud 원격 개발 환경 구축
- [x] code-server 웹 IDE 구축
- [x] Tailscale Funnel HTTPS 접속
- [x] Fail2Ban 보안 구성
- [x] LIMO ROS 2 패키지 GitHub 관리
- [x] 원격 Teleoperation 코드 구성
- [ ] ROS 2 Topic 통신 심화
- [ ] LiDAR 데이터 처리
- [ ] Camera 데이터 처리
- [ ] Gazebo 자율주행 시뮬레이션
- [ ] 경로 추종
- [ ] 장애물 회피
- [ ] 자율주행 제어 알고리즘 고도화

## 12. Related Documentation

Cloud 기반 개발 환경 및 운영 과정에서 발생한 문제와 해결 과정은 별도 문서로 관리합니다.

```
docs/
├── SETUP_GUIDE.md
├── CLOUD.md
├── ARCHITECTURE.md
├── TROUBLESHOOTING.md
└── CLOUD_WEB_IDE_SECURITY_RECOVERY.md
```

## 13. Git Workflow

프로젝트 변경사항은 Git을 이용하여 관리합니다.
```
git add .
git commit -m "feat: ..."
git push origin main
```
GitHub를 통해 프로젝트의 구현 과정과 변경 이력을 지속적으로 관리합니다.

## 14. Future Work

향후에는 다음 기능을 중심으로 프로젝트를 확장할 예정입니다.
- LiDAR 기반 장애물 인식
- Camera 기반 환경 인식
- Sensor Fusion
- 경로 계획 및 추종
- 자율주행 제어
- ROS 2 기반 멀티노드 시스템
- AI Knowledge Hub와 개발 코드/문서 연계
