# ROS TOOLS

Note: All commands are referred to ubuntu and ROS Jade

## Core

[Installation instructions](http://wiki.ros.org/jade/Installation/UbuntuARM)

- - - -

## Tools

### **Cv_camera**
Read data from camera or file

#### Install:
```bash
sudo apt-get install ros-jade-cv-camera
```
#### Run:
- Run the command:
```bash
rosrun cv_camera cv_camera_node
```
- Use a launch file
```bash
roslaunch <file_name.launch>
```
Example of launch file:
```xml
<launch>
        <node pkg="cv_camera" type="cv_camera_node" name="camera_input">
                <param name="device_id" value="0"/>
        </node>
</launch>
```

### **Rtabmap**
Node for SLAM and more

#### Install:
```bash
sudo apt-get install ros-jade-rtabmap
```

### **Rosserial**
Node that connect a serial device to Ros

#### Use:
Flash the client program on the device, than run the host:
```bash
rosrun rosserial_python serial_node.py </dev/tty...>
```

### **Rostopic**
Tool for topics' management

#### Install:
```bash
sudo apt-get install ros-jade-rostopic
```
#### List all running topics:
```bash
rostopic list
```

### **Topic_tools**
Tools for operations on topics

#### Install:
```bash
sudo apt-get install ros-jade-topic-tools
```
#### Redirect data:
```bash
rosrun topic_tools relay <input_topic> <output_topic>
```

### **Image_view**
Tool for image visualization

#### Install:
```bash
sudo apt-get install ros-jade-image-view
```

#### Run:
```bash
rosrun image_view image_view image:=<topic_name>
```
