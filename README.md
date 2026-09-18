# ROS 2 Mobile Robot — SLAM & Autonomous Navigation

A ROS 2 Humble based differential-drive mobile robot simulated in Gazebo, featuring LiDAR-based SLAM, AMCL localization, and autonomous navigation using the Nav2 stack.

The project demonstrates a complete mobile robotics workflow:

**Simulation → SLAM Mapping → Map Saving → Localization → Path Planning → Autonomous Navigation**

---

## Project Demo

### Gazebo Simulation & SLAM Mapping

The robot is simulated inside a custom Cafe environment in Gazebo. A LiDAR sensor scans the environment while SLAM Toolbox is used to build a 2D occupancy grid map.

![Gazebo Simulation and SLAM Mapping](images/cafe_slam.png)

### Autonomous Navigation

After creating and saving the map, the robot uses AMCL for localization and Nav2 for autonomous navigation.

A destination can be selected in RViz using the `2D Goal Pose` tool. Nav2 then plans a path and commands the differential-drive robot to move autonomously toward the selected destination.

> A navigation demonstration video is included with the project.

---

# Features

- ROS 2 Humble based mobile robot
- Differential-drive robot
- Gazebo simulation
- Custom Cafe simulation environment
- LiDAR sensor
- Camera and depth camera support
- ROS 2 Control
- SLAM using SLAM Toolbox
- 2D occupancy grid map generation
- Map saving
- AMCL-based localization
- Autonomous navigation using Nav2
- RViz2 visualization
- Velocity command multiplexing
- URDF/Xacro robot description
- Configurable ROS 2 parameters using YAML

---

# System Workflow

```text
                         ┌──────────────────────┐
                         │   Gazebo Simulation  │
                         │     Cafe World      │
                         └──────────┬───────────┘
                                    │
                              LiDAR + TF
                                    │
                                    ▼
                         ┌──────────────────────┐
                         │    SLAM Toolbox      │
                         │       Mapping        │
                         └──────────┬───────────┘
                                    │
                               Saved Map
                                    │
                                    ▼
                         ┌──────────────────────┐
                         │        AMCL          │
                         │     Localization     │
                         └──────────┬───────────┘
                                    │
                         Robot Pose in Map
                                    │
                                    ▼
                         ┌──────────────────────┐
                         │        Nav2          │
                         │  Planning & Control  │
                         └──────────┬───────────┘
                                    │
                              Velocity Commands
                                    │
                                    ▼
                         ┌──────────────────────┐
                         │ Differential Drive   │
                         │     Controller       │
                         └──────────┬───────────┘
                                    │
                                    ▼
                                Robot Motion
