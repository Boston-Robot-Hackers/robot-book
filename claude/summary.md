---
title: "Source Material Summary"
date: 2026-04-26
author: Claude Sonnet 4.6
---

# Source Material Summary

## cosi119r — COSI 119a Autonomous Robotics Course (Brandeis)

~54 content files. Nanoc static site. Lectures in 3 parts (~28 total), plus labs, homeworks, background.

**Part 1** (8 lectures): ROS basics, coordinates, perception, sensors, movement, best practices  
**Part 2** (12 lectures): Hardware, TF2, localization, AMCL, computer vision, navigation, planning, fiducials  
**Part 3** (8 lectures): FSMs, behavior control, Kalman filters, projects, guest speakers

Content references cg-topics via `:topic_include` / `:topic_link` directives.

---

## cg-topics/robotics — Reusable Topic Library

127 files across 11 subdirectories.

| Directory | Files | Content |
|---|---|---|
| `ros_book/` | 18 | PRR book chapter notes — ROS fundamentals through navigation |
| `robotics_notes/` | 32 | Deep technical notes on robotics concepts |
| `robotics_bigideas/` | 11 | Conceptual frameworks: perception, control, localization, planning |
| `robotics_projects/` | 15 | Project specs: wall-follow, fiducials, arm, multi-robot, balance |
| `robotics_labs/` | 8 | Lab exercises 1–10 |
| `robotics_pas_2/` | 5 | Active programming assignments |
| `robotics_logistics/` | 21 | Course admin, setup, policies |
| `robotics_inactive_pas/` | 8 | Archived assignments |
| `robotics_handson/` | 2 | Hands-on intros (RViz, topics) |
| `mbot/` | 6 | mBot/Arduino platform content |

---

## Core Topics Covered

- ROS architecture: nodes, topics, services, actions, parameters
- TF2 coordinate transforms
- Sensing: LIDAR, cameras, odometry, IMU, depth sensors
- Motion control, PID algorithms
- Gazebo simulation
- SLAM, AMCL localization, mapping
- Path planning, move_base navigation stack
- Computer vision, line detection, fiducial markers
- Kalman filters
- Finite state machines, behavior architectures

## Scale Assessment

Enough material for a full semester course → substantial book. Significant overlap and redundancy to cull. Strong nucleus around ROS + navigation stack. `robotics_logistics/` content (admin, setup) likely not book material.
