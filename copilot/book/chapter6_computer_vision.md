---
title: Computer Vision
author: GPT-4.1
date: 2026-04-26
prev_url: /copilot/book/chapter5_lidar/
prev_title: "Chapter 5: Working with LIDAR"
next_url: /copilot/book/chapter7_localization_mapping/
next_title: "Chapter 7: Localization and Mapping"
---


# Chapter 6: Computer Vision

## Introduction

Computer vision enables robots to interpret and understand visual information from the world. It is a cornerstone of modern robotics, supporting navigation, object recognition, tracking, and interaction. By processing images and video streams, robots can make sense of their environment, recognize objects and people, follow lines, and even read signs or gestures.

### Why Computer Vision?
Robots operate in complex, dynamic environments. Cameras provide rich, high-bandwidth data that, when processed with the right algorithms, allow robots to navigate through hallways and rooms, recognize and track objects or people, follow lines or paths on the ground, read signs, numbers, or QR codes, and understand gestures and facial expressions.

Computer vision appears across virtually every robotics domain. Autonomous vehicles rely on it for lane detection and obstacle avoidance; service robots use it for object pickup and face recognition; and industrial robots depend on it for quality inspection and sorting tasks.

## Cameras and Image Acquisition

Robots use a variety of cameras and sensors to acquire visual data. Standard webcams provide RGB images and are well-suited for basic vision tasks. Depth cameras — such as the Intel RealSense or Microsoft Kinect — go further by capturing both color and depth information (RGB-D), enabling the robot to perceive 3D structure in its environment. Stereo cameras achieve a similar effect by using two lenses separated by a known baseline, estimating depth through triangulation much as human binocular vision does.

Image data is typically represented as a matrix of pixel values (for color: RGB). Depth cameras add a parallel matrix of distance values. This data is processed in real time for feedback and control.

**Example:**
> "Interface the depth camera to Alien and use it for something" (Project idea)

## OpenCV and Image Processing

