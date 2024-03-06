## Miraidon Robot

Miraidon: from the japanese word "mirai" (future) and the sufix "-don" (tooth), used for naming some dinosaurs species. 

In this project, Miraidon will abandon his Pokémon form to become a robot. 

The project is being developed using ROS2: Humble.

All the information and advances of the project can be found in this repository.

### Develeoper station setup
- Install [Ubuntu 22.04](ubunu.com/download/desktop)
- Install ROS2 Humble following the [installation guide](https://docs.ros.org/en/humble/Installation.html)
- Install the required packages running the following commands on a new terminal:
```
sudo apt-get install ros-humble-gazebo-ros
sudo apt-get install ros-humble-gazebo-pkgs
sudo apt-get install ros-humble-xacro
sudo apt-get install ros-humble-joint-state-publisher-gui
sudo apt-get install ros-humble-teleop-twist-keyboard
```
- Install the compilation tool running the following commands on a new terminal:

```
sudo apt update
sudo apt install python3-colcon-common-extensions
```

- Compile the Miraidon project by running the following commands on a new terminal:
```
source /opt/ros/humble/setup.bash
mkdir -p devel_ws/src
cd devel_ws/src
git clone https://github.com/tnacho-23/miraidon_bot.git
cd ..
colcon build --symlink-install
```


#### What can you do?
In the actual state of the project, you are able to launch the simulation of the robot and drive it around in gazebo.


For doing it, you can run the following commands on a new terminal:

```
source /opt/ros/humble/setup.bash
source dev_ws/dev/install/setup.bash
ros2 launch miraidon_bot miraidon_sim.launch.py
```

That should open the simulation. For moving the robot run on a new terminal:

```
source /opt/ros/humble/setup.bash
ros2 run teleop_twist_keyboard teleop_twist_keyboardy 
```
### To Do:
- Raspberrypi setup
- Make it move in the real robot 
- Document all the necesary things to do in the raspberry pi
