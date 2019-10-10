# Motoman

[![Build Status: ROS buildfarm](http://build.ros.org/job/Kdev__motoman__ubuntu_xenial_amd64/badge/icon)](http://build.ros.org/job/Kdev__motoman__ubuntu_xenial_amd64)
[![Build Status: Travis CI](https://travis-ci.org/ros-industrial/motoman.svg?branch=kinetic-devel)](https://travis-ci.org/ros-industrial/motoman)

[![license - apache 2.0](https://img.shields.io/:license-Apache%202.0-yellowgreen.svg)](https://opensource.org/licenses/Apache-2.0)
[![license - bsd 3 clause](https://img.shields.io/:license-BSD%203--Clause-blue.svg)](https://opensource.org/licenses/BSD-3-Clause)

[![support level: consortium / vendor](https://img.shields.io/badge/support%20level-consortium%20/%20vendor-brightgreen.png)](http://rosindustrial.org/news/2016/10/7/better-supporting-a-growing-ros-industrial-software-platform)


[ROS-Industrial][] Motoman metapackage. See the [ROS wiki][] page for more information.

The [motoman_experimental][] repository contains additional packages.


## Contents

Branch naming follows the ROS distribution they are compatible with. `-devel` branches may be unstable. Releases are made from the distribution branches (`indigo`, `kinetic`).

Older releases may be found in the Github mirror of the old ROS-Industrial [subversion repository][].


## ROS Distro Support

|         | Kinetic |
|:-------:|:-------:|
| Branch  | [`kinetic-devel`](https://github.com/ros-industrial/motoman/tree/kinetic-devel) |
| Status  | supported |
| Version | [version](http://repositories.ros.org/status_page/ros_kinetic_default.html?q=motoman) |


## ROS Buildfarm

|         |  Kinetic Source  |  Kinetic Debian  |
|:-------:|:----------------:|:-----------------|
| motoman | [![not released](http://build.ros.org/buildStatus/icon?job=Ksrc_uX__motoman__ubuntu_xenial__source)](http://build.ros.org/view/Ksrc_uX/job/Ksrc_uX__motoman__ubuntu_xenial__source/) | [![not released](http://build.ros.org/buildStatus/icon?job=Kbin_uX64__motoman__ubuntu_xenial_amd64__binary)](http://build.ros.org/view/Kbin_uX64/job/Kbin_uX64__motoman__ubuntu_xenial_amd64__binary/) |


## Building

### On newer (or older) versions of ROS

Building the packages on newer (or older) versions of ROS is in most cases possible and supported. For example: building the packages in this repository on Ubuntu Xenial/ROS Kinetic or Ubuntu Bionic/ROS Melodic systems is supported. This will require creating a Catkin workspace, cloning this repository, installing all required dependencies and finally building the workspace.

### Catkin tools

It is recommended to use [catkin_tools][] instead of the default [catkin][] when building ROS workspaces. `catkin_tools` provides a number of benefits over regular `catkin_make` and will be used in the instructions below. All packages can be built using `catkin_make` however: use `catkin_make` in place of `catkin build` where appropriate.

### Building the packages

The following instructions assume that a [Catkin workspace][] has been created at `$HOME/catkin_ws` and that the *source space* is at `$HOME/catkin_ws/src`. Update paths appropriately if they are different on the build machine.

These instructions build the `kinetic-devel` branch on a ROS Kinetic system:

```bash
# change to the root of the Catkin workspace
$ cd $HOME/catkin_ws

# retrieve the latest development version of motoman. If you'd rather
# use the latest released version, replace 'kinetic-devel' with 'kinetic'
$ git clone -b kinetic-devel https://github.com/ros-industrial/motoman.git src/motoman

# check build dependencies. Note: this may install additional packages,
# depending on the software installed on the machine
$ rosdep update

# be sure to change 'kinetic' to whichever ROS release you are using
$ rosdep install --from-paths src/ --ignore-src --rosdistro kinetic

# build the workspace (using catkin_tools)
$ catkin build
```

### Activating the workspace

Finally, activate the workspace to get access to the packages just built:

```bash
$ source $HOME/catkin_ws/devel/setup.bash
```

At this point all packages should be usable (ie: `roslaunch` should be able to auto-complete package names starting with `motoman_..`). In case the workspace contains additional packages (ie: not from this repository), those should also still be available.


## Installation and usage

Refer to [Working With ROS-Industrial Robot Support Packages][] for information on how to use the files provided by the robot support and MoveIt configuration packages. See also the other pages on the [ROS wiki][].

Refer to the [tutorials][] for information on installation and configuration of the controller-specific software components.



[ROS-Industrial]: http://wiki.ros.org/Industrial
[ROS wiki]: http://wiki.ros.org/motoman
[motoman_experimental]: https://github.com/ros-industrial/motoman_experimental
[subversion repository]: https://github.com/ros-industrial/swri-ros-pkg
[Catkin workspace]: http://wiki.ros.org/catkin/Tutorials/create_a_workspace
[catkin]: http://wiki.ros.org/catkin
[catkin_tools]: https://catkin-tools.readthedocs.io/en/latest
[Working With ROS-Industrial Robot Support Packages]: http://wiki.ros.org/Industrial/Tutorials/WorkingWithRosIndustrialRobotSupportPackages
[tutorials]: http://wiki.ros.org/motoman_driver/Tutorials
