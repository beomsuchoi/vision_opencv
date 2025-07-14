vision_opencv
=============
ros2 vision_opencv contains packages to interface ROS 2 with [OpenCV](http://opencv.org/) which is a library designed for computational efficiency and strong focus for real time computer vision applications. This repository contains:
* `cv_bridge`: Bridge between ROS 2 image messages and OpenCV image representation
* `image_geometry`: Collection of methods for dealing with image and pixel geometry
* `opencv_tests`: Integration tests to use the capability of the packages with opencv
* `vision_opencv`: Meta-package to install both `cv_bridge` and `image_geometry`

In order to use ROS 2 with OpenCV, please see the details within [cv_bridge](https://github.com/ros-perception/vision_opencv/tree/ros2/cv_bridge) package.


# 1. 기존 cv_bridge 제거
sudo apt remove ros-humble-cv-bridge

# 2. cv_bridge 소스 다운로드
cd ~/ros2_ws/src
git clone https://github.com/ros-perception/vision_opencv.git -b humble

# 3. OpenCV 4.10.0 경로 설정
export OpenCV_DIR=/usr/local/lib/cmake/opencv4
export PKG_CONFIG_PATH=/usr/local/lib/pkgconfig:$PKG_CONFIG_PATH

# 4. cv_bridge를 OpenCV 4.10.0용으로 재빌드
cd ~/ros2_ws
colcon build --packages-select cv_bridge --cmake-args -DCMAKE_BUILD_TYPE=Release

# 5. 환경 설정
source install/setup.bash
