# OpenVins for Ros Eloquent
# Installation
`sudo apt-get install ros-eloquent-ros2bag ros-eloquent-rosbag2*` (Bag utilities, not all might work, it's fine)
`sudo apt-get install libeigen3-dev libboost-all-dev libceres-dev`
`sudo apt-get install ros-eloquent-cv-bridge` (Try uninstalling and reinstalling opencv bridge if build gives errors)

(ONLY BUILD OPENCV THIS IF BUILD ERROR PERSISTS, else ignore these steps)
(No need to build opencv contrib with -DENABLE_ARUCO_TAGS=OFF, can be skipped)
`git clone https://github.com/opencv/opencv/
git clone https://github.com/opencv/opencv_contrib/
mkdir opencv/build/
cd opencv/build/
cmake -DOPENCV_EXTRA_MODULES_PATH=../../opencv_contrib/modules ..
make -j8
sudo make install`

If dependencies are installed, build openvins
`mkdir -p ~/ov_ws/src/`
`cd ~/ov_ws/src/`
`git clone https://github.com/bhushanap/openvins/`
`cd ..`
`colcon build -DENABLE_ARUCO_TAGS=OFF`
