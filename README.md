## Miraidon Robot

Miraidon: from the japanese word "mirai" (future) and the sufix "-don" (tooth), used for naming some dinosaurs species. 

In this project, Miraidon will abandon his Pokémon form to become a robot. 

The project is being developed using ROS2: Humble.

All the information and advances of the project can be found in this repository.

### Develeoper station setup
- Install [Ubuntu 22.04](ubunu.com/download/desktop).
- Install ROS2 Humble following the [installation guide](https://docs.ros.org/en/humble/Installation.html).
- Install the required packages running the following commands on a new terminal:
```
sudo apt update
sudo apt install git
sudo apt install ros-humble-gazebo-ros
sudo apt install ros-humble-gazebo-pkgs
sudo apt install ros-humble-gazebo-plugins
sudo apt install ros-humble-xacro
sudo apt install ros-humble-joint-state-publisher-gui
sudo apt install ros-humble-teleop-twist-keyboard
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
source devel_ws/install/setup.bash
ros2 launch miraidon_bot miraidon_sim.launch.py
```

That should open the simulation. For moving the robot run on a new terminal:

```
source /opt/ros/humble/setup.bash
ros2 run teleop_twist_keyboard teleop_twist_keyboardy 
```
### RaspberryPi setup

In this section, we are going to set up and install all the necesary in the computer that is going to be mounted on the robot. In this case, the selected computer is a Raspberry Pi 4 with 8gb if RAM.

On the first place, flash a microSD card with the newest version of Ubuntu Mate 22 raspberry version. You can find it [here](https://ubuntu-mate.org/raspberry-pi/).

Once flashed, connect your microSD card to the device and plug it to start the first boot. Just follow the on-screen instructions. 

You can choose any name and password you want for the device , but in this case, we will use the followings:

```
User name: miraidon
Device name: miraidon-pi
password: miraidon
```

#### RaspberryPi configuration
- Install ROS2 Humble following the [installation guide](https://docs.ros.org/en/humble/Installation.html).
- Install the required packages running the following commands on a new terminal:
```
sudo apt update
sudo apt install git
sudo apt install openssh-server
```
##### SSH configuration
For accessing the device remotely, it is necessary to set up the ssh:
- On a new terminal type
`sudo raspi-config`. Then go to interface options and enable ssh.

- On another terminal, type `sudo systemctl status ssh` and make sure that SSH is active.

- Finally, on another terminal type: `sudo ufw allow ssh`

- Now, on your developer machine, as long as both machines are connected to the same network, you can type:
```
ssh miraidon@miraidon-pi.local
```
And you will be able to access to your Raspberry remotely. In case it doesn't work, replace the `miraidon-pi.local` for your machine IP. You can get it by typing `hostname -I`.

### To Do:
- Make it move in the real robot 
- Document all the necesary things to do in the raspberry pi

