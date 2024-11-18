.. _documentation_home:

*****
|LPN|
*****
.. raw:: html

    <h1 align="center">
      <div>
        <div style="position: relative; padding-bottom: 0%; overflow: hidden; max-width: 100%; height: auto;">
          <iframe width="450" height="300" src="https://www.youtube-nocookie.com/embed/C8DI6OonV7Q" title="YouTube video player" frameborder="0" allow="accelerometer; autoplay; clipboard-write; encrypted-media; gyroscope; picture-in-picture" allowfullscreen></iframe>
          <iframe width="450" height="300" src="https://www.youtube-nocookie.com/embed/Z5kRd4MLgFU" title="YouTube video player" frameborder="0" allow="accelerometer; autoplay; clipboard-write; encrypted-media; gyroscope; picture-in-picture" allowfullscreen></iframe>
        </div>
      </div>
    </h1>

Overview
########

MOCAP4ROS2 is a Focused Technical Project funded initially by ROSIN. Its goal is to standardize the Motion Capture (mocap in short) Systems by providing standard interfaces that any mocap driver should respect when publishing its data and any mocap application could expect. MOCAP4ROS2 also provides tools to monitorize and control one or many mocap system running at the same time.

MOCAP4ROS2 features:
* Support for major mocap vendors: `Vicon <https://github.com/MOCAP4ROS2-Project/mocap4ros2_vicon>`_, `Optitrack <https://github.com/MOCAP4ROS2-Project/mocap4ros2_optitrack>`_, and `Qualisys <https://github.com/MOCAP4ROS2-Project/mocap4ros2_qualisys>`_.
* `Standard interfaces <https://github.com/MOCAP4ROS2-Project/mocap_interfaces>`_ for Motion capture data: Markers and RigidBodies
* `Interfaces for control <https://github.com/MOCAP4ROS2-Project/mocap4r2/tree/rolling/mocap4r2_control/mocap4r2_control_msgs>`_ mocap systems.
* ROS 2 Tools for controlling mocap sytems: `RQT-based GUI <https://github.com/MOCAP4ROS2-Project/mocap4r2/tree/rolling/mocap4r2_control/rqt_mocap4r2_control>`_ and `mocap4r2cli <https://github.com/MOCAP4ROS2-Project/mocap4r2/tree/rolling/mocap4r2cli>`__, a MOCAP4ROS2 extension for `roscli <https://github.com/ros2/ros2cli>`__. 
* `App for visualizing <https://github.com/MOCAP4ROS2-Project/mocap4r2/tree/rolling/mocap4r2_marker_viz>`_ mocap data as visual markers. 
* `App for Groud Truth <https://github.com/MOCAP4ROS2-Project/mocap4r2/tree/rolling/mocap4r2_robot_gt>`_ data for robotic experiments. 
* A `Dummy mocap system <https://github.com/MOCAP4ROS2-Project/mocap4r2/tree/rolling/mocap4r2_dummy_driver>`_ for helping developers to create tools and apps.

To learn more about this project, such as related projects, and maintainers, see :ref:`about`.

We hope that this software helps to include MOCAP in more Robotics projects, offering simple and powerful software to 
generate intelligent behaviors for robots.

We want to invite you to contribute to this `Open Source project in GitHub <https://github.com/MOCAP4ROS2-Project>`_ !!



.. toctree::
   :hidden:

   getting_started/index.rst
   build_instructions/index.rst
   design/index.rst
   tutorials/index.rst
   about/index.rst
   