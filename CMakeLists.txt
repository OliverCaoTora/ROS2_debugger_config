cmake_minimum_required(VERSION 3.10)
project(ros_topic_dynamic_load)

if(CMAKE_COMPILER_IS_GNUCXX OR CMAKE_CXX_COMPILER_ID MATCHES "Clang")
  add_compile_options(-Wall -Wextra -Wpedantic)
endif()

# find dependencies
find_package(ament_cmake REQUIRED)
find_package(rclcpp REQUIRED)
find_package(std_msgs REQUIRED)
find_package(sereact_custom_messaging REQUIRED)
find_package(nlohmann_json REQUIRED)

set(CMAKE_CXX_STANDARD 17) # Adjusted to C++17, common for ROS 2
set(CMAKE_CXX_STANDARD_REQUIRED ON)
set(CMAKE_CXX_EXTENSIONS OFF)

add_executable(ros_topic_dynamic_load 
    src/test_conveyor_manager.cpp
)

target_sources(ros_topic_dynamic_load PRIVATE
  src/conveyor_segment.cpp
  src/conveyor_segment_straight.cpp
  src/conveyor_segment_cross.cpp
)

target_include_directories(ros_topic_dynamic_load PRIVATE
    ${CMAKE_CURRENT_SOURCE_DIR}/include
)

ament_target_dependencies(ros_topic_dynamic_load
    rclcpp
    std_msgs
    sereact_custom_messaging
    nlohmann_json
)

# Install executable
install(TARGETS 
    ros_topic_dynamic_load
    DESTINATION lib/${PROJECT_NAME}
)

if(BUILD_TESTING)
  find_package(ament_lint_auto REQUIRED)
  # the following line skips the linter which checks for copyrights
  # comment the line when a copyright and license is added to all source files
  set(ament_cmake_copyright_FOUND TRUE)
  # the following line skips cpplint (only works in a git repo)
  # comment the line when this package is in a git repo and when
  # a copyright and license is added to all source files
  set(ament_cmake_cpplint_FOUND TRUE)
  ament_lint_auto_find_test_dependencies()
endif()

ament_package()
