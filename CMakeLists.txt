cmake_minimum_required(VERSION 3.10)
include(BoBRobotics.cmake)
project(bob_mavros_navigation)

make_base_target()

find_package(catkin REQUIRED COMPONENTS
  mavros_msgs
  roscpp
)

###################################
## catkin specific configuration ##
###################################
## The catkin_package macro generates cmake config files for your package
## Declare things to be passed to dependent projects
## INCLUDE_DIRS: uncomment this if your package contains header files
## LIBRARIES: libraries you create in this project that dependent projects also need
## CATKIN_DEPENDS: catkin_packages dependent projects also need
## DEPENDS: system dependencies of this project that dependent projects also need
catkin_package(
#  INCLUDE_DIRS include
#  LIBRARIES bob_mavros_navigation
#  CATKIN_DEPENDS mavros_msgs roscpp
#  DEPENDS system_lib
)

###########
## Build ##
###########

## Specify additional locations of header files
## Your package locations should be listed before other locations
include_directories(
# include
  ${catkin_INCLUDE_DIRS}
)

## Declare a C++ executable
## With catkin_make all packages are built within a single CMake context
## The recommended prefix ensures that target names across packages don't collide
add_executable(offb_node src/offb_node.cpp)
target_link_libraries(offb_node ${catkin_LIBRARIES} BoBRobotics::base)
