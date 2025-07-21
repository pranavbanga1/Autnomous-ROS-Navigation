# 🐢 TurtleBot3 – Vision-Based Navigation with ROS

This project implements a **monocular vision-based obstacle avoidance system** on the TurtleBot3 Burger using **ROS Noetic**. In this milestone, the robot autonomously detects orange traffic cones simulating road construction and maneuvers around them in real time.

<img width="1820" height="1012" alt="Test1" src="https://github.com/user-attachments/assets/192b3776-2f3d-4189-a314-843cf2866c3f" />


---

## 🎯 Project Objective

Enable the TurtleBot3 to:

- Detect orange traffic cones using HSV segmentation
- Execute a bypass maneuver into the opposing lane
- Return to its original lane after passing obstacles
- Operate entirely using **camera input** no LIDAR, depth sensors, or maps

---

## 💡 Real-World Relevance

Autonomous systems must detect and avoid unexpected hazards (e.g., roadblocks or construction zones) without compromising safety or operation. This project mimics such behavior using **low-cost hardware** and open-source ROS tools, making it applicable to:

- Warehouse robots
- Last-mile autonomous delivery
- Smart mobility platforms

---

## 🔁 Recap of Milestones

- **Milestone 1:** Lane detection using Canny edge detection + Hough Transform with proportional control
- **Milestone 2:** Traffic light detection and stop-go logic using HSV color segmentation
- **Milestone 3:** This phase adds orange cone detection and integrates avoidance logic

---

## 🧠 Engineering Specs

- ✅ **Obstacle Detection** – Detect traffic cones using HSV-based color filtering  
- ✅ **Maneuvering** – Veer into adjacent lane and return post-obstacle  
- ✅ **Vision-Only** – No LIDAR, depth sensors, or GPS  
- ✅ **Autonomous** – No human intervention  
- ✅ **ROS Integrated** – Multiple nodes for modular behavior control

---

## 🧪 ROS Nodes Used

```bash
📦 /lane_detector_node        # Canny + Hough-based center alignment
📦 /traffic_light_node        # HSV-based red/green light logic
📦 /cone_detector_node        # HSV-filtered orange cone detection
📦 /avoidance_controller_node # Executes timed avoidance trajectory
```

<img width="1671" height="661" alt="workflow" src="https://github.com/user-attachments/assets/9eea09c7-b3c0-49c0-a047-d154fd23895f" />

---

## 🛠️ Installation & Setup

```bash
# Clone repo
git clone https://github.com/yourusername/turtlebot3-obstacle-avoidance.git
cd turtlebot3-obstacle-avoidance

# Source ROS
source /opt/ros/noetic/setup.bash
source ~/catkin_ws/devel/setup.bash

# Install dependencies
rosdep install --from-paths src --ignore-src -r -y

# Launch system
roslaunch turtlebot3_vision autonav_phase3.launch
```

> ⚠️ Ensure camera calibration is done before running.

---

## 📂 Code Structure

```
turtlebot3_vision/
├── launch/
│   └── autonav_phase3.launch
├── nodes/
│   ├── cone_detector.py
│   ├── avoidance_controller.py
│   └── lane_following.py
├── config/
│   └── hsv_thresholds.yaml
├── scripts/
│   └── calibration.py
└── README.md
```

---

## 🧪 Testing & Calibration

- `scripts/calibration.py` – for tuning HSV thresholds
- Tune `hsv_thresholds.yaml` based on lighting
- Test `cone_detector.py` with recorded bagfiles before deploying
  
<p align="center">
  <img src="https://github.com/user-attachments/assets/b2f13837-b5a1-4bf3-9d40-1f768c30f0bc" width="30%" alt="HSV Param" />
  <img src="https://github.com/user-attachments/assets/8be71a44-b84c-497a-9629-f728e05a8f5f" width="30%" alt="Green Calibration" />
  <img src="https://github.com/user-attachments/assets/e35fd614-fbd7-45f8-a9f7-ca8071f70ceb" width="30%" alt="Forecasted View" />
  
</p>






---

## 🧠 Learnings

- ✅ Achieved reactive autonomy with **monocular camera only**
- ✅ Integrated multiple ROS nodes for behavior layering
- ✅ Mimicked real-world lane management using simple computer vision

---

## 🙌 Acknowledgements

Developed for the **Mobile Robotics Course**, Ontario Tech University.  
Powered by: `ROS`, `OpenCV`, `Python`, `TurtleBot3 Burger`

---


