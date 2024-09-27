.. _build-instructions:

Build and Install
#################

OptiTrack System
*****************

To test the OptiTrack system, follow these steps:

.. note::

    Create the `src` directory if it doesn't already exist.

    .. code-block:: console

        mocap4ros2_ws$ mkdir src && cd src

1. Clone the required repositories:

.. code-block:: console

    mocap4ros2_ws/src$ git clone https://github.com/MOCAP4ROS2-Project/mocap4ros2_optitrack.git
    mocap4ros2_ws/src$ git clone https://github.com/MOCAP4ROS2-Project/mocap.git
    mocap4ros2_ws/src$ git clone https://github.com/MOCAP4ROS2-Project/mocap_msgs.git

2. Install the dependencies:

.. code-block:: console

    mocap4ros2_ws/src$ vcs import < mocap/dependency_repos.repos
    mocap4ros2_ws$ cd .. && rosdep install --from-paths src --ignore-src -r -y

3. Build the workspace:

.. code-block:: console

    mocap4ros2_ws$ colcon build --symlink-install


Vicon System
************

The following steps will guide you through setting up the Vicon system:


## Installation

### Dependencies:

The Vicon drivers for ROS2 are based on Vicon DataStream SDK 1.11.0. When building the `mocap4r2_vicon_driver`, the SDK is automatically downloaded and installed. The following packages are required for this process:
- `wget`
- `p7zip-full`

Additionally, this package depends on two repositories from the MOCAP4ROS2 project:
- [mocap4r2_msgs](https://github.com/MOCAP4ROS2-Project/mocap4r2_msgs)
- [mocap4r2_control](https://github.com/MOCAP4ROS2-Project/mocap)

A `.rosinstall` file is provided to manage dependencies automatically.

### Installation Steps:

The following commands will install the DataStream SDK, dependencies, and Vicon driver:

.. code-block:: console

    # Install dependencies
    sudo apt-get install wget git p7zip-full 

    # Create workspace
    mkdir -p ~/mocap4r2_ws/src
    cd ~/mocap4r2_ws/src

    # Clone the Vicon repository
    git clone https://github.com/MOCAP4ROS2-Project/mocap4ros2_vicon.git -b rolling

    # Clone the necessary MOCAP repositories
    cp mocap4ros2_vicon/mocap4ros2.rosinstall .rosinstall
    wstool update

    # Manage ROS2 dependencies
    sudo rosdep init  # May not be needed if already done
    rosdep update
    rosdep install --from-paths . --ignore-packages-from-source --rosdistro humble -y

    # Build everything
    cd ~/mocap4r2_ws/
    colcon build --symlink-install --packages-up-to mocap4r2_vicon_driver

### Configuration:

To configure the system, check the file `config/mocap4r2_vicon_driver_params.yaml`. Be sure to update the `host_name` parameter to match the IP address and port of the machine running the Vicon tracker.

### Launching:

After sourcing the workspace, you can launch the Vicon driver with:

.. code-block:: console

    ros2 launch mocap4r2_vicon_driver mocap4r2_vicon_driver_launch.py

Since the Vicon driver is a lifecycle node, you'll need to activate it after launching:

.. code-block:: console

    ros2 lifecycle set /mocap4r2_vicon_driver_node activate

***