[OpenCV](https://opencv.org/) is the most widely used open-source library for computer vision. It provides image filtering operations such as blurring and sharpening, edge detection via algorithms like Canny and Sobel, color space conversion between RGB, HSV, and grayscale, feature detection for corners, blobs, and contours, and real-time object tracking — all within a consistent, well-documented API.

**Sample Python code for reading and displaying an image:**
```python
import cv2
img = cv2.imread('image.jpg')
cv2.imshow('Image', img)
cv2.waitKey(0)
cv2.destroyAllWindows()
```

**Sample code for real-time camera feed:**
```python
import cv2
cap = cv2.VideoCapture(0)
while True:
	ret, frame = cap.read()
	cv2.imshow('Camera', frame)
	if cv2.waitKey(1) & 0xFF == ord('q'):
		break
cap.release()
cv2.destroyAllWindows()
```

**Hands-On:**
Try using OpenCV to filter an image, detect edges, or find contours. Use ROS 2 topics to publish and subscribe to camera images — see the [ROS 2 image_transport documentation](https://docs.ros.org/en/rolling/p/image_transport/) for details. To bridge between ROS 2 image messages and OpenCV arrays, use [cv_bridge](https://docs.ros.org/en/rolling/p/cv_bridge/). If your camera introduces lens distortion, the [ROS 2 camera_calibration package](https://docs.ros.org/en/rolling/p/camera_calibration/) can help you correct it.

## Line Detection

Line detection is a classic robotics problem, especially for line-following robots. The goal is to identify and follow lines or paths on the ground using a camera.

**Algorithms:**
The three most common approaches are color thresholding (isolating the color of the line, for example black on white), edge detection (finding the sharp boundaries on either side of the line), and the Hough Transform (detecting mathematically straight lines across the full image).

**Example:**
Detecting and following lines on the floor for navigation.

**Project:**
- "Create a Maze solver that uses Computer Vision. First use CV to follow a wall, then to tell the difference between a wall and an opening."

## Fiducial Markers

Fiducials are special patterns (such as AprilTags or QR codes) placed in the environment to help robots localize themselves. They are easy for computer vision algorithms to detect and uniquely identify.

**Applications:**
Fiducials are commonly used for robot localization and mapping, for identifying specific objects or locations in the environment, and for teaching a robot to reliably recognize particular places or items it will need to interact with.

**Fiducial SLAM:**
Instead of using [LIDAR](chapter5_lidar.md) or video alone, Fiducial SLAM uses the positions of fiducials to define a coordinate space. The robot can locate itself and other objects relative to these markers, even if it cannot build a traditional map of walls.

**Project:**
- "Demonstrate understanding of Fiducials by implementing fiducial SLAM."

**Further Reading:**
- [AprilTag](https://april.eecs.umich.edu/software/apriltag.html)

## Face and Gesture Recognition

Robots can use computer vision to recognize faces and gestures, enabling more natural human-robot interaction.

**Face Recognition:**
A robot equipped with face recognition can detect and identify people using its camera, opening up applications such as personalised greetings, security screening, and team-member interaction.

**Gesture Recognition:**
Gesture recognition allows the robot to interpret hand signals or body movements, which is useful for visual teleoperation and for providing an intuitive, controller-free way for humans to direct robot behaviour.

**Project Ideas:**
- "Design and implement some form of Face Recognition."
- "Recognize gestures visually."

## Depth Perception and 3D Vision

Depth cameras and stereo vision allow robots to perceive the world in three dimensions. This is essential for tasks like obstacle avoidance, object manipulation, and navigation in complex environments. For a broader overview of depth sensing and how it compares to other sensors, see [Chapter 4: Sensors Overview](chapter4_sensors_overview.md#44-depth-sensors).

**Project:**
- "Interface the depth camera to Alien and use it for something."

## Computer Vision in Campus Rover

The Campus Rover project integrates many of these concepts: it recognises the faces of team members and greets them by name, reads door numbers visually to identify office locations, interprets hand gestures for visual teleoperation, and uses fiducials for both localisation and floor detection.

## Hands-On Labs and Projects

Explore these project ideas to deepen your understanding of computer vision in robotics:
- Maze solver using computer vision
- Face recognition for personalized interaction
- Gesture recognition for robot control
- Depth camera integration
- Fiducial SLAM for localization

## Assignments

The following assignments relate to computer vision topics in this chapter:

- **PA: Line Follower** — Robot looks for a line on the floor and follows it using camera input
- **PA: Fiducials** — Fiducial navigation programming assignment using AprilTags

## Further Reading and Resources

- [OpenCV](https://opencv.org/)
- [AprilTag](https://april.eecs.umich.edu/software/apriltag.html)
- [cv_bridge — ROS 2 to OpenCV image conversion](https://docs.ros.org/en/rolling/p/cv_bridge/)
- [image_transport — efficient ROS 2 image streaming](https://docs.ros.org/en/rolling/p/image_transport/)
- [camera_calibration — ROS 2 lens calibration](https://docs.ros.org/en/rolling/p/camera_calibration/)
- [vision_opencv (ROS 2)](https://github.com/ros-perception/vision_opencv/tree/ros2)
- [RealSense First Impressions](https://msadowski.github.io/Realsense-T265-First-Impressions/)

### Relevant Papers
- Olson, ["AprilTag: A robust and flexible visual fiducial system" (2011)](https://april.eecs.umich.edu/pdfs/olson2011tags.pdf) — the original AprilTag paper; directly relevant to fiducial-based localization exercises.
- Ross, ["Fiducial Marker Navigation for Mobile Robots"](http://www.cs.ru.ac.za/research/g09r5654/downloads/shortpaper.pdf) — practical treatment of using fiducial markers for robot navigation.
- Endres et al., ["An Evaluation of the RGB-D SLAM System"](http://www2.informatik.uni-freiburg.de/~endres/files/publications/endres12icra.pdf) — evaluation of visual + depth SLAM, relevant to depth camera work.
- Murphy, ["Human-Robot Interaction in Rescue Robotics" (2004)](https://www.aaai.org/Papers/Symposia/Spring/2007/SS-07-09/SS07-09-020.pdf) — real-world context for why vision and sensing robustness matters so much.

---

*This chapter is based solely on classroom source materials and is designed for educational use.*

> **Disclaimer:** This content was generated from classroom source materials by an AI assistant. Errors may be present — please report any to [pitosalas@gmail.com](mailto:pitosalas@gmail.com).
