project(webcam2ros)
cmake_minimum_required(VERSION 3.10)

find_package(catkin REQUIRED COMPONENTS
  cv_bridge
  image_transport
  roscpp
  sensor_msgs
  std_msgs
)
find_package(OpenCV REQUIRED)
 
include_directories(
  ${catkin_INCLUDE_DIRS}
  ${OpenCV_INCLUDE_DIRS}
)

catkin_package( 
  INCLUDE_DIRS include
  LIBRARIES
  CATKIN_DEPENDS roscpp std_msgs image_transport sensor_msgs std_msgs cv_bridge
  DEPENDS
) 
add_executable(img_publisher src/img_publisher.cpp)
add_executable(img_viewer src/img_viewer.cpp)
 
target_link_libraries(img_publisher ${catkin_LIBRARIES} ${OpenCV_LIBS})
target_link_libraries(img_viewer ${catkin_LIBRARIES} ${OpenCV_LIBS})
