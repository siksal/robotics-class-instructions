# MoveIt2 Installation and AR4 Robot Arm Setup
This tutorial shows how to install MoveIt2! and configure the AR4 robot URDF and package. You should install ROS 2 Humble before statrting this process.

## MoveIt2! Installation
```sh
sudo apt update
sudo apt upgrade
sudo apt install ros-humble-moveit
```

## Create AR4 package
### Create a workspace
```sh
mkdir -p ar4_ws/src
cd ar4_ws
```
### Build the workspace
```sh
colcon build
```

If colcon build does not work, it's probably not installed.
### Install Colcon and Other ROS tools
```sh
sudo apt install ros-dev-tools
echo "source /usr/share/colcon_argcomplete/hook/colcon-argcomplete.bash" >> ~/.bashrc
```

### Create AR4 robot description package
```sh
cd ~/ar4_ws/src
ros2 pkg create --build-type ament_cmake ar4_description
```

### Add AR4 URDF files
Create URDF and MESH directories
```sh
cd ~/ar4_ws/src/ar4_description
mkdir urdf meshes
```

Visit the PAU learning portal, download the ar4.urdf file and place it in the urdf folder (or directory).
Also download all the mesh files (eg Link1.STL etc) and put them in the meshes folder.

### Source ROS 2 and your AR4 workspace
```sh
echo "source /opt/ros/humble/setup.bash" >> ~/.bashrc
echo "source ~/ar4_ws/install/setup.bash" >> ~/.bashrc
```

### Build your workspace again to reflect changes
```sh
colcon build
```

Close all opened terminals and open a new one to reflect the sourcing of ROS 2 and AR4 workspace.

### Launch the MoveIt2 Setup Assistant
```sh
ros2 launch moveit_setup_assistant setup_assistant.launch.py
```
You should the MoveIt2 Setup Assistant come up as shown below.
![MoveIt2 Setup Assistant](https://github.com/siksal/robotics-class-instructions/blob/main/MoveIt2-AR4/assets/MoveIte2-Setup-Assistant.png)

* Click on Create New MoveIt Configuration Package
* Click the "Browse" button and select your URDF file it's located.

You have successfully loaded a URDF file with MoveIt. Send a screenshot of the MoveIt Setup Assistant that shows the link to your URDF file as shown below.
![MSA](https://github.com/siksal/robotics-class-instructions/blob/main/MoveIt2-AR4/assets/MSA.png)
