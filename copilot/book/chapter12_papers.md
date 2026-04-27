---
title: Key Papers and Reading List
author: GitHub Copilot (GPT-4.1)
date: 2026-04-27
prev_url: /copilot/book/chapter11_projects/
prev_title: "Appendix B: Robot Project Ideas"
---

# Appendix C: Key Papers and Reading List

## Introduction

This appendix collects papers that the course instructor identified as most valuable for understanding autonomous mobile robotics. They are grouped by topic and annotated with a brief note on why each is worth reading. Whether you are new to robotics or reinforcing your foundations, these references will deepen your understanding of the algorithms, architectures, and real-world challenges that define the field.

---

## Real-World Robotics

- **Murphy, "Human-Robot Interaction in Rescue Robotics" (2004)** — [IEEE Trans. Syst. Man Cybern.](https://www.aaai.org/Papers/Symposia/Spring/2007/SS-07-09/SS07-09-020.pdf). Essential reading on the gap between lab robotics and robots that must work in chaotic real-world conditions. Relevant to [Chapter 1: Defining Robots](chapter1_robots.md).

- **Martin, "Real Robots Don't Drive Straight" (2007)** — [AAAI Spring Symposium](https://www.aaai.org/Papers/Symposia/Spring/2007/SS-07-09/SS07-09-020.pdf). A frank and important look at the difference between an idealized robot model and real physical hardware behavior. Essential before writing any motion control code. Relevant to [Chapter 2: Robot Hardware](chapter2_robot_hardware.md).

---

## General Robotics

- **Niemueller & Widyadharma, "Artificial Intelligence – An Introduction to Robotics" (2003)** — [Semantic Scholar](https://www.semanticscholar.org/paper/Artificial-Intelligence-An-Introduction-to-Robotic-Niemüller-Widyadharma/1855fc75e7364cb7aeb28114bdac5cc6a00d0119). A concise and accessible overview of what robots are and the role of AI. Good starting point for [Chapter 1: Defining Robots](chapter1_robots.md).

---

## Navigation and SLAM

- **Riisgaard & Blas, "SLAM for Dummies: A Tutorial Approach to Simultaneous Localization and Mapping" (2004)** — [MIT DSpace](https://dspace.mit.edu/bitstream/handle/1721.1/36832/16-412JSpring2004/NR/rdonlyres/Aeronautics-and-Astronautics/16-412JSpring2004/A3C5517F-C092-4554-AA43-232DC74609B3/0/1Aslam_blas_report.pdf). The most accessible introduction to SLAM. Explains how LIDAR scans are used to build maps and localize the robot simultaneously. Relevant to [Chapter 5: Working with LIDAR](chapter5_lidar.md).

- **Fox, Burgard & Thrun, "The Dynamic Window Approach to Collision Avoidance"** — [UW CSE](http://www.cs.washington.edu/node/4749). The classic paper for converting LIDAR obstacle data into safe velocity commands. Foundation of local planners in Nav2. Relevant to [Chapter 5: Working with LIDAR](chapter5_lidar.md).

- **"Wall Following for Autonomous Navigation"** — [UPenn SUNFEST](https://sunfest.seas.upenn.edu/wp-content/uploads/2018/07/12-bayer.pdf). A concrete example of LIDAR-based reactive navigation, directly relevant to obstacle-avoidance exercises.

- **Montemerlo et al., "FastSLAM: A Factored Solution to the Simultaneous Localization and Mapping Problem"** — [Stanford AI](http://ai.stanford.edu/~koller/Papers/Montemerlo+al:AAAI02.pdf). Particle-filter-based SLAM — the algorithmic family behind many practical implementations.

- **Kavraki et al., "Probabilistic Roadmaps for Path Planning in High-Dimensional Configuration Spaces"** — [Kavraki Lab](http://www.kavrakilab.org/sites/default/files/kavraki1996prm-high-dim-conf.pdf). The PRM paper; foundational for sampling-based path planning.

- **LaValle, "Rapidly-Exploring Random Trees: A New Tool for Path Planning"** — [UIUC MSL](http://msl.cs.uiuc.edu/~lavalle/papers/Lav98c.pdf). The RRT paper; the other major branch of sampling-based planning.

---

## Robot Behavior and Control

- **Brooks, "A Robust Layered Control System for a Mobile Robot"** — [Semantic Scholar](https://www.semanticscholar.org/paper/A-robust-layered-control-system-for-a-mobile-robot-Brooks/dc66c15a005dd1a3a9f033769e7fbc3b943be188). The subsumption architecture paper. Showed that distributed, reactive behavior layers are more robust than centralized planning. Directly relevant to [Chapter 3: Robot Software Architecture](chapter3_software_arch.md).

- **Arkin, "Motor Schema-Based Mobile Robot Navigation"** — [Semantic Scholar](https://www.semanticscholar.org/paper/Motor-Schema-Based-Mobile-Robot-Navigation-Arkin/fc86aea4a0dedaa7525aeb68464722445eceab50). Influential behavior-based architecture for navigation; complements the subsumption approach.

- **De Silva & Ekanayake, "Behavior-Based Robotics and the Reactive Paradigm: A Survey" (2008)** — [Utah CS](http://www.cs.utah.edu/~alnds/papers/behavior_robotics_2008.pdf). Surveys the landscape of behavior-based approaches. Good background for the behavior-design chapters.

---

## Computer Vision and Fiducials

- **Olson, "AprilTag: A Robust and Flexible Visual Fiducial System" (2011)** — [EECS Michigan](https://april.eecs.umich.edu/pdfs/olson2011tags.pdf). The original AprilTag paper. Directly relevant to fiducial-based localization exercises in [Chapter 6: Computer Vision](chapter6_computer_vision.md).

- **Ross, "Fiducial Marker Navigation for Mobile Robots"** — [Rhodes CS](http://www.cs.ru.ac.za/research/g09r5654/downloads/shortpaper.pdf). Practical treatment of using fiducial markers for robot navigation.

- **Endres et al., "An Evaluation of the RGB-D SLAM System"** — [Uni Freiburg](http://www2.informatik.uni-freiburg.de/~endres/files/publications/endres12icra.pdf). Evaluation of visual + depth SLAM; relevant to depth camera work in [Chapter 6](chapter6_computer_vision.md).

---

## Artificial Intelligence in Robotics

- **Watson, Ficiei & Pollack, "Embodied Evolution: Embodying an Evolutionary Algorithm in a Population of Robots"** — [Brandeis](http://129.64.46.116/papers/ee_cec99.pdf). An example of evolutionary computation applied to robot learning.

- **Grabowski et al., "Heterogeneous Teams of Modular Robots for Mapping and Exploration"** — [Semantic Scholar](https://www.semanticscholar.org/paper/Heterogeneous-Teams-of-Modular-Robots-for-Mapping-Kuijpers/989585de3ebfa2806e43f7da0773769bfe923d85). Multi-robot systems for exploration; broadens the scope beyond single-robot navigation.

---

## Video and Online Resources

- **[Visualizing Quaternions](https://eater.net/quaternions)** and **[Quaternions (3Blue1Brown)](https://www.youtube.com/watch?v=d4EgbgTm0Bg)** — Essential for understanding 3D rotation representation, which underpins tf2 and robot pose estimation.
- **[Artificial Intelligence for Robotics (Udacity CS373)](https://classroom.udacity.com/courses/cs373)** — Sebastian Thrun's course; excellent introduction to SLAM and localization mathematics.
- **[ETH Zurich: Programming for Robots](https://www.youtube.com/watch?v=0BxVPCInS3M)** — Video introduction and review of ROS concepts.
- **[Podcast: Self-Driving Deep Learning (Software Engineering Daily)](http://traffic.libsyn.com/sedaily/SelfDrivingDeepLearning.mp3)** — Good background on deep learning applied to autonomous navigation.

---

*This appendix is based solely on classroom source materials and is designed for educational use.*

> **Disclaimer:** This content was generated from classroom source materials by an AI assistant. Errors may be present — please report any to [pitosalas@gmail.com](mailto:pitosalas@gmail.com).
