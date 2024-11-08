#!/usr/bin/env python3

import rospy
from geometry_msgs.msg import PoseArray, Pose
from std_msgs.msg import Header

def publish_pose_array():
    pub = rospy.Publisher('pose_array', PoseArray, queue_size=10)
    rospy.init_node('pose_array_publisher', anonymous=True)
    rate = rospy.Rate(10)  # 10 Hz
    
    while not rospy.is_shutdown():
        pose_array = PoseArray()
        pose_array.header = Header()
        pose_array.header.stamp = rospy.Time.now()
        pose_array.header.frame_id = "map"  # Change as needed

        # Create some dummy poses
        for i in range(5):
            pose = Pose()
            pose.position.x = i
            pose.position.y = i
            pose.position.z = 0
            pose.orientation.w = 1.0  # No rotation
            pose_array.poses.append(pose)

        pub.publish(pose_array)
        rate.sleep()

if __name__ == '__main__':
    try:
        publish_pose_array()
    except rospy.ROSInterruptException:
        pass
