# TurtleBot 4 Autonomous Navigation & YOLO Object Detection

Dự án này thực hiện định vị (AMCL), điều hướng tự động tuần tự qua các điểm mục tiêu (Waypoints Navigation sử dụng Nav2) và tích hợp nhận diện vật thể thời gian thực bằng mô hình YOLO trên robot mô phỏng TurtleBot 4 trong Gazebo (ROS 2 Humble).

## Cấu trúc Repository
- `launch/`: Các file launch khởi chạy mô phỏng, bản đồ và node điều khiển[cite: 1].
- `config/`: Các file cấu hình cho Nav2, AMCL, RViz2[cite: 1].
- `maps/`: Chứa file bản đồ `map.yaml` và `map.pgm`[cite: 1].
- `scripts/` hoặc thư mục source code của node: Chứa code Python điều hướng và nhận diện YOLO[cite: 1].

## Hướng dẫn cài đặt và Build

1. Clone repository vào thư mục `src` của ROS 2 workspace:
   ```bash
   cd ~/ros2_ws/src
   git clone [https://github.com/YOUR_USERNAME/turtlebot4_navigation_yolo.git](https://github.com/YOUR_USERNAME/turtlebot4_navigation_yolo.git)

    Cài đặt các gói phụ thuộc hệ thống và thư viện Python[cite: 1]:
    Bash

    sudo apt update
    sudo apt install ros-humble-turtlebot4-navigation ros-humble-nav2-simple-commander ros-humble-cv-bridge
    pip install ultralytics opencv-python

    Build package bằng colcon:
    Bash

    cd ~/ros2_ws
    colcon build --packages-select tb4_simplesimu
    source install/setup.bash

Hướng dẫn chạy chương trình

    Khởi chạy môi trường mô phỏng và nạp bản đồ (Localization & Navigation):
    Bash

    ros2 launch tb4_simplesimu sim_nav.launch.py

    Chạy node điều khiển di chuyển tự động qua các điểm Goal:
    Bash

    ros2 run tb4_simplesimu navigate_waypoints.py

    Chạy node nhận diện vật thể YOLO kết hợp camera:
    Bash

    ros2 run tb4_simplesimu yolo_detector.py
