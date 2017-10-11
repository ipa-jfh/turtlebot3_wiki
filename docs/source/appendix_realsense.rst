.. _appendix_realsense:

Appendix #RealSense™
==============

.. image:: _static/appendix/realsense/realsense_r200.png

Overview
--------

`Intel® RealSense™`_ is a platform for implementing gesture-based human-computer interaction techniques. It consists of series of consumer grade 3D cameras together with an easy to use machine perception library. The Intel® RealSense™ R200 camera is a USB 3.0 device that can provide color, depth, and infrared video streams. The TurtleBot3 Waffle model adopts Intel® RealSense™ R200 to enable 3D SLAM and navigation, and it is possible to apply various applications such as gesture recognition, object recognition and scene recognition based on 3D depth information obtained using RealSense™'s innovative Active Stereo Technology.

Specifications
--------------

Technical Specifications
~~~~~~~~~~~~~~~~~~~~~~~~

+--------------------------+--------------------------------------------------------------------+
| Items                    | Specifications                                                     |
+==========================+====================================================================+
| RGB Video Resolution     | 1920 x 1280, 2M                                                    |
+--------------------------+--------------------------------------------------------------------+
| IR Depth Resolution      | 640 x 480, VGA                                                     |
+--------------------------+--------------------------------------------------------------------+
| Laser Projector          | Class 1 IR Laser Projector (IEC 60825-1:2007 Edition 2)            |
+--------------------------+--------------------------------------------------------------------+
| Frame Rate               | 30 fps (RGB), 60 fps (IR depth)                                    |
+--------------------------+--------------------------------------------------------------------+
| FOV (Field-of-View)      | 77° (RGB), 70° (IR depth), Diagonal Field of View                  |
+--------------------------+--------------------------------------------------------------------+
| Range                    | 0.3m ~ 4.0m                                                        |
+--------------------------+--------------------------------------------------------------------+
| Operating Supply Voltage | 5V (via USB port)                                                  |
+--------------------------+--------------------------------------------------------------------+
| USB Port                 | USB 3.0                                                            |
+--------------------------+--------------------------------------------------------------------+
| Dimensions               | 101.56mm length x 9.55mm height x 3.8mm width                      |
+--------------------------+--------------------------------------------------------------------+
| Mass                     | Under 35g                                                          |
+--------------------------+--------------------------------------------------------------------+

Minimum System Requirements
~~~~~~~~~~~~~~~~~~~~~~~~~~~

+--------------------------+--------------------------------------------------------------------+
| Items                    | Specifications                                                     |
+==========================+====================================================================+
| Processors               | 4th Generation and future Intel® Core™ processors                  |
+--------------------------+--------------------------------------------------------------------+
| Disk Storage             | 1GB                                                                |
+--------------------------+--------------------------------------------------------------------+
| Memory                   | 2GB                                                                |
+--------------------------+--------------------------------------------------------------------+
| Interface                | USB 3.0                                                            |
+--------------------------+--------------------------------------------------------------------+
|                          | Ubuntu 14.04 and 16.04 LTS (GCC 4.9 toolchain)                     |
+                          +--------------------------------------------------------------------+
| Operating System         | Windows 8.1 and Windows 10 (Visual Studio 2015 Update 2)           |
+                          +--------------------------------------------------------------------+
| for SDK                  | Mac OS X 10.7+ (Clang toolchain)                                   |
+                          +--------------------------------------------------------------------+
|                          | Ostro                                                              |
+--------------------------+--------------------------------------------------------------------+

Here is the detail specification document: `Intel® RealSense™ Datasheet`_

Intel® RealSense™ R200 for TurtleBot3
-----------------

The Intel® RealSense™ R200 is applied on TurtleBot3 Waffle.

.. image:: _static/hardware/turtlebot3_models.png

Introduction Video
------------------

The TurtleBot3 Waffle uses Intel® RealSense™ Camera R200 as a default vision sensor. Check this video out that shows how Intel® RealSense™ Camera R200 can be used in TurtleBot3 Waffle.

.. raw:: html

  <iframe width="640" height="360" src="https://www.youtube.com/embed/V8VJUkWWaO8?ecver=1" frameborder="0" allowfullscreen></iframe>

|

User Guide
----------

`Intel® RealSense™ packages`_ enable the use of Intel® RealSense™ R200, F200, SR300 and ZR300 cameras with ROS. Below table describes packages required to operate Intel® RealSense™. You will be guided to install these packaged in the next section.

+---------------------+---------------------------------------------------------------------------+
| Package             | Description                                                               |
+=====================+===========================================================================+
| `librealsense`_     | Underlying library driver for communicating with Intel® RealSense™ camera |
+---------------------+---------------------------------------------------------------------------+
| `realsense_camera`_ | ROS Intel® RealSense™ camera node for publishing camera                   |
+---------------------+---------------------------------------------------------------------------+

Installation
~~~~~~~~~~~~

.. WARNING::

  There are installation prerequisites for the Intel® RealSense™ package installation in http://wiki.ros.org/librealsense

The following commands will install relevant Intel® RealSense™ packages on your ROS system.

.. code-block:: bash

  sudo apt-get install linux-headers-generic
  sudo apt-get install ros-kinetic-librealsense
  sudo apt-get install ros-kinetic-realsense-camera

Run realsense_camera node
~~~~~~~~~~~~~~~~~~~~~~~~~

.. code-block:: bash

  roslaunch realsense_camera r200_nodelet_default.launch

While the realsense_camera node is running, you can view various data from Intel® RealSense™ by launching rqt_image_view.

.. code-block:: bash

  rqt_image_view

Once the gui application is appeared on the screen, you can select data topic name related to Intel® RealSense™ from drop down menu at the top of the application.

References
----------

- Intel® RealSense™ Datasheet https://software.intel.com/sites/default/files/managed/d7/a9/realsense-camera-r200-product-datasheet.pdf
- Data ranges https://software.intel.com/en-us/articles/intel-realsense-data-ranges
- Intel® RealSense™ SDK https://software.intel.com/en-us/intel-realsense-sdk
- Purchase https://click.intel.com/realsense.html

.. _Intel® RealSense™: https://click.intel.com/realsense.html
.. _https://software.intel.com/sites/default/files/managed/d7/a9/realsense-camera-r200-product-datasheet.pdf
.. _Intel® RealSense™ packages: http://wiki.ros.org/RealSense
.. _librealsense: http://wiki.ros.org/librealsense
.. _realsense_camera: http://wiki.ros.org/realsense_camera
.. _Intel® RealSense™ Datasheet: https://software.intel.com/sites/default/files/managed/d7/a9/realsense-camera-r200-product-datasheet.pdf
