# ROS2 LIMO

ROS 2 기반 LIMO 자율주행 로봇 학습 및 프로젝트 저장소.

## Project Overview

본 프로젝트는 ROS 2 환경에서 LIMO 기반 자율주행 로봇의 구조와 제어 방법을 학습하고,
센서, 토픽, 노드, 주행 제어 및 시뮬레이션을 단계적으로 실습하는 것을 목표로 한다.

## Development Environment

- OS: Ubuntu 22.04 LTS
- ROS 2: Humble
- Robot Platform: LIMO
- Language: Python / C++
- Simulation: Gazebo
- Development: VS Code / code-server
- Cloud: Oracle Cloud Infrastructure
- Version Control: Git / GitHub

## Directory Structure

```text
ros2-limo/
├── .gitignore
├── README.md
├── src/
├── scripts/
├── docs/
└── experiments/
```

## Main Topics

### ROS 2

- Node
- Topic
- Publisher / Subscriber
- Service
- Action
- TF / TF2
- Launch
- Parameter
- QoS

### Autonoous Driving
- Sensor data processing
- Odometry
- LiDAR
- Camera
- Path following
- Velocity control
- Obstacle avoidance

### Simulation

- Gazebo
- RViz
- LIMO simulation
- Sensor visualization

## Cloud Development Environment

본 프로젝트는 Oracle Cloud 븰�쑘의 의 원격 개발 환경에서 관리한다.

```text
Local PC
   │
   │ Chrome / Edge
   ▼
Tailscale Funnel
   │
   ▼
code-server
   │
   ▼
Oracle Cloud Ubuntu
   │
   └── ROS 2 / LIMO workspace
```

이를 통해 별도의 로컬 개발환경 설치 없이 웹 브라우저에서 동일한 ROS 2 개발 환경에 접근할 수 있다.

## Progress

- [ ] ROS 2 기본 구조 학습
- [ ] LIMO 패키지 구성
- [ ] Topic 통신 실습
- [ ] Sensor 데이터 처리
- [ ] Gazebo 시뮬레이션
- [ ] RViz 시각화
- [ ] 자율주행 제어
- [ ] 프로젝트 결과 정리

## Notes

실습 과정에서 발생한 문제와 해결 방법은 `docs/`에 기록한다.
실험 결과와 비교 자료는 `experiments/`에 저장한다.
