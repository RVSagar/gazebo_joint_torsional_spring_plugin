cmake_minimum_required(VERSION 2.8.3 FATAL_ERROR)
project(gazebo_joint_torsional_spring)

# Load catkin and all dependencies required for this package
find_package(catkin REQUIRED COMPONENTS 
  roscpp 
  gazebo_ros 
)

# Find Gazebo
find_package(gazebo REQUIRED)
include_directories(${GAZEBO_INCLUDE_DIRS})
link_directories(${GAZEBO_LIBRARY_DIRS})
set(CMAKE_CXX_FLAGS "${CMAKE_CXX_FLAGS} ${GAZEBO_CXX_FLAGS}")

catkin_package(
  DEPENDS 
    roscpp 
    gazebo_ros 
)

# Build plugin
add_library(joint_torsional_spring_plugin SHARED src/gazebo_joint_torsional_spring.cpp)
target_link_libraries(joint_torsional_spring_plugin ${GAZEBO_LIBRARIES})

