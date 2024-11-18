.. _build-instructions:

Build and Install
#################

Create the `src` directory if it doesn't already exist.

.. code-block:: console

    mocap4r2_ws$ mkdir src && cd src


OptiTrack System
================

To test the OptiTrack system, follow these steps:

.. note::

    The OptiTrack drivers for ROS2 are based on the NatNet SDK 3.1.0. When building the `mocap4ros2_optitrack` package, the SDK is automatically downloaded and installed.

    Additionally, this package depends on two repositories from the MOCAP4ROS2 project:
    - [mocap_msgs](https://github.com/MOCAP4ROS2-Project/mocap4r2_msgs)
    - [mocap4r2_control](https://github.com/MOCAP4ROS2-Project/mocap)

1. Clone the required repositories:

.. code-block:: console

    mocap4r2_ws/src$ git clone https://github.com/MOCAP4ROS2-Project/mocap4ros2_optitrack.git
    mocap4r2_ws/src$ git clone https://github.com/MOCAP4ROS2-Project/mocap4r2.git
    mocap4r2_ws/src$ git clone https://github.com/MOCAP4ROS2-Project/mocap_interfaces.git

2. Manage ROS2 dependencies:

.. code-block:: console

    mocap4r2_ws/src$ vcs import < mocap4ros2_optitrack/dependency_repos.repos
    rosdep update # May not be needed if already done
    mocap4r2_ws$ cd .. && rosdep install --from-paths src --ignore-src -r -y

3. Build the workspace:

.. code-block:: console

    cd ~/mocap4r2_ws/
    mocap4r2_ws$ colcon build --symlink-install

Configuration
-------------
To configure the system, check and modify the file `config/mocap4ros2_optitrack_driver_params.yaml`. Please remember to update the `host_name` parameter to match the IP address and port of the machine running the OptiTrack system.

Launching
---------
After sourcing the workspace, you can launch the OptiTrack driver with:

.. code-block:: console

    ros2 launch mocap4r2_optitrack_driver optitrack2.launch.py

Since the OptiTrack driver is a lifecycle node, you'll need to activate it after launching:

.. code-block:: console

    ros2 lifecycle set /mocap4r2_optitrack_driver_node activate

Visualization
-------------
To visualize the data, you can use the `rviz2` tool:

.. code-block:: console

    ros2 launch mocap4r2_marker_viz mocap4r2_marker_viz.launch.py mocap4r2_system:=optitrack

Vicon System
============

To test the Vicon system, follow these steps:

.. note::

    The Vicon drivers for ROS2 are based on Vicon DataStream SDK 1.11.0. When building the `mocap4r2_vicon_driver`, the SDK is automatically downloaded and installed.

    Additionally, this package depends on two repositories from the MOCAP4ROS2 project:
    - [mocap4r2_msgs](https://github.com/MOCAP4ROS2-Project/mocap4r2_msgs)
    - [mocap4r2_control](https://github.com/MOCAP4ROS2-Project/mocap)

1. Install the dependencies:

.. code-block:: console

    sudo apt-get install wget git p7zip-full

2. Clone the required repositories:

.. code-block:: console

    mkdir -p ~/mocap4r2_ws/src
    cd ~/mocap4r2_ws/src
    git clone https://github.com/MOCAP4ROS2-Project/mocap4ros2_vicon.git -b rolling
    cp mocap4ros2_vicon/mocap4ros2.rosinstall .rosinstall
    wstool update

3. Manage ROS2 dependencies:

.. code-block:: console

    mocap4r2_ws$ sudo rosdep init  # May not be needed if already done
    rosdep update
    rosdep install --from-paths src --ignore-src -r -y

4. Build the workspace:

.. code-block:: console

    cd ~/mocap4r2_ws/
    colcon build --symlink-install --packages-up-to mocap4r2_vicon_driver


Configuration
-------------

To configure the system, check the file `config/mocap4r2_vicon_driver_params.yaml`. Be sure to update the `host_name` parameter to match the IP address and port of the machine running the Vicon tracker.

Launching
---------

After sourcing the workspace, you can launch the Vicon driver with:

.. code-block:: console

    ros2 launch mocap4r2_vicon_driver mocap4r2_vicon_driver_launch.py

Since the Vicon driver is a lifecycle node, you'll need to activate it after launching:

.. code-block:: console

    ros2 lifecycle set /mocap4r2_vicon_driver_node activate

Visualization
-------------
To visualize the data, you can use the `rviz2` tool:

.. code-block:: console

    ros2 launch mocap4r2_marker_viz mocap4r2_marker_viz.launch.py mocap4r2_system:=vicon