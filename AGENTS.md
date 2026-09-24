# Project Agent Instructions

## 1. Project

Project:
2026-2 캡스톤디자인 "LIMO의 모험"

Goal:
AgileX LIMO를 이용한 실내 자율 순찰 및 안내 시스템 구현.

Repository:
https://github.com/CHUNGJINWOO/ros2-limo

## 2. User Role

Primary responsibility:
- Autonomous driving
- Dynamic obstacle avoidance

Main scope:
- LiDAR-based obstacle detection
- SLAM integration
- Localization / AMCL
- Navigation2 (Nav2)
- Global / local path planning
- Path following
- Dynamic obstacle avoidance
- Autonomous patrol
- Guidance behavior

## 3. Source Priority

When implementing or explaining the project, use the following priority:

1. Professor-provided [WeGo] Limo_ROS2 textbook
2. AgileX official LIMO ROS 2 source and documentation
3. Official ROS 2 documentation
4. Official Navigation2 documentation
5. Official SLAM Toolbox documentation
6. Community repositories and blog posts as secondary references only

Do not copy community code without checking whether it matches the official sources and this project structure.

## 4. Working Rules

Before changing code:

1. Read the relevant README and documentation.
2. Inspect the existing package and source structure.
3. Identify the smallest change that solves the task.
4. Explain the planned change when the change is significant.

Do not make large architectural changes without a clear reason.

Prefer project-specific packages and files over unnecessary modification of the original AgileX packages.

## 5. Implementation and Testing

After code changes, whenever practical:

1. Check `git diff`
2. Build the affected package with `colcon build`
3. Run the relevant node, launch file, or test
4. Check relevant ROS 2 topics, services, actions, logs, or RViz output
5. Report the result

Do not claim that a feature works unless it has actually been tested or the limitation is clearly stated.

## 6. ROS 2 Environment

Primary local simulation environment:

- Windows
- WSL2
- Ubuntu 22.04.5
- x86_64
- ROS 2 Humble

Primary ROS workspace:

~/ros2_ws

Project repository:

~/school/2026-2/ros2-limo

Oracle Cloud ARM64 is primarily used for:
- remote development
- storage and backup
- project infrastructure
- data processing
- AI-Hub services

Do not assume Oracle Cloud ARM64 is the primary Gazebo simulation environment.

## 7. Documentation

Important project context is maintained in:

- `README.md`
- `docs/PROJECT_CONTEXT.md`
- `docs/DEVELOPMENT_STATUS.md`

When an implementation changes the project's architecture, workflow, or important development status, update the appropriate documentation.

Keep useful troubleshooting and historical development records instead of deleting them simply because the problem has been solved.

## 8. Teaching Style

The user is learning ROS 2 and autonomous robotics while implementing the project.

When explaining implementation decisions, include:

- What the code does
- Why it is needed
- Why the chosen approach fits this project
- Relevant alternatives and trade-offs

Prefer understandable, explainable implementations over unnecessary abstraction.

## 9. Safety for Repository Changes

Do not:

- delete project history without a reason
- replace working architecture unnecessarily
- overwrite unrelated files
- modify credentials, SSH keys, secrets, or `.env` files
- commit generated build/install/log directories

Before destructive or broad changes, ask for confirmation.

## 10. Current Development Direction

The intended development pipeline is:

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
