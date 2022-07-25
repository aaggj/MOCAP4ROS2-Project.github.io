.. _build-instructions:

Build and Install
#################

Optitrack System
*****************
Installation
------------
1. Install the ROS 2 binary packages as described in the official docs
2. Create workspace

   .. code-block:: bash
   
      mkdir -p ~/mocap_ws/src
      cd ~/mocap_ws/src
      
3. Download: the repo:

   .. code-block:: bash
   
      git clone --recursive https://github.com/MOCAP4ROS2-Project/mocap4ros2_optitrack.git
      
4. Resolve dependencies:

   .. code-block:: bash
   
      vcs import < mocap4ros2_optitrack/dependency_repos.repos
      
Simulation
----------
          
1. Install the Turtlebot 3 packages:

   .. code-block:: bash

      sudo apt install ros-<ros2-distro>-turtlebot3*
      
2. Download: the repo:

   .. code-block:: bash
   
      git clone --recursive https://github.com/MOCAP4ROS2-Project/mocap4ros2_gazebo.git
      
Running simulation example
--------------------------

1. Start a terminal in your GUI
2. Set key environment variables:

   .. code-block:: bash

      source /opt/ros/<ros2-distro>/setup.bash
      export TURTLEBOT3_MODEL=waffle
      export GAZEBO_MODEL_PATH=$GAZEBO_MODEL_PATH:/opt/ros/<ros2-distro>/share/turtlebot3_gazebo/models
      export GAZEBO_MODEL_PATH=$GAZEBO_MODEL_PATH:~/mocap_ws/install/gazebo_mocap_plugin/share/gazebo_mocap_plugin/models/
      
3. In the same terminal, run

   .. code-block:: bash

      ros2 launch gazebo_mocap_plugin tb3_simulation_launch.py
   
4. Open gzclient in other terminal (to-do: still not work fine)
 
 
 
Vicon System
************

To be done

