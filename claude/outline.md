---
title: "Introduction to Robotics — Book Outline"
date: 2026-04-26
author: Claude Sonnet 4.6
---

# Introduction to Robotics — Proposed Outline

## Part 1: What Is a Robot?

- **Ch 1: Defining Robots** — characteristics, history, what makes something a robot
- **Ch 2: Robot Hardware** — locomotion (wheels, treads, legs), actuators, computing platforms (TurtleBot3)
- **Ch 3: Robot Software Architecture** — why robots need special software, distributed systems, ROS motivation

## Part 2: Perceiving the World

- **Ch 4: Sensors Overview** — LIDAR, cameras, depth sensors, odometry, IMU, touch, GPS
- **Ch 5: Working with LIDAR** — scan data, filtering noise, obstacle detection
- **Ch 6: Computer Vision** — cameras, OpenCV, line detection, fiducial markers

## Part 3: ROS — The Robot Operating System

- **Ch 7: ROS Introduction** — distributed process management, nodes, the computation graph
- **Ch 8: Topics and Messages** — publish/subscribe, queues, latched topics, custom messages
- **Ch 9: Services** — synchronous client/server communication
- **Ch 10: Actions** — long-running tasks with feedback
- **Ch 11: ROS 2 Development** — workspaces, packages, colcon build, ament_python, best practices

## Part 4: Motion and Control

- **Ch 12: Coordinate Frames and Transforms** — local/global frames, quaternions, TF2
- **Ch 13: Locomotion and Movement** — kinematics, Twist messages, differential drive
- **Ch 14: PID Control** — proportional/integral/derivative, tuning, avoiding oscillation
- **Ch 15: Robot Bodies** — joints, links, URDF, kinematic chains, manipulators

## Part 5: Knowing Where You Are

- **Ch 16: Localization Fundamentals** — odometry, dead reckoning, uncertainty
- **Ch 17: Maps and SLAM** — occupancy grids, building maps, simultaneous localization and mapping
- **Ch 18: AMCL and Particle Filters** — probabilistic localization, Monte Carlo methods
- **Ch 19: Kalman Filters** — estimating state under uncertainty

## Part 6: Navigation

- **Ch 20: Path Planning** — global planners, obstacle avoidance, search algorithms
- **Ch 21: The Navigation Stack** — Nav2, global/local planners, costmaps
- **Ch 22: Practical Navigation** — point to point, waypoints, indoor vs outdoor

## Part 7: Behavior and Intelligence

- **Ch 23: How Robots Decide What To Do** — event-based architectures, reactive systems
- **Ch 24: Finite State Machines** — modeling behavior, transitions, ROS implementation
- **Ch 25: Behavior Trees** — tick-based execution, composites, leaves
- **Ch 26: Complex Robot Systems** — managing complexity, testing, design patterns

## Part 8: Human-Robot Interaction

- **Ch 27: Robots Around People** — social conventions, safety, awareness
- **Ch 28: Voice and Interface Control** — Alexa integration example

## Homework Assignments

- **HW 1:** ROS basics — nodes, topics, first publisher/subscriber
- **HW 2:** Sensor data — reading and interpreting LIDAR scans
- **HW 3:** Motion control — move robot with Twist messages, implement PID
- **HW 4:** Coordinate transforms — TF2 frames, transforming between coordinate systems
- **HW 5:** Mapping — build a map with SLAM, save and load it
- **HW 6:** Localization — run AMCL, localize robot on saved map
- **HW 7:** Navigation — use Nav2 to navigate autonomously to waypoints
- **HW 8:** Behavior — implement finite state machine for a multi-step task
- **HW 9:** Computer vision — detect line or fiducial marker, steer robot toward it

## Robot Project Ideas

- **Wall Follower** — robot maintains fixed distance from wall using LIDAR
- **Maze Escape** — robot navigates out of maze without prior map
- **Line Follower** — robot follows painted or projected line using camera
- **Fiducial Navigation** — robot navigates to goals identified by AR markers
- **Follow Bot** — robot follows a moving target (person or object)
- **Campus Rover** — autonomous delivery robot for outdoor campus navigation
- **Indoor Waypoint Navigator** — visits sequence of indoor locations autonomously
- **Outdoor Waypoint Navigator** — GPS or visual waypoint following outdoors
- **Robot Arm** — pick-and-place task using manipulator with inverse kinematics
- **Multi-Robot Coordination** — two robots cooperate on shared task
- **Balance Bot** — self-balancing robot using IMU feedback

## Appendices

- A: Key Papers in Robotics
- B: Simulation Setup (Gazebo / STDR)
- C: TurtleBot3 Setup Guide

---

*Note: robotics_logistics/ content (course admin, policies) and guest speaker content excluded.*
