# OpenVins for Ros Eloquent
# Installation
`sudo apt-get install ros-eloquent-ros2bag ros-eloquent-rosbag2*` (Bag utilities, not all might work, it's fine)

`sudo apt-get install libeigen3-dev libboost-all-dev libceres-dev`

`sudo apt-get install ros-eloquent-cv-bridge` (Try uninstalling and reinstalling opencv bridge if build gives errors)

(ONLY BUILD OPENCV THIS IF OPENVINS BUILD ERROR PERSISTS, else ignore these next few steps)

(No need to build opencv contrib with -DENABLE_ARUCO_TAGS=OFF, can be skipped)

`git clone https://github.com/opencv/opencv/`

`mkdir opencv/build/`

`cd opencv/build/`

`cmake -DOPENCV_EXTRA_MODULES_PATH=../../opencv_contrib/modules ..`

`make -j8`

`sudo make install`

If above dependencies are installed, build openvins

`mkdir -p ~/ov_ws/src/`

`cd ~/ov_ws/src/`

`git clone https://github.com/bhushanap/openvins/`

`cd ..`

`colcon build -DENABLE_ARUCO_TAGS=OFF`

# Important Folder

[Configuration](config/racecar) folder links to estimator parameters as well as calibrated values for camera and IMU intrinsics. These can be tweaked to adjust performance of the algorithm.

The topics to scan from the IMU and camera are also adjusted here.

Use `ros2 launch ov_msckf subscribe.launch.py config:=racecar rviz_enable:=true` to launch the state estimator with visualization enabled. New configs can be made and saved in another folder like the racecar configuration folder.

