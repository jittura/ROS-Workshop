# Custom Message in ROS

```
#!/usr/bin/env python

 import rospy
 from my_package.msg import Point3D

 rospy.init_node('point_publisher')
 pub = rospy.Publisher('/point', Point3D, queue_size=10)

 point = Point3D()
 point.x = 1.0
 point.y = 2.0
 point.z = 3.0

 rate = rospy.Rate(10)
 while not rospy.is_shutdown():
    pub.publish(point)
    rate.sleep()
```
In CMakeLists.txt, do the following editing  
  ```
  find_package(catkin REQUIRED COMPONENTS
  roscpp
  rospy
  std_msgs
  message_generation # add this line
)
```

Also add
```
add_message_files(
  FILES
  MyCustomMessage.msg # add your message file(s) here
)

generate_messages(
  DEPENDENCIES
  std_msgs
)
```
In package.xml, do the following edit
```
<build_depend>message_generation</build_depend>
<exec_depend>message_runtime</exec_depend>
```



