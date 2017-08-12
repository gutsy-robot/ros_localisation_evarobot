You need to have the evarobot simulator for running this example.

After you have installed the simulator and other dependencies.


Do a: 		
		
	roslaunch ros_localization_evarobot dual_ekf_navsat_example.launch 

In a seperate terminal go to the bag directory of the project and do a:

	rosbag play gps_only.bag

I have used the evarobot sim, because it has an IMU already mounted on the robot, so I don't need to write manual transforms from base_link to imu_link. When using this in our car, we will have the transforms(once we finish writing them) between these links, so we should be fine.

Also, I have filtered out the sensor_msgs/NavStat msgs from the rosbags given on the ROS Localisation repo: 
				
				https://github.com/cra-ros-pkg/robot_localization

Because while using the simulator I already have an odom source and IMU msgs, so I don't need those msgs from the rosbag as they will conflict in case I directly play them.

When we run this on the car, we would have a different odom source(visual odomotery). This example is only an attempt to show how we can configure the .yaml and launch files for our case.

Hope this was helpful!
