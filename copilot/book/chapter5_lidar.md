---
title: Working with LIDAR
author: GPT-4.1
date: 2026-04-26
prev_url: /copilot/book/chapter4_sensors_overview/
prev_title: "Chapter 4: Sensors Overview"
next_url: /copilot/book/chapter6_computer_vision/
next_title: "Chapter 6: Computer Vision"
---


# Chapter 5: Working with LIDAR

## 5.1 Introduction to LIDAR
LIDAR (Light Detection and Ranging) is one of the most important sensors in modern mobile robotics. It works by emitting laser pulses and measuring the time it takes for the light to reflect off objects and return. By rotating the laser, a LIDAR sensor can quickly scan its surroundings and build a 2D or 3D map of distances to obstacles.

LIDAR is used for mapping, localization, and obstacle avoidance. For example, the YDLIDAR X4 (used in our robots) provides a 2D scan of the environment, which is essential for navigation and safety. For a broader look at where LIDAR fits among all robot sensors, see [Chapter 4: Sensors Overview](chapter4_sensors_overview.md#42-lidar).

## 5.2 LIDAR Data Structure
LIDAR data is published in ROS 2 on the `/scan` topic as `sensor_msgs/msg/LaserScan` messages. The most important field is `ranges`, which is an array of distance measurements. Each entry in this array corresponds to a specific angle, so together they form a "slice" of the robot's surroundings.

Other fields in the message include the minimum and maximum angles, the increment between measurements, and the time at which the scan was taken. For more details, see the [LaserScan message documentation](https://docs.ros2.org/latest/api/sensor_msgs/msg/LaserScan.html).

Here is a minimal ROS 2 Python node that subscribes to LIDAR data:

```python
import rclpy
from rclpy.node import Node
from sensor_msgs.msg import LaserScan

class LidarListener(Node):
    def __init__(self):
        super().__init__('lidar_listener')
        self.create_subscription(LaserScan, '/scan', self.scan_callback, 10)

    def scan_callback(self, msg):
        self.get_logger().info(f'Received scan with {len(msg.ranges)} ranges')
        mid = len(msg.ranges) // 2
        self.get_logger().info(f'Distance ahead: {msg.ranges[mid]:.2f} m')

def main():
    rclpy.init()
    rclpy.spin(LidarListener())
    rclpy.shutdown()

if __name__ == '__main__':
    main()
```

## 5.3 Filtering and Cleaning LIDAR Data
Raw LIDAR data is often noisy. Reflections, transparent objects, or sensor limitations can produce invalid readings (such as 0 or NaN). Filtering is essential before using the data for navigation or mapping.

Common filtering steps include:
- Removing outliers (values outside the sensor's valid range)
- Replacing invalid values with a maximum distance or ignoring them
- Smoothing the data with a moving average or median filter

You can write a ROS 2 node that subscribes to `/scan`, filters the data, and republishes it on a new topic (e.g., `/scan_filtered`). See the [ROS 2 Writing a Simple Publisher and Subscriber tutorial](https://docs.ros.org/en/rolling/Tutorials/Beginner-Client-Libraries/Writing-A-Simple-Py-Publisher-And-Subscriber.html) for the pattern.

## 5.4 Obstacle Detection
One of the main uses of LIDAR is obstacle detection. By examining the `ranges` array, you can identify obstacles that are closer than a certain threshold. For example, if any value in `ranges` is less than 0.3 meters, the robot should stop or turn to avoid a collision.

You can also segment the scan to identify free and occupied regions, which is useful for mapping and path planning. More advanced algorithms can cluster points to detect individual objects or walls.

## 5.5 Visualization and Debugging
Visualization tools are essential for understanding and debugging LIDAR data. In ROS 2, [RViz2](https://docs.ros.org/en/rolling/Tutorials/Intermediate/RViz/RViz-User-Guide/RViz-User-Guide.html) is the standard tool for visualizing 2D and 3D sensor data. You can see the LIDAR scan as a set of points or lines in the robot's coordinate frame.

To analyze LIDAR data offline, you can save it to a CSV file using the following command:

```bash
ros2 topic echo --csv /scan | head -n 50 > ~/scan_data.csv
```

This records 50 messages from the `/scan` topic for later analysis in a spreadsheet or plotting tool.

## Assignments

The following assignments relate to LIDAR topics in this chapter:

- **PA: Lidar Wall Follow** — Using LIDAR sensing to drive the robot along a wall
- **PA: Maze Escape!** — Use wall-following algorithms in a maze escape
- **Mini-PA: Filter Scan** (Lab 8) — Filter raw scan data before using it for navigation
- **Mini-PA: Robo Chaser** (Lab 9) — Use LIDAR distance data to follow a target robot

## 5.6 Further Reading
- [YDLIDAR X4](https://www.ydlidar.com/products/view/5.html)
- [Reading Laserscan Data](http://www.theconstructsim.com/read-laserscan-data/)
- [RViz2 User Guide](https://docs.ros.org/en/rolling/Tutorials/Intermediate/RViz/RViz-User-Guide/RViz-User-Guide.html)
- [SLAM Toolbox (ROS 2)](https://docs.ros.org/en/rolling/p/slam_toolbox/) — the standard package for 2D LIDAR-based simultaneous localization and mapping in ROS 2
- [Nav2 — Navigation Stack for ROS 2](https://nav2.ros.org/) — the full navigation framework that uses LIDAR data for costmaps, path planning, and obstacle avoidance

### Relevant Papers
- Riisgaard & Blas, ["SLAM for Dummies: A Tutorial Approach to Simultaneous Localization and Mapping" (2004)](https://dspace.mit.edu/bitstream/handle/1721.1/36832/16-412JSpring2004/NR/rdonlyres/Aeronautics-and-Astronautics/16-412JSpring2004/A3C5517F-C092-4554-AA43-232DC74609B3/0/1Aslam_blas_report.pdf) — the most accessible introduction to how LIDAR scans are used to build maps and localize simultaneously.
- ["Wall Following for Autonomous Navigation"](https://sunfest.seas.upenn.edu/wp-content/uploads/2018/07/12-bayer.pdf) — a concrete example of LIDAR-based reactive navigation, directly relevant to obstacle-avoidance exercises.
- Fox et al., ["The Dynamic Window Approach to Collision Avoidance"](http://www.cs.washington.edu/node/4749) — the classic paper for converting LIDAR obstacle data into safe velocity commands.

---

*This chapter is based solely on classroom source materials and is designed for educational use.*

> **Disclaimer:** This content was generated from classroom source materials by an AI assistant. Errors may be present — please report any to [pitosalas@gmail.com](mailto:pitosalas@gmail.com).
