---
title: "Chapter 4 Outline: Sensors Overview"
date: 2026-04-26
author: Claude Sonnet 4.6
---

# Chapter 4 Outline: Sensors Overview

## 4.1 Why Sensors Are Everything

- Robotics is extensively sensor-driven — without sensors, no autonomy
- Sensors are the bridge between physical world and software
- Every decision a robot makes is based on sensor data
- Key insight: sensors are always noisy and imperfect — algorithms must account for this

## 4.2 LIDAR

- Rotating laser beam, time-of-flight measurement
- Produces a `ranges` array: distance at each bearing angle
- Publishes to `/scan` as `LaserScan` message
- 2D vs. 3D LIDAR
- Key limitation: operates in single horizontal plane
- Invalid values: `inf`, `0`, values below min / above max range
- Our platform: YDLIDAR X4

## 4.3 Visual Cameras

- Standard webcam: 2D pixel matrix, each pixel `{r,g,b}`
- Published as `sensor_msgs/Image` on `/camera/rgb/image_raw`
- Compressed variants: `/compressed`, `/theora` for WiFi bandwidth
- Processed with OpenCV
- Data volume: 640×480 @ 30fps = ~27M pixel values/sec
- Bandwidth constraint is real on wireless links

## 4.4 Depth Cameras

- Adds distance per pixel: `{r,g,b,d}`
- Microsoft Kinect was first widely used example
- Useful for detecting objects and measuring their range simultaneously
- Higher data volume than color camera
- Not present on base TurtleBot3 Burger; available on Waffle model

## 4.5 Odometry (Wheel Encoders)

- Encoders count wheel rotations as pulses
- Forward kinematics: wheel rotations → distance traveled
- Published as `nav_msgs/Odometry` on `/odom`
- Accumulates error over time (wheel slip, floor imperfections)
- Foundation of dead reckoning — only source of pose if no other sensor
- Differential drive: compute x, y, theta from left/right wheel counts

## 4.6 IMU (Inertial Measurement Unit)

- 3-axis accelerometer: measures linear acceleration
- 3-axis gyroscope: measures angular velocity
- 3-axis magnetometer: measures magnetic heading
- TurtleBot3 OpenCR board includes 9-axis IMU (MPU9250)
- Used for orientation estimation, fused with wheel odometry
- Gyroscope drifts over time — must be corrected

## 4.7 Other Sensors

- **Touch / bump sensors** — detect physical contact; simple but reliable
- **Cliff sensors** — infrared; detect floor drop-offs (Roomba-style)
- **GPS** — outdoor positioning; meter-level accuracy, unavailable indoors
- **Ultrasonic sensors** — cheap distance measurement; less accurate than LIDAR
- **Infrared** — short-range proximity; common in simple platforms

## 4.8 Sensor Fusion

- No single sensor is sufficient — each has blind spots and failure modes
- Combining multiple sensors improves reliability and accuracy
- Example: odometry + IMU → better pose estimate than either alone
- Example: odometry + LIDAR → SLAM
- The robot's belief about its state is always a probabilistic estimate

## 4.9 Working with Sensor Data in ROS

- Every sensor publishes to a topic with a standard message type
- Key sensor topics on TurtleBot3:
  - `/scan` — LIDAR (`LaserScan`)
  - `/odom` — wheel odometry (`Odometry`)
  - `/imu` — IMU data (`Imu`)
  - `/camera/rgb/image_raw` — camera (Waffle only) (`Image`)
- Visualize with RViz: see sensor data in real time in 3D
- Inspect with `ros2 topic echo`, `ros2 topic hz`
