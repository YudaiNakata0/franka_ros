# ROS integration for Franka Robotics research robots

[![CI](https://github.com/frankarobotics/franka_ros/actions/workflows/ci.yml/badge.svg)](https://github.com/frankarobotics/franka_ros/actions/workflows/ci.yml)


See the [Franka Control Interface (FCI) documentation][fci-docs] for more information.

## License

All packages of `franka_ros` are licensed under the [Apache 2.0 license][apache-2.0].

[apache-2.0]: https://www.apache.org/licenses/LICENSE-2.0.html
[fci-docs]: https://frankarobotics.github.io/docs

## Notes on Installation
+ Install packages before build
```bash
# replace ${ROS_DISTRO} with noetic, one, ...
sudo apt install ros-${ROS_DISTRO}-libfranka ros-${ROS_DISTRO}-ros-control
#  additional packages (for when errors occur)
sudo apt install ros-${ROS_DISTRO}-ros-controllers ros-${ROS_DISTRO}-combined-robot-hw
```
+ C++ version *handled in commit af0f5ff
  + use C++17
+ boost_sml *handled in commit af0f5ff, fc6de0b
  + install source from https://github.com/boost-ext/sml.git and place under franka_gazebo/include/
  + change library name
    + ```
      #include <boost_sml/sml.hpp> -> #include <boost/sml.hpp>
      ```
  + CMakeLists.txt
    + add "include/sml/include" to include_directories()
    + remove "boost_sml" from find_package(), catkin_package()
