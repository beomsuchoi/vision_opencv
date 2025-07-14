vision_opencv
=============

# 1. 기존 cv_bridge 제거
sudo apt remove ros-humble-cv-bridge

# 2. cv_bridge 소스 다운로드
cd ~/ros2_ws/src
git clone https://github.com/ros-perception/vision_opencv.git -b humble

# 3. OpenCV 4.XX.0 경로 설정
export OpenCV_DIR=/usr/local/lib/cmake/opencv4
export PKG_CONFIG_PATH=/usr/local/lib/pkgconfig:$PKG_CONFIG_PATH

# 4. cv_bridge를 OpenCV 4.XX.0용으로 재빌드 (현재 4.10.0 쓰는 중)
cd ~/ros2_ws
colcon build --packages-select cv_bridge --cmake-args -DCMAKE_BUILD_TYPE=Release

# 5. 환경 설정
source install/setup.bash
