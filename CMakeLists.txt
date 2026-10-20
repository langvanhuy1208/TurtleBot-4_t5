cmake_minimum_required(VERSION 3.8)
project(tb4_simplesimu)

if(CMAKE_COMPILER_IS_GNUCXX OR CMAKE_CXX_COMPILER_ID MATCHES "Clang")
  add_compile_options(-Wall -Wextra -Wpedantic)
endif()

find_package(ament_cmake REQUIRED)

install(DIRECTORY
  launch
  maps
  config
  scripts
  urdf
  worlds
  DESTINATION share/${PROJECT_NAME}
)

install(PROGRAMS
  scripts/auto_mapper.py
  scripts/waypoint_navigator.py
  scripts/yolo_detector.py
  scripts/odom_tf_broadcaster.py
  scripts/scan_retimestamp.py
  DESTINATION lib/${PROJECT_NAME}
)

ament_package()
