.. _build-instructions:

Build and Install
#################

Optitrack System
*****************

If you want to test the optitrack system, you should follow the following steps:

.. note::

    Create the src directory if you have not created it before

    .. code-block:: console

        mocap4ros2_ws$ mkdir src && cd src

1. Clone the following repositories

.. code-block:: console

    mocap4ros2_ws/src$ git clone https://github.com/MOCAP4ROS2-Project/mocap4ros2_optitrack.git
    mocap4ros2_ws/src$ git clone https://github.com/MOCAP4ROS2-Project/mocap.git
    mocap4ros2_ws/src$ git clone https://github.com/MOCAP4ROS2-Project/mocap_msgs.git

2. Install dependencies

.. code-block:: console

    mocap4ros2_ws/src$ vcs import < mocap/dependency_repos.repos
    mocap4ros2_ws$ cd .. && rosdep install --from-paths src --ignore-src -r -y

3. Build workspace

.. code-block:: console

    mocap4ros2_ws$ colcon build --symlink-install

 
Vicon System
************

To be done

