cmake_minimum_required(VERSION 2.8.3)
project(cob_mimic)

find_package(catkin REQUIRED COMPONENTS rospy std_msgs message_generation)

#######################################
## Declare ROS messages and services ##
#######################################

add_service_files(DIRECTORY srv FILES
  SetMimic.srv
)

generate_messages(DEPENDENCIES std_msgs)

###################################
## catkin specific configuration ##
###################################

catkin_package(
    CATKIN_DEPENDS rospy std_msgs message_runtime# TODO
    INCLUDE_DIRS # TODO include
    LIBRARIES # TODO
)

#############
## Install ##
#############

## Mark executables and/or libraries for installation
install(TARGETS 
  ARCHIVE DESTINATION ${CATKIN_PACKAGE_LIB_DESTINATION}
  LIBRARY DESTINATION ${CATKIN_PACKAGE_LIB_DESTINATION}
  RUNTIME DESTINATION ${CATKIN_PACKAGE_BIN_DESTINATION}
)

install(PROGRAMS src/mimic_node.py
  DESTINATION ${CATKIN_PACKAGE_BIN_DESTINATION}/src
)

install(DIRECTORY common
  DESTINATION ${CATKIN_PACKAGE_SHARE_DESTINATION}/common
)

