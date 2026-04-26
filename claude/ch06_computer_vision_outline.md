---
title: "Chapter 6 Outline: Computer Vision"
date: 2026-04-26
author: Claude Sonnet 4.6
---

# Chapter 6 Outline: Computer Vision

## 6.1 Vision in Robotics

- Cameras give robots rich information LIDAR cannot: color, texture, shape, faces, text
- Computer vision = algorithms that extract meaning from pixel arrays
- Key challenge: huge data volume, high computational cost
- ROS provides standard image message types and bridges to OpenCV
- This chapter: practical introduction — get images, process them, steer a robot

## 6.2 Camera Types

- **Standard RGB camera** — color image, `{r,g,b}` per pixel
- **Depth camera** — adds distance per pixel `{r,g,b,d}`; e.g. Intel RealSense, Kinect
- **Fisheye / wide-angle** — wider field of view, more distortion
- **Stereo camera** — two lenses, derive depth from disparity
- TurtleBot3 Waffle has a Raspberry Pi Camera (RGB); Burger does not

## 6.3 Images in ROS

- Message type: `sensor_msgs/Image`
- Published to `/camera/rgb/image_raw`
- Compressed variants save bandwidth over WiFi:
  - `/camera/rgb/image_raw/compressed` — JPEG/PNG
  - `/camera/rgb/image_raw/theora` — video stream
- Visualize live with:

```bash
ros2 run rqt_image_view rqt_image_view
```

- Frame rate matters: ~10 fps in simulation, up to 30 fps on hardware
- High frame rate = high CPU load; tune as needed

## 6.4 OpenCV and cv_bridge

- OpenCV is the standard computer vision library (Python: `cv2`)
- `cv_bridge` converts between `sensor_msgs/Image` and OpenCV's `numpy` array format

```python
from cv_bridge import CvBridge
import cv2

bridge = CvBridge()

def image_callback(msg):
    cv_image = bridge.imgmsg_to_cv2(msg, desired_encoding='bgr8')
    # cv_image is now a numpy array: shape (height, width, 3)
    cv2.imshow("Camera", cv_image)
    cv2.waitKey(1)
```

## 6.5 Color Filtering

- Goal: isolate pixels of a specific color (e.g., a yellow line)
- HSV color space is better than RGB for color filtering — separates hue from brightness
- Convert to HSV, define color range, apply mask:

```python
hsv = cv2.cvtColor(cv_image, cv2.COLOR_BGR2HSV)
lower_yellow = np.array([40, 0, 0])
upper_yellow = np.array([120, 255, 255])
mask = cv2.inRange(hsv, lower_yellow, upper_yellow)
```

- `mask` is a binary image: 255 where color matches, 0 elsewhere
- Color thresholds must be tuned for specific lighting conditions

## 6.6 Finding the Centroid

- After masking, find the center of mass of the matching pixels
- Centroid = weighted average of pixel positions — tells you *where* the feature is

```python
M = cv2.moments(mask)
if M['m00'] > 0:
    cx = int(M['m10'] / M['m00'])  # centroid x
    cy = int(M['m01'] / M['m00'])  # centroid y
```

- `cx` tells you if the line is left or right of center
- Use this to compute a steering correction

## 6.7 Line Following

- Full pipeline: acquire image → filter by color → find centroid → compute error → steer
- Error = centroid x position minus image center x
- Feed error to proportional controller (or full PID):

```python
error = cx - image_width / 2
angular_z = -error * KP        # proportional gain
twist.linear.x = FORWARD_SPEED
twist.angular.z = angular_z
cmd_vel_pub.publish(twist)
```

- This is a P-controller (proportional only); adding I and D terms improves tracking
- Works well on clear lines with consistent lighting; fails in poor conditions

## 6.8 Fiducial Markers

- Fiducials are printed patterns robots can detect and identify reliably
- More robust than color filtering: work in varied lighting, give position and orientation
- Common systems: ArUco markers, AprilTags
- Each marker has a unique ID — robot can distinguish multiple markers
- ROS packages: `aruco_detect`, `apriltag_ros`
- Uses: labeling goals ("go to marker 5"), docking, multi-robot coordination

## 6.9 Practical Considerations

- **Bandwidth**: compressed images essential over WiFi; raw images for local processing only
- **Latency**: processing pipeline adds delay; factor into control loop timing
- **Lighting**: vision algorithms are sensitive to lighting changes — test in actual conditions
- **Resolution**: higher resolution = more detail but more computation; 320×240 often sufficient for basic tasks
- **RViz**: can display image topics for live debugging
