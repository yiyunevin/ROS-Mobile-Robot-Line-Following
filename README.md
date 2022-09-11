# ROS-Mobile-Robot-Red-Line-Following

Conclusion of ROS Practice

+ roscpp / rospy
+ topic / service / action
+ launch (all-in-one)
+ ros with opencv (monocular camera)
+ youbot control (both arm and moobile base)

## Environment Setup

- Environment: Ubuntu 18.04 + ROS Melodic
- Platform: KUKA youBot
- Visual Device: Pointgrey Flea3 camera 

## Usage

1. Clone the repository to workspace and compile by `$ catkin_make`
2. Prepare the dependencies:
    - [pointgrey_camera_driver](http://wiki.ros.org/pointgrey_camera_driver)
    - [camera_calibration](http://wiki.ros.org/camera_calibration)
    - [image_proc](http://wiki.ros.org/image_proc)
3. Adjust the filepathes in `.../script/follow_line.py` and `.../script/follow_record.py`
4. Launch files: 
    ```
    roslaunch youbot_driver_ros_interface youbot_driver.launch
    roslaunch find_line youbot_findline.launch
    ```
5. Follow the hints on the screen

### Parameters of launch file

+ ```/image_pub```: the result image will be published to topic `/camera/find_red_line` (true) or directly show with cv::imshow (false)
+ ```/print_red_info```: (for debugging) print the information about line detection 
+ ```/do_arm_ini```、```/do_follow_line```、```/do_back_line```、```/do_arm_home```: enable each task

### Result (Image Processing)

+ `M` : Slope 
+ `White px` : area of the above part of the path in pixel

<p align=center>
    <img width="50%" src=https://user-images.githubusercontent.com/26008008/189539266-01060d5c-fc8d-4633-8860-2eb336c166b6.png>
    <img width="50%" src=https://user-images.githubusercontent.com/26008008/189539268-c0a23b6c-8f60-4836-b072-23e0afb9671c.png>
</p>

