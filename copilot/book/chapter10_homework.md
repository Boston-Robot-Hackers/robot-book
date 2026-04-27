---
title: Homework Assignments
author: GitHub Copilot (GPT-4.1)
date: 2026-04-27
prev_url: /copilot/book/chapter9_behaviors/
prev_title: "Chapter 9: Robot Behaviors and State Machines"
---

# Appendix A: Homework Assignments

These assignments accompany the chapters of this book and are organized by topic area. They were developed for the COSI 119a Autonomous Robotics course at Brandeis University. Each assignment is designed to reinforce the concepts introduced in the corresponding chapter through hands-on practice — first in simulation, and then (where possible) on real hardware.

---

## Programming Assignments (PAs)

### PA: Basic Control

- **Chapter:** [Chapter 3: Robot Software Architecture](chapter3_software_arch.md) and [Chapter 2: Robot Hardware](chapter2_robot_hardware.md)
- **Purpose:** Introduces creating a basic ROS 2 program. Foundation of everything that follows.
- **Skills practiced:** Controlling motion with `cmd_vel`; publish/subscribe; sensing with LIDAR and odometry; algorithms and state management.
- **Tasks:**
  1. Drive the robot 1 meter out, do a 180° turn in place, and return to the start
  2. Drive the robot in an exact 1-meter square
  3. Drive the robot in a circle with a radius of 1 meter
  4. Demonstrate in simulation (Gazebo)
- **Deliverables:** Clean Python ROS 2 node; short video of demo plus code walkthrough

---

### PA: LIDAR Wall Follow

- **Chapter:** [Chapter 5: Working with LIDAR](chapter5_lidar.md)
- **Purpose:** Wall following is a classic early robotics problem. Brings together motion control and LIDAR sensing.
- **Skills practiced:** ROS 2 app structure; launch files; `cmd_vel` motion; `/scan` subscription; LIDAR data filtering and wedge analysis
- **Tasks:** Write a node that moves the robot along a wall maintaining a fixed distance. Handle basic starting conditions (parallel at correct distance, too far, too close) and more challenging ones (corners, arbitrary initial orientation).
- **Deliverables:** ROS 2 package with commented Python source, README with run instructions, short video

---

### PA: Maze Escape!

- **Chapter:** [Chapter 5: Working with LIDAR](chapter5_lidar.md)
- **Purpose:** Apply wall-following algorithms to solve a maze
- **Tasks:** Use wall-following and obstacle-avoidance logic to navigate out of a maze in simulation
- **Deliverables:** ROS 2 package, video

---

### PA: Line Follower

- **Chapter:** [Chapter 6: Computer Vision](chapter6_computer_vision.md)
- **Purpose:** Robot looks for a line on the floor and follows it using camera input
- **Skills:** Camera image subscription, color thresholding, contour detection with OpenCV, proportional steering control
- **Deliverables:** ROS 2 package, video

---

### PA: Fiducials

- **Chapter:** [Chapter 6: Computer Vision](chapter6_computer_vision.md)
- **Purpose:** Fiducial navigation using AprilTags for robot localization
- **Skills:** AprilTag detection, fiducial SLAM, coordinate frame reasoning with tf2
- **Deliverables:** ROS 2 package, video

---

## Lab Assignments

### Lab 1: Check Environments and Tutorials

- **Chapter:** [Introduction](chapter00_intro.md)
- Set up ROS 2 environment; complete ROS 2 beginner tutorials; verify simulation tools (Gazebo, RViz2)

### Lab 2: Practice Topics, Messages, Services and Actions

- **Chapter:** [Chapter 3: Robot Software Architecture](chapter3_software_arch.md)
- Practice ROS 2 publish/subscribe, services, and actions in simulation

### Lab 3: Work with Real Robots

- **Chapter:** [Chapter 2: Robot Hardware](chapter2_robot_hardware.md)
- Follow lab safety rules; drive TurtleBot3 using teleop; observe real hardware behavior

### Lab 4: Teleop Bot — PID Control

- **Chapter:** [Chapter 3: Robot Software Architecture](chapter3_software_arch.md)
- Implement teleop-style node; introduction to PID control for smooth motion

### Lab 6: Radians, Multiple Robots, and Custom Messages

- **Chapter:** [Chapter 3: Robot Software Architecture](chapter3_software_arch.md)
- Work with angular measurements in radians; create and publish custom ROS 2 message types; coordinate multiple robots

### Lab 8: Mini-PA: Filter Scan

- **Chapter:** [Chapter 5: Working with LIDAR](chapter5_lidar.md)
- Subscribe to `/scan`; apply noise filtering; republish cleaned scan data

### Lab 9: Mini-PA: Robo Chaser

- **Chapter:** [Chapter 5: Working with LIDAR](chapter5_lidar.md)
- Use LIDAR distance data to detect and follow a target robot

### Lab 10: Mini-PA: URDF

- **Chapter:** [Chapter 2: Robot Hardware](chapter2_robot_hardware.md)
- Create and test a URDF description for the project robot

---

## Longer-Term Assignments

### HW: Hello Robot!

- **Chapter:** [Introduction](chapter00_intro.md)
- First running program: get a node running on the robot (real or simulated) and demonstrate basic control

### HW: TF2 Tutorial Extension

- **Chapter:** [Chapter 3: Robot Software Architecture](chapter3_software_arch.md)
- Read and implement examples from the [ROS 2 tf2 Tutorials](https://docs.ros.org/en/rolling/Tutorials/Intermediate/Tf2/Introduction-To-Tf2.html); answer written questions about the TF tree and how transforms work

### HW: Dependency on Initial Conditions

- **Chapter:** [Chapter 3: Robot Software Architecture](chapter3_software_arch.md)
- Launch the robot from a non-default starting pose; diagnose and explain whether your basic_mover algorithm depends on initial conditions; fix any bugs found

### HW: Double Follow PA

- **Chapter:** [Chapter 5: Working with LIDAR](chapter5_lidar.md)
- Practice with TF2 transforms; implement a node where one robot follows another using coordinate frame reasoning

---

## Project Assignments

### Team Project Proposal

Submit a brief written proposal for your semester project describing: what the robot will do, what sensing and actuation it will use, what ROS 2 nodes you plan to write, and how you will evaluate success.

### Weekly Standups

Each week, share a brief (2–3 minute) update with the class: what your team accomplished, what is blocked, and what you plan for the next sprint.

### Hello Robot! (Project Milestone)

Demonstrate the first running program on your project robot — any behavior that proves the software stack is up and running.

### Project Major Milestone

Prepare a demo and brief presentation for a checkpoint meeting with the instructor. Show working code and describe what remains.

---

*This appendix is based solely on classroom source materials and is designed for educational use.*

> **Disclaimer:** This content was generated from classroom source materials by an AI assistant. Errors may be present — please report any to [pitosalas@gmail.com](mailto:pitosalas@gmail.com).
