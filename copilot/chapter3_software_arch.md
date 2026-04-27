---
title: Robot Software Architecture
author: GPT-4.1
date: 2026-04-26
prev_url: /copilot/chapter2_robot_hardware/
prev_title: "Chapter 2: Robot Hardware"
next_url: /copilot/chapter4_sensors_overview/
next_title: "Chapter 4: Sensors Overview"
---


# Chapter 3: Robot Software Architecture

## 3.1 Why Robots Need Special Software

Robots are not just computers on wheels—they are complex, tightly integrated systems that must sense, plan, and act in the real world. Unlike traditional software, which runs in predictable digital environments, robot software must constantly interact with unpredictable physical realities. This means:

- Integrating hardware (motors, sensors, controllers) with software logic
- Reacting in real time to sensor input and environmental changes
- Handling uncertainty, noise, and incomplete information
- Supporting autonomy, safety, and robust error handling

For example, a robot vacuum must detect obstacles, plan a path, and control its motors—all while responding instantly to a pet darting across its path. These requirements demand software architectures that are modular, responsive, and resilient.

Robots also face unique challenges: sensors can fail or provide noisy data, actuators may not behave as expected, and the environment can change without warning. Good robot software anticipates these issues, using feedback loops, error detection, and redundancy to maintain reliable operation.

## 3.2 Distributed Systems in Robotics

Modern robots are, by necessity, distributed systems. Rather than a single computer running all code, robots typically use multiple processors and microcontrollers, each responsible for different subsystems. For example:

- A Raspberry Pi or laptop might run high-level planning and perception
- An Arduino or OpenCR board handles low-level motor control and sensor interfacing
- Sensors and actuators may have their own embedded processors

These components communicate over wired or wireless networks, exchanging data and commands. This distributed approach offers several advantages:

- **Modularity:** Each subsystem can be developed, tested, and replaced independently
- **Scalability:** More sensors or actuators can be added without redesigning the whole system
- **Fault tolerance:** If one part fails, others can continue operating or compensate

However, distributed systems also introduce complexity. Communication delays, synchronization issues, and network failures must be managed. Robot software frameworks, like ROS, are designed to address these challenges.

## 3.3 ROS Motivation and Architecture

The Robot Operating System (ROS) is the most widely used framework for robot software development. ROS was created to solve the unique challenges of robotics:

- **Nodes:** Each functional component (e.g., sensor driver, controller, planner) runs as a separate process, called a node. This separation improves reliability and makes it easier to develop and debug complex systems. See the [ROS 2 Nodes documentation](https://docs.ros.org/en/rolling/Concepts/Basic/About-Nodes.html).
- **Topics:** Nodes communicate by publishing and subscribing to topics. For example, a LIDAR node publishes sensor data on a `/scan` topic (see [Chapter 5: Working with LIDAR](chapter5_lidar.md)), while a mapping node subscribes to that topic to build a map. See the [ROS 2 Topics documentation](https://docs.ros.org/en/rolling/Concepts/Basic/About-Topics.html).
- **Services:** For request/response interactions, nodes can offer services. For example, a node might provide a service to reset the robot's position or query its battery level. See [ROS 2 Services documentation](https://docs.ros.org/en/rolling/Concepts/Basic/About-Services.html).
- **Actions:** Some tasks, like navigation, take time and require feedback. ROS actions support long-running goals with progress updates and the ability to cancel or preempt tasks. See [ROS 2 Actions documentation](https://docs.ros.org/en/rolling/Concepts/Basic/About-Actions.html).

ROS abstracts away hardware details, allowing developers to focus on high-level logic. It also provides powerful tools for simulation (Gazebo), visualization (RViz), and debugging. The modularity of ROS means that code can be reused across different robots and projects, accelerating development and fostering collaboration.

## 3.4 Example Architectures

To make these concepts concrete, let's look at two example architectures:

### Simple Robot Software Stack

Imagine a basic mobile robot equipped with a [LIDAR](chapter5_lidar.md) and a [camera](chapter6_computer_vision.md). Its software might be organized as follows:

- **Sensor nodes** publish data from the LIDAR and camera
- **Control nodes** subscribe to sensor data and send commands to the motors
- **State estimation and planning nodes** use sensor data to estimate the robot's position and plan paths

This modular approach allows each part of the system to be developed and tested independently. If you want to swap out the camera for a different model, you only need to update the camera node.

### TurtleBot3 Software Architecture

The TurtleBot3 is a popular educational and research robot. Its architecture illustrates the distributed, modular nature of modern robotics:

- The Raspberry Pi runs the ROS core and high-level nodes for navigation, mapping, and user interaction.
- The OpenCR board handles low-level motor control, reading wheel encoders, and processing IMU data.
- LIDAR and camera nodes publish sensor data to the ROS network.
- All nodes communicate over ROS topics and services, allowing for flexible integration and easy debugging.

The diagram below summarizes this architecture:

```mermaid
graph TD
    A[ROS Core] --> B[Sensor Nodes]
    A --> C[Control Nodes]
    A --> D[Planning Nodes]
    B --> E[Lidar]
    B --> F[Camera]
    C --> G[Motor Controller]
    D --> H[Navigation]
```

This architecture allows the TurtleBot3 to perform complex tasks like simultaneous localization and mapping (SLAM), obstacle avoidance, and autonomous navigation—all using modular, reusable software components.

## 3.5 Further Reading

To deepen your understanding of robot software architecture and ROS, explore these resources:

- [ROS 2 Documentation](https://docs.ros.org/en/rolling/)
- [TurtleBot3 Software Architecture](https://emanual.robotis.com/docs/en/platform/turtlebot3/overview/)

### Relevant Papers
- Martin, ["Real Robots Don't Drive Straight" (2007)](https://www.aaai.org/Papers/Symposia/Spring/2007/SS-07-09/SS07-09-020.pdf) — a frank look at the gap between idealized robot models and real physical behavior; essential reading before writing any motion control code.
- Arkin, ["Motor Schema-Based Mobile Robot Navigation"](https://www.semanticscholar.org/paper/Motor-Schema-Based-Mobile-Robot-Navigation-Arkin/fc86aea4a0dedaa7525aeb68464722445eceab50) — influential work on behaviour-based architectures for navigation.
- Brooks, ["A Robust Layered Control System for a Mobile Robot"](https://www.semanticscholar.org/paper/A-robust-layered-control-system-for-a-mobile-robot-Brooks/dc66c15a005dd1a3a9f033769e7fbc3b943be188) — the subsumption architecture paper that inspired distributed, reactive robot software design.

---

*This chapter is based solely on classroom source materials and is designed for educational use.*

> **Disclaimer:** This content was generated from classroom source materials by an AI assistant. Errors may be present — please report any to [pitosalas@gmail.com](mailto:pitosalas@gmail.com).
