---
title: Robot Project Ideas
author: GitHub Copilot (GPT-4.1)
date: 2026-04-27
prev_url: /copilot/book/chapter10_homework/
prev_title: "Appendix A: Homework Assignments"
---

# Appendix B: Robot Project Ideas

## What Makes a Good Project

A strong semester project demonstrates a complete, working robot behavior — not just a component or a simulation. The best projects integrate all three pillars of autonomous robotics: **sensing** (reading the environment through cameras, LIDAR, or other inputs), **decision-making** (interpreting that data and choosing actions), and **actuation** (moving the robot or triggering outputs in the physical world). Projects are assessed on three dimensions: the **degree of challenge** relative to the team's starting point, the **quality of execution** (does it actually work reliably?), and **professional presentation** — clean code, clear documentation, and a compelling demo that communicates what was built and why it matters.

---

## Final Project Deliverables

A complete project submission for COSI 119a consists of five parts:

1. **Live demo** during finals week (5–10 minutes, using real hardware). The robot must perform its core behavior in front of the class. Judges evaluate robustness, not just best-case performance.
2. **GitHub repository** moved to the [campusrover](https://github.com/campusrover) organization — clean, well-documented, and portfolio-ready. README must explain how to install, configure, and run the project from scratch.
3. **Lab Notebook FAQ entry** — each teammate individually submits one FAQ entry to the [Lab Notebook](https://campusrover.github.io/labnotebook2/) documenting something they learned or debugged during the project.
4. **Project report** (~10 pages, written in Markdown and added to the Lab Notebook) covering:
   - Problem statement and motivation
   - Technical description of what was built
   - Interesting algorithms or design decisions
   - How to use the code
   - Project story: what worked, what didn't, what you would do differently
5. **Video** (4–5 minutes): a narrated code tour plus real demo footage, with all teammates contributing narration.

---

## Project Ideas by Category

The following ideas have been used or proposed in past semesters of COSI 119a. They are starting points — teams are encouraged to adapt the scope to match their interest and available time.

### Navigation and Mapping

- **Autonomous Campus Rover:** Navigate the building autonomously, reading door numbers visually, and delivering messages between offices. Combines LIDAR-based navigation ([Chapter 5](chapter5_lidar.md)), computer vision ([Chapter 6](chapter6_computer_vision.md)), and behavior coordination across multiple tasks.
- **Maze Solver with SLAM:** Build a map of an unknown maze using SLAM, then navigate to the exit using the constructed map. This extends the Maze Escape programming assignment with full localization rather than purely reactive behavior.
- **Multi-Floor Navigation:** Plan routes that include elevator or ramp navigation, requiring the robot to reason about vertical space beyond the flat 2D assumptions of standard SLAM.

### Computer Vision Applications

- **Face Recognition Greeter:** Recognize faces of registered team members and greet each person by name when they approach. Uses a forward-facing camera and a face-recognition library integrated with ROS 2 topics.
- **Gesture-Controlled Robot:** Recognize hand signals — stop, go, turn left, turn right — and translate them into robot velocity commands. This is a form of visual teleoperation that eliminates the need for a physical controller.
- **Line-Following Maze Solver:** Use computer vision to follow a line painted or taped on the floor, then use CV to distinguish a solid wall from an opening at each junction.
- **Door Number Reader:** Mount a camera on the robot and use OCR to identify office rooms by their posted door number plaques, enabling destination-by-name navigation.

### Fiducials and Localization

- **Fiducial SLAM:** Place AprilTag markers around the environment as known landmarks. Localize the robot relative to those markers and navigate between tagged waypoints without building a traditional LIDAR occupancy map.
- **Treasure Hunt:** Attach fiducials to a set of objects hidden around the space. The robot must search for, detect, and approach each one in sequence, logging each find.

### Interaction and Social Robotics

- **Delivery Robot:** Accept a destination specified verbally or via a simple web UI, navigate autonomously to that location, and announce arrival — either through a speaker or an on-screen message.
- **Security Guard Robot:** Patrol a defined perimeter on a timed schedule, detect people appearing unexpectedly in restricted zones, and raise a configurable alarm (sound, LED, ROS topic).
- **Robot Dance Performance:** Choreograph a sequence of motions synchronized to music, demonstrating precise timing, smooth velocity profiles, and coordinated actuation — a showcase of motion control fundamentals.

### Sensing and Hardware Experiments

- **Depth Camera Integration:** Interface an RGB-D camera (such as the Intel RealSense or Microsoft Kinect) and use the resulting 3D point cloud for richer obstacle avoidance or simple object pick-and-place.
- **URDF Custom Robot:** Design a custom robot description in URDF, simulate it in Gazebo, write ROS 2 nodes to control it, and demonstrate a working behavior — entirely in simulation.
- **Race Track Challenge:** Drive the robot as fast as possible around a defined track without touching the walls, using LIDAR distance feedback to maintain safe clearance at speed.

---

## Semester Project Workflow

Projects run for approximately the last third of the semester, giving teams of 2–3 students roughly five weeks from proposal to final demo. The workflow follows an iterative cycle: teams first submit a one-page **proposal** describing the goal, the sensing and actuation approach, and a stretch goal. Instructors provide feedback and approve a scope. Teams then develop in weekly sprints, attending **weekly standup check-ins** where they share current status, blockers, and the next week's plan. A **milestone demo** at the midpoint of the project period — typically a simplified version of the core behavior — serves as an early integration test and a chance to recalibrate scope before the final week.

---

## Tips from Past Projects

The most successful projects start simple and expand deliberately. Get one behavior working end-to-end on real hardware before layering on additional features — a robot that reliably does one thing is far more impressive than one that attempts three things and fails at all of them. Use simulation heavily during early development to iterate quickly on logic, and save real hardware time for integration testing, where unexpected sensor noise and physical reality will surface the bugs that simulation masked. Document as you go: keep a running notes file, screenshot interesting ROS graphs, and record short videos of intermediate milestones. The final report is dramatically easier to write when you have a record of the journey rather than trying to reconstruct it from memory in the last 48 hours.

---

*This appendix is based solely on classroom source materials and is designed for educational use.*

> **Disclaimer:** This content was generated from classroom source materials by an AI assistant. Errors may be present — please report any to [pitosalas@gmail.com](mailto:pitosalas@gmail.com).
