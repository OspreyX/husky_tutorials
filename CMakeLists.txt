cmake_minimum_required(VERSION 2.8.3)
project(husky_tutorials)

find_package(catkin REQUIRED COMPONENTS roscpp roslaunch moveit_ros_planning_interface cmake_modules)
find_package(Eigen REQUIRED)
include_directories(SYSTEM ${Boost_INCLUDE_DIR} ${EIGEN_INCLUDE_DIRS})
include_directories(${catkin_INCLUDE_DIRS})
link_directories(${catkin_LIBRARY_DIRS})

catkin_package()

roslaunch_add_file_check(launch)

add_executable(pick_place_tutorial src/pick_place_tutorial.cpp)
target_link_libraries(pick_place_tutorial ${catkin_LIBRARIES})

install(DIRECTORY src launch 
  DESTINATION ${CATKIN_PACKAGE_SHARE_DESTINATION}
)

install(TARGETS pick_place_tutorial DESTINATION ${CATKIN_PACKAGE_BIN_DESTINATION})

