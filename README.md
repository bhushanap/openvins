# OpenVins for Ros Eloquent
# Installation

Install following dependencies as mentioned [here](https://docs.openvins.com/gs-installing.html) -

`sudo apt-get install ros-eloquent-ros2bag ros-eloquent-rosbag2*` (Bag utilities, not all might work, it's fine)

`sudo apt-get install libeigen3-dev libboost-all-dev libceres-dev`

`sudo apt-get install ros-eloquent-cv-bridge` (Try uninstalling and reinstalling opencv bridge if build gives errors)

(IF THE ABOVE DOESN'T SUFFICE, THEN ONLY BUILD OPENCV, else ignore these next few steps)

`git clone https://github.com/opencv/opencv/`

`mkdir opencv/build/`

`cd opencv/build/`

`cmake -DOPENCV_EXTRA_MODULES_PATH=../../opencv_contrib/modules ..`

`make -j8`

`sudo make install`

Asssuming the dependencies are installed correctly, build openvins

`mkdir -p ~/ov_ws/src/`

`cd ~/ov_ws/src/`

`git clone https://github.com/bhushanap/openvins/`

`cd ..`

`colcon build -DENABLE_ARUCO_TAGS=OFF`

# Important Folder

[Configuration](config/racecar) folder links to estimator parameters as well as calibrated values for camera and IMU intrinsics. These can be tweaked to adjust performance of the algorithm.

The topics to scan from the IMU and camera are also adjusted here.

Use `ros2 launch ov_msckf subscribe.launch.py config:=racecar rviz_enable:=true` to launch the state estimator with visualization enabled. New configs can be made and saved in another folder like the racecar configuration folder.

