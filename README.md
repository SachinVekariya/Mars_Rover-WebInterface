# Mars_Rover-Web_Interface

Mars Rover provides an interface to operate ROS (Robot Operating System) based Bot from Website. Interface provides two operating mode Autonomous and Manual Control along with status of Bot in form of Visual Feed and Sensor Data.

<img src="/Mars_Rover_Home_Page.png">


## User Guide

### Navigation Bar
* Home Page <br/> Interface to operate Bot from Web.
* About <br/> Guide to Operate Bot using this Web Interface.
* Contact <br/> You can give your valuable suggestion.

### Sidebar
* Server <br/> Launch WebSocket Server on your Local Machine which is responsible for connection between Local Machine and Web Interface. It also updates the connection status between server and Web Interface. For more details visit <a href="https://github.com/RobotWebTools/rosbridge_suite" target="_blank">RobotWebTools</a>.

* Roscore <br/> Run Roscore on your Local Machine and update the status of it.

* Gazebo <br/> Launch Gazebo which is simulation software and load <a                             href="https://github.com/SachinVekariya/Autonomous_Bot/tree/main/bot/urdf" target="_blanl">Robot model</a> into Gazebo on Local Machine. It also Publish various sensors data which are mounted on Bot.

* Mapviz <br/> Launch <a href="http://wiki.ros.org/mapviz" target="_blank">Mapviz</a> which is ROS based visualization tool.

### Gazebo Video Feed
It provides video feed from Camera which is mounted on Bot (Inside Gazebo). In backend, it runs <a href="http://wiki.ros.org/mjpeg_server" target="_target">MJPEG Server</a> on your Local Machine and Load image on Web Interface.

### Task Selection
Default task is Manual Control which you can control from Manual Control and you can switch to Autonomous Control by Activating Switch.

### Status

* Imu <br/> Subscribe imu/data topic and then convert Quaternion to Euler Angle and shows yaw angle with respect to North Direction in Degree (0 to 360).
* GPS <br/> Subscribe /gps_fix topic and show latitude and longitude.
* Speed <br/> It shows the speed of bot in terms of Linear and Angular Velocity.
* Autonomous <br/> It provides the Status of Autonomous Controller like Current goal, Distance from Destination and Bot current operation - Goal to Goal / Obstacle Avoidance.

### Manual Control

* Button <br/> It can control bot with set of buttons. Button W for forward, S for backward, A for left, D for right and center button for Stop.
* Keyboard <br/> It can control bot with keyboard. Key W for forward, S for backward, A for left, D for right and Spacebar button for Stop.
<br/>
Button/Keyboard Control is disabled on Autonomous Mode.

### Autonomous Control
To operate in Autonomous Mode, we need to provide information about Bot route like Number of Goal and Coordinates of them.Then, you can start Autonomous mode by pressing Start button with task Switch in Autonomous.


## SetUp - ROS 

*Tested on Ubuntu 20.04 and Ros-Noetic.

Install Ros version according to your Ubuntu Version.
<br>
<a href="http://wiki.ros.org/melodic/Installation/Ubuntu">Ros-Melodic</a> for Ubuntu 18.04 & <a href="http://wiki.ros.org/noetic/Installation/Ubuntu">Ros-Noetic</a> for Ubuntu 20.04
<br>

Install ROS Packages <br>
* sudo apt-get install ros-noetic-rosbridge-server <br>
* sudo apt-get install ros-noetic-rosbridge-suite <br>

Install ROS packages inside the ROS workspace <br>
* git clone https://github.com/RobotWebTools/mjpeg_server.git <br> (Change CV_IMWRITE_JPEG_QUALITY to cv::IMWRITE_JPEG_QUALITY if get error while catkin_make)
* git clone https://github.com/SachinVekariya/Autonomous_Bot.git <br>
Dont't forget to add "source ~/Your_WorkSpace_Name/devel/setup.bash" in ~/.bashrc

## SetUp - Web

* <a href="https://www.digitalocean.com/community/tutorials/how-to-install-node-js-on-ubuntu-20-04" >Install</a> Nodejs (Version > 15.0.0)
* $ git clone https://github.com/SachinVekariya/Mars_Rover-WebInterface.git
* $ cd Mars_Rover-WebInterface/WebGUI/
* $ npm i
* $ node app.js <br>

Open your favourite broswer and search http://localhost:3000/ and Now your Web Interface is ready to control Bot.
