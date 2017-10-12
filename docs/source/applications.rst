.. _chapter_applications:

Applications
============

This chapter shows some demos using Turtlebot3.
In order to implement these demos, you have to install the turtlebot3_applications package.

.. NOTE:: Turtlebot3 has been tested on ``Ubuntu 16.04`` and ``ROS Kinetic Kame``.

.. TIP:: The terminal application can be found with the Ubuntu search icon on the top left corner of the screen. Shortcut key for terminal is Ctrl-Alt-T.

[``Remote PC``] Go to ROS source directory (/home/<user_name>/catkin_ws/src) and clone the turtlebot3_applications repository.

.. code-block:: bash

  cd ~/catkin_ws/src
  git clone https://github.com/ROBOTIS-GIT/turtlebot3_applications.git

[``Remote PC``] catkin_make to install the new package.

.. code-block:: bash

 cd ~/catkin_ws && catkin_make


TurtleBot Follower Demo
-----------------------

.. NOTE:: The follower demo was implemented only using a 360 Laser Distance Sensor LDS-01. a classification algorithm is used based on previous fitting with samples of person and obstacles positions to take actions. It follows someone in front of the robot within a 50 centimeter range and 140 degrees.

.. NOTE:: Running the follower demo in an area with obstacles may not work well. Therefore, it is recommended to run the demo in an open area without obstacles.

[``TurtleBot``] In order to run the demo, parameter in LIDAR launch file has to be modified. In the below example, Pluma is used to edit the launch file. In the param tag with frame_id as a name, replace `base_scan` to `odom` and save the file as shown in the below images.

.. code-block:: bash

  pluma ~/catkin_ws/src/turtlebot3/turtlebot3_bringup/launch/turtlebot3_lidar.launch
  
  
.. image:: _static/application/base_scan.png


.. image:: _static/application/odom.png


.. NOTE::  Turtlebot Follower Demo requires scikit-learn, NumPy and ScyPy packages. 

[``Remote PC``] Install scikit-learn, NumPy and ScyPy packages with below commands.

.. code-block:: bash

  sudo apt-get install python-pip
  sudo pip install -U scikit-learn numpy scipy
  sudo pip install --upgrade pip

[``Remote PC``] When installation is completed, run roscore on the remote pc with below command.

.. code-block:: bash

  roscore
  
[``TurtleBot``] Launch the Turtlebot3_bringup

.. code-block:: bash

  roslaunch turtlebot3_bringup turtlebot3_robot.launch

[``Remote PC``] Move to turtlebot3_follower source directory 

.. code-block:: bash

  cd ~/catkin_ws/src/turtlebot3_applications/turtlebot3_follower/src

[``Remote PC``] Launch turtlebot3_follow_filter with below command.
  
.. code-block:: bash

  roslaunch turtlebot3_follow_filter turtlebot3_follow_filter.launch
    
[``Remote PC``] Launch turtlebot3_follower with below command.

.. code-block:: bash

  rosrun turtlebot3_follower follower.py
  
.. raw:: html

  <iframe width="560" height="315" src="https://www.youtube.com/embed/w9YTxZVY6yQ" frameborder="0" allowfullscreen></iframe>
  
  
  
TurtleBot Panorama Demo Using Raspberry Pi Camera Module
--------------------------------------------------------

.. NOTE:: The turtlebot3_panorama demo uses pano_ros for taking snapshots and stitching them together to create panoramic image.
.. NOTE:: Panorama demo requires to install Raspicam package. Instructions for installing this package can be found at https://github.com/UbiquityRobotics/raspicam_node
.. NOTE:: Panorama demo requires to install OpenCV and cvbridge packages. Instructions for installing OpenCV can be found at http://docs.opencv.org/2.4/doc/tutorials/introduction/linux_install/linux_install.html

[``TurtleBot``] Launch the Raspberry Pi cam V2

.. code-block:: bash

  roslaunch raspicam_node camerav2_1280x960.launch

[``Remote PC``] Launch Panorama with below command.

.. code-block:: bash

  roslaunch turtlebot3_panorama panorama.launch

[``Remote PC``] To start the panorama demo, please enter below command.

.. code-block:: bash

  rosservice call turtlebot3_panorama/take_pano 0 360.0 30.0 0.3


Parameters that can be sent to the rosservice to get a panoramic image are:

- mode for taking the pictures.
    0 : snap&rotate (i.e. rotate, stop, snapshot, rotate, stop, snapshot, ...)  
    1 : continuous (i.e. keep rotating while taking snapshots)  
    2 : stop taking pictures and create panoramic image  
- total angle of panoramic image, in degrees
- angle interval (in degrees) when creating the panoramic image in snap&rotate mode, time interval (in seconds) otherwise
- rotating velocity (in radians/s)


[``Remote PC``] To view the result image, please enter below command.

.. code-block:: bash

  rqt_image_view image:=/turtlebot3_panorama/panorama


.. image:: _static/application/panorama_view.png

Automatic Docking
-----------------

(TODO)
