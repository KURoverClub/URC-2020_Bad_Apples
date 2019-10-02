# KU Rover Club - Software Intro

##### Varun Chadha . Brian Quiroz
---
## So you want to be an expert at ArduPilot, huh
##### Well strap in, it's going to be a long journey
###### Here is what we will need
* [ArduPilot](http://ardupilot.org/)
* Software in the loop ([SITL](http://ardupilot.org/dev/docs/sitl-simulator-software-in-the-loop.html))
* Ground station software
* [Gazebo](http://gazebosim.org/)
    * [Gazebo Ros Packages](http://gazebosim.org/tutorials?tut=ros_installing&cat=connect_ros)
* Robot Operating System ([ROS](https://www.ros.org/))
* [MavRos](http://wiki.ros.org/mavros) ( Ros package for [MavLink](https://mavlink.io/en/) )
---
# ArduPilot
1. Follow the link for the basic set up [guide](http://ardupilot.org/dev/docs/building-the-code.html) to build the ardupilot source code... They use waf as their build automation tool
    * Choose the link corresponding to your OS
    * Usually you can just get away with running the script they provide to set up all the requirements after cloning the ardupilot repo
    * Once done with running the script execute the two commands found in their [build.md](https://github.com/ArduPilot/ardupilot/blob/master/BUILD.md) ( this is listed in the above documentation, but the link is small so I will post it here too )
    * I recommend double checking that the script added a path to the autotest directory of ardupilot to your bashrc profile.  If it did not, add that as well.
        * export PATH=$PATH:$HOME/ardupilot/Tools/autotest
        * export PATH=/usr/lib/ccache:$PATH
* DO NOT FORGET THAT WHEN YOU UPDATE YOUR BASH PROFILE ALWAYS RESOURCE YOUR ACTIVE TERMINAL SESSION :octocat:

2. Occasionally, you may run into one of the following errors.  Hopefully these will help solve those nasty bugs
    * No command found for sim_vehicle.py
        * I forgot the solution to this... ( I will try and update at a later date )
    * Missing/No such file “mavproxy.py”
        * This most likely occurs when you try and launch sitl with the sim_vehicle.py command and usually caused by missing dependencies, missing path variables, or not resourcing your bash profile.
    * In terms of dependencies, make sure you have the following
        * Mavproxy - install via pip
        * pymavlink - install via pip
        * Sometimes mavproxy is missing a dependency so you can follow the instructions [here](https://ardupilot.github.io/MAVProxy/html/getting_started/download_and_installation.html) to install them
    * Make sure you added the path variables from the previous steps to your bash profile
    * Again, make sure to resource your bash profile
---
# SITL
Software in the loop is the primary way we will simulate ardupilot’s control logic.
* Follow the [link](http://ardupilot.org/dev/docs/sitl-simulator-software-in-the-loop.html#) to set up SITL for your corresponding OS
* You can run SITL from anywhere, if you have your path set up correctly in your bashrc, via the following
```sim_vehicle.py -v ArduRover --map --console```
    * Note: you will not need the -v flag if you are located in the ArduRover subfolder
---
# Ground Station
We will want a ground station to allow for us to communicate with the rover and see sensor readings.
There are multiple options to choose from, but if you are on windows then MissionPlanner is a good choice.  Finding other software should be a trivial google away.
1. Mission Planner ( if on windows ):
    * Do not use this, as ROS is only available on Linux.
    * However, if you do want this, it is useful for visualizing sensor data and quickly setting parameters for ardupilot: http://ardupilot.org/planner/
---
# Gazebo
1. The following [link](http://ardupilot.org/dev/docs/using-gazebo-simulator-with-sitl.html) tells how to install gazebo 9 and how to connect it to sitl
2. I believe we want to install [gazebo_ros_pkgs](http://gazebosim.org/tutorials?tut=ros_installing&cat=connect_ros) to allow for sensors to communicate via MavRos ( which we will install later )
---
# ROS
ROS documentation for ardupilot is helpful, albeit sometimes confusing, and can be found [here](http://ardupilot.org/dev/docs/ros.html)

1. We will install ROS melodic as that is compatible with Ubuntu 18.04
    * The [guide](http://ardupilot.org/dev/docs/ros-install.html) from ardupilot refers to kinetic so just replace kinetic with melodic wherever you see it
---
# MavROS
1. Instructions to install MavRos can also be found from the ros install documentation page from ardupilot [here](http://ardupilot.org/dev/docs/ros-install.html)

---
# Set Up
We will now go through the set up instructions to get ROS working with SITL and Gazebo
1. ROS with SITL:
    * The following [link](http://ardupilot.org/dev/docs/ros-sitl.html) will show you how to launch SITL connected to ROS and communicate between the two
2. ROS with SITL in Gazebo:
    * This seems to be the trickiest thing to set up as no real documentation has been made for it.  Instead, the [documentation](http://ardupilot.org/dev/docs/ros-gazebo.html) references another documentation page that does not help with ROS and an old blog post made back in 2014.
---
# Helpful Links
## SITL
* http://ardupilot.org/dev/docs/using-sitl-for-ardupilot-testing.html
## Mavlink messages
* https://mavlink.io/en/messages/common.html
## Connect with devs
* https://gitter.im/ArduPilot/ardupilot
## Forum discussion board
* https://discuss.ardupilot.org/c/arducopter/copter-simulation

