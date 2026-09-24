# LIMO Project Context

## 1. Project Overview

Project:
2026-2 캡스톤디자인 "LIMO의 모험"

Project goal:

AgileX LIMO mobile robot을 기반으로
실내 환경에서 자율적으로 순찰하고 목적지까지 이동하여
사용자를 안내할 수 있는 ROS 2 기반 시스템을 구현한다.

Repository:

https://github.com/CHUNGJINWOO/ros2-limo

Related infrastructure repository:

https://github.com/CHUNGJINWOO/ros2

Related AI infrastructure:

https://github.com/CHUNGJINWOO/ai-hub

---

## 2. Project Scope

The project is developed incrementally.

Intended development pipeline:

ROS 2 basics
→ LiDAR
→ obstacle detection
→ SLAM
→ localization
→ Nav2
→ path planning
→ obstacle avoidance
→ autonomous patrol
→ guidance

The final system should combine these components into
an indoor autonomous patrol and guidance system.

---

## 3. User's Main Responsibility

The user's primary responsibility is:

- Autonomous driving
- Dynamic obstacle avoidance

Main technical scope:

- LiDAR-based obstacle detection
- SLAM integration
- Localization / AMCL
- Navigation2 (Nav2)
- Global path planning
- Local path planning / control
- Path following
- Dynamic obstacle avoidance
- Autonomous patrol
- Guidance behavior

Other team members may handle system-level integration,
sensor fusion, hardware setup, or other components.

The user's implementation should integrate with those components
rather than unnecessarily duplicating them.

---

## 4. Repository Role

This repository contains the LIMO ROS 2 base software
and project-specific autonomous driving development.

Current repository structure:

ros2-limo/
├── README.md
├── AGENTS.md
├── docs/
├── experiments/
├── scripts/
│   └── remote_teleop_node.py
└── src/
    └── limo_ros2/
        ├── limo_base/
        ├── limo_car/
        ├── limo_description/
        └── limo_msgs/

### limo_base

Provides the basic LIMO driver and hardware interface.

Main responsibilities include:

- LIMO driver
- Serial communication
- velocity command handling
- odometry
- IMU-related publishing
- robot status
- TF-related processing
- LIMO base launch files

### limo_car

Provides LIMO Ackermann simulation components.

Main areas include:

- Gazebo model
- sensor simulation
- robot model
- launch files
- RViz configuration
- simulation worlds

### limo_description

Provides URDF/Xacro and robot visualization resources.

### limo_msgs

Contains custom ROS 2 messages used by the LIMO project.

### scripts

Contains project-level experimental scripts,
including remote velocity command publishing.

---

## 5. Important Architectural Boundary

The original AgileX LIMO packages should be treated as the
base platform.

Project-specific autonomous driving functionality should
preferably be implemented in separate project packages or
project-specific modules rather than unnecessarily modifying
the original LIMO driver.

The goal is to preserve the distinction between:

1. LIMO base functionality
2. Simulation/model functionality
3. Project-specific autonomous driving functionality

---

## 6. Current Functional Boundary

The repository currently provides the foundation for:

- LIMO ROS 2 communication
- LIMO driver
- robot state and odometry structures
- TF-related processing
- Ackermann robot model
- Gazebo simulation resources
- RViz configuration
- custom LIMO message definitions
- basic remote velocity command experiments

The repository does not yet contain the complete
project-level autonomous driving stack.

The following are development targets rather than
already-completed repository features:

- LiDAR obstacle detection
- SLAM
- Localization / AMCL
- Nav2
- Global path planning
- Local path planning / control
- Dynamic obstacle avoidance
- Autonomous patrol
- Guidance behavior
- Full autonomous-driving integration

---

## 7. Development Environments

### Local simulation environment

Primary simulation environment:

- Windows
- WSL2
- Ubuntu 22.04.5
- x86_64
- ROS 2 Humble

The local x86_64 environment is the primary environment
for Gazebo and autonomous-driving simulation.

Primary ROS workspace:

~/ros2_ws

### Oracle Cloud environment

Oracle Cloud:

- Ubuntu 22.04.5
- ARM64 / aarch64

Primary purposes:

- remote development
- project file access
- storage and backup
- data processing
- AI-Hub infrastructure

Oracle Cloud ARM64 should not be treated as the primary
Gazebo simulation environment.

---

## 8. Project Repository vs ROS Workspace

The Git repository and ROS workspace are separate concepts.

Git repository:

~/school/2026-2/ros2-limo

ROS workspace:

~/ros2_ws

The ROS workspace may contain packages used for experiments
or testing that are not yet part of the Git repository.

Before assuming that a ROS package exists in the repository,
inspect the actual repository tree.

---

## 9. Source and Reference Priority

Implementation and explanations should use the following
source priority:

1. Professor-provided [WeGo] Limo_ROS2 textbook
2. AgileX official LIMO ROS 2 source and documentation
3. Official ROS 2 documentation
4. Official Navigation2 documentation
5. Official SLAM Toolbox documentation
6. Community repositories and other secondary sources

Community examples may be used for comparison or troubleshooting,
but should not automatically be treated as the project's
implementation standard.

---

## 10. Professor's LIMO Material

The professor-provided [WeGo] Limo_ROS2 textbook is the
primary educational reference for this project.

In particular, LiDAR-related implementation should begin
from the structure demonstrated in the textbook and then
be expanded as the project requirements become more advanced.

The project's autonomous-driving implementation should remain
understandable and explainable in the context of the professor's
course material.

---

## 11. Intended Autonomous Driving Architecture

The intended high-level architecture is:

LIMO Sensors
    │
    ├── LiDAR
    ├── IMU
    └── Odometry
            │
            ▼
      Perception / Obstacle Detection
            │
            ▼
       SLAM / Localization
            │
            ▼
            Nav2
            │
      ┌─────┴─────┐
      ▼           ▼
 Global Planner  Local Controller
      │           │
      └─────┬─────┘
            ▼
       Velocity Commands
            │
            ▼
           LIMO

Obstacle avoidance is treated as an important part of the
local navigation and safety behavior.

---

## 12. Development Philosophy

The project should be implemented incrementally.

Each feature should move through:

Design
→ implementation
→ build
→ test
→ debugging
→ documentation

The goal is not only to make the robot work,
but also to make the implementation explainable
in a capstone report and presentation.

Important development decisions should record:

- why the method was selected
- alternatives considered
- implementation details
- problems encountered
- solutions attempted
- final parameter choices
- simulation results
- real-robot differences

---

## 13. AI-Hub Relationship

AI-Hub is a separate repository and separate software system.

Repository:

https://github.com/CHUNGJINWOO/ai-hub

Its long-term purpose is to provide a common knowledge and
MCP-based infrastructure that can connect project documents,
code, and multiple AI/agent systems.

The current LIMO project is one of the primary projects
that AI-Hub is intended to understand and index.

The relationship is:

AI-Hub
    │
    ├── project knowledge / document retrieval
    ├── MCP tools
    └── future AI / agent integrations
             │
             └── ros2-limo

AI-Hub should not be treated as part of the LIMO robot runtime.
It is development infrastructure surrounding the project.

---

## 14. Infrastructure Repository Relationship

The repository:

https://github.com/CHUNGJINWOO/ros2

contains ROS 2 development infrastructure, cloud environment
configuration, and related operational documentation.

Relationship:

ros2
    │
    └── development infrastructure
             │
             └── ros2-limo

ros2-limo
    │
    └── LIMO project implementation

ai-hub
    │
    └── AI / knowledge infrastructure
