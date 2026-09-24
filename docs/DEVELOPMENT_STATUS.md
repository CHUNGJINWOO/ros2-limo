# LIMO Development Status

Last updated:
2026-09-24

## 1. Overall Status

Current phase:

ROS 2 / LIMO base environment and project structure preparation

The repository currently provides the basic LIMO ROS 2 software,
simulation resources, and development infrastructure.

Project-level autonomous driving functions are not yet fully implemented.

---

## 2. Completed

### Repository / Infrastructure

- [x] LIMO ROS 2 repository established
- [x] GitHub repository connected
- [x] Project documentation structure established
- [x] `AGENTS.md` added
- [x] `docs/PROJECT_CONTEXT.md` added
- [x] Oracle Cloud remote development environment available
- [x] VS Code Remote SSH access to Oracle Cloud confirmed

### Existing LIMO Software

- [x] LIMO base driver package
- [x] Serial communication structure
- [x] Velocity command handling
- [x] Odometry-related publishing
- [x] IMU-related publishing structure
- [x] LIMO status message
- [x] TF-related processing
- [x] Ackermann robot model
- [x] Gazebo simulation resources
- [x] URDF / Xacro resources
- [x] RViz configuration
- [x] Basic remote velocity command experiment

---

## 3. Project-Specific Autonomous Driving Status

### LiDAR

Status:
Partially prepared

Current state:

- LIMO repository contains LiDAR/YDLIDAR-related launch resources.
- External LiDAR driver dependencies are referenced.
- Project-specific LiDAR obstacle detection is not yet implemented.

Next:

- Verify `/scan`
- Confirm `sensor_msgs/msg/LaserScan`
- Implement basic LiDAR obstacle detection
- Compare implementation with professor-provided LIMO textbook

---

### SLAM

Status:
Not implemented

Target:

- SLAM Toolbox
- Indoor map creation
- TF validation
- Map saving

---

### Localization

Status:
Not implemented

Target:

- AMCL
- map / odom / base_link TF relationship
- localization parameter tuning

---

### Navigation2

Status:
Not implemented

Target:

- Nav2 installation/configuration
- costmap configuration
- global planner
- local controller
- goal navigation

---

### Obstacle Avoidance

Status:
Not implemented

Target:

- static obstacle handling
- dynamic obstacle handling
- emergency stop
- local path adjustment
- safe recovery behavior

---

### Autonomous Patrol

Status:
Not implemented

Target:

- waypoint-based patrol
- repeated patrol route
- obstacle-aware patrol
- patrol state transitions

---

### Guidance

Status:
Not implemented

Target:

- destination selection
- navigation to destination
- integration with patrol mode
- user guidance behavior

---

## 4. Existing Experimental Work

A separate ROS workspace is used for development experiments.

ROS workspace:

`~/ros2_ws`

Current experimental package:

`~/ros2_ws/src/limo_capstone`

Current experimental functionality:

- `limo_e_stop.py`
- professor textbook-based LiDAR emergency-stop example
- `/scan` subscription
- `/e_stop` publisher

Build status:

`colcon build` succeeded for the experimental package.

The experimental package is currently separate from the main
`ros2-limo` repository structure.

Before integrating it into the repository,
the implementation should be rechecked against the current project architecture.

---

## 5. Current Development Environment

### Primary Simulation Environment

- Windows
- WSL2
- Ubuntu 22.04.5
- x86_64
- ROS 2 Humble

Primary ROS workspace:

`~/ros2_ws`

### Remote Development Environment

- Oracle Cloud
- Ubuntu 22.04.5
- ARM64 / aarch64
- ROS 2 Humble
- VS Code Remote SSH

Current repository path on Oracle Cloud:

`~/school/2026-2/ros2-limo`

---

## 6. Known Environment Considerations

### Oracle Cloud ARM64

Oracle Cloud is not the primary Gazebo simulation environment.

Use it primarily for:

- remote development
- project file access
- storage / backup
- infrastructure
- AI-Hub services
- data processing

Use local WSL2 x86_64 as the primary environment for
Gazebo-based simulation and autonomous-driving experiments.

### ROS Network Configuration

The project contains cloud/local ROS networking configuration.

Important variables may include:

- `ROS_DOMAIN_ID`
- `ROS_LOCALHOST_ONLY`
- `RMW_IMPLEMENTATION`
- `ROS_IP`
- `FASTRTPS_DEFAULT_PROFILES_FILE`

Do not assume cloud/local networking modes are interchangeable.

For single-machine local tests, use a consistent ROS 2 environment.

---

## 7. Current Known Issues / Items to Verify

- Verify the exact LIMO Gazebo launch procedure in the current repository.
- Verify all external LiDAR dependencies used by current launch files.
- Verify whether upstream launch files reference packages that are not present in the current repository.
- Establish a clean local WSL2 simulation environment.
- Install/configure Nav2.
- Install/configure SLAM Toolbox.
- Verify `/scan` in simulation.
- Verify TF tree.
- Establish the first complete LiDAR → SLAM → localization → Nav2 pipeline.

---

## 8. Next Development Steps

Recommended order:

1. Verify local ROS 2 / LIMO simulation
2. Verify LiDAR `/scan`
3. Implement basic obstacle detection
4. Install and verify SLAM Toolbox
5. Create and save an indoor map
6. Configure localization
7. Install and configure Nav2
8. Verify basic goal navigation
9. Implement obstacle avoidance
10. Test dynamic obstacle scenarios
11. Implement autonomous patrol
12. Integrate guidance behavior
13. Test on the real LIMO
14. Tune parameters on the real robot

---

## 9. Development Record Rule

Update this file when a major project state changes.

Examples:

- feature implemented
- package added
- simulation verified
- parameter tuning completed
- major bug discovered
- major bug resolved
- architecture changed

Do not rewrite historical records unnecessarily.

When possible, record:

- date
- change
- reason
- result
- next action
