cmake_minimum_required(VERSION 2.8.12)
project(arm_moving)


add_compile_options(-std=c++11)

find_package(catkin REQUIRED COMPONENTS
  moveit_core
  roscpp
  rospy
  std_msgs
  moveit_ros_planning
  moveit_ros_planning_interface
  geometry_msgs
  moveit_visual_tools
)

catkin_package(
    CATKIN_DEPENDS
        moveit_core
        moveit_ros_planning
        moveit_ros_planning_interface
)

include_directories(
  ${catkin_INCLUDE_DIRS}
)

add_executable(pr2_arm_moving src/pr2_arm_moving.cpp)
add_dependencies(pr2_arm_moving ${${PROJECT_NAME}_EXPORTED_TARGETS} ${catkin_EXPORTED_TARGETS})
target_link_libraries(pr2_arm_moving ${catkin_LIBRARIES})

