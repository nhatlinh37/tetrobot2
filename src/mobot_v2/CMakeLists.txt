cmake_minimum_required(VERSION 2.8.3)

project(mobot_v2)

find_package(catkin REQUIRED COMPONENTS
	message_generation
	roscpp
	rospy
	std_msgs
	geometry_msgs
	urdf
	xacro
	message_generation
)

catkin_package(
	CATKIN_DEPENDS
	geometry_msgs
	roscpp
	rospy
	std_msgs
)

find_package(roslaunch)

foreach(dir config launch meshes urdf)
	install(DIRECTORY ${dir}/
		DESTINATION ${CATKIN_PACKAGE_SHARE_DESTINATION}/${dir})
endforeach(dir)

# Install Python scripts
catkin_install_python(PROGRAMS
  lidar_publisher.py
  pose_array_publisher.py
  DESTINATION ${CATKIN_PACKAGE_BIN_DESTINATION}
)