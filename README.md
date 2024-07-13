# What is ROS2 ?
ROS2 (Robot Operating System 2) is the next generation of ROS, Open source, active community, and a flexible framework for writing robot software. It is designed to address the limitations of ROS1, particularly in terms of performance, security, and scalability. <br> 

The key differencies between ROS and ROS2: <br>

<img src= "https://github.com/user-attachments/assets/f2226529-32e5-449e-a584-fda7870a1b40" alt= "image" width= 600>

# Why ROS2?
instead of building simple applications on Arduino that will make a big confusion for the builder to handle so many servos and microcontrollers, the ROS2 is there exists to deal with all of these complex applications and make them easier to understand and implement. 

# Checking the ROS2 Distribution

from this [link](https://docs.ros.org/en/rolling/Releases.html) double-check on the ROS2 version you should use and the compatibilities with the operating sytem you have. Since I have Ubunto 20.04, the compatible ROS2 is [Foxy Fitzroy](https://docs.ros.org/en/rolling/Releases/Release-Foxy-Fitzroy.html)

<img src= "https://github.com/user-attachments/assets/cff036e1-2584-49e4-bff5-8847e5d6a6d4" alt= "image" width= 400>

# Install ROS2 
To install ROS2, open this [link](https://docs.ros.org/en/foxy/Installation/Ubuntu-Install-Debians.html)

I will show you here the output for each step:

## Set local 
```
locale  # check for UTF-8

sudo apt update && sudo apt install locales
sudo locale-gen en_US en_US.UTF-8
sudo update-locale LC_ALL=en_US.UTF-8 LANG=en_US.UTF-8
export LANG=en_US.UTF-8

locale  # verify settings
```
<img src= "https://github.com/user-attachments/assets/d7b48e76-0694-4c32-b476-e8bfdece4886" alt= "image" width= 400>

## Setup Sources
- You will need to add the ROS 2 apt repository to your system. <br>
- First ensure that the Ubuntu Universe repository is enabled. <br>
```
sudo apt install software-properties-common
sudo add-apt-repository universe
```
<img src= "https://github.com/user-attachments/assets/9d69851e-44a7-47cf-9214-af117b73a5f0" alt= "image" width= 400> <br>
- Now add the ROS 2 GPG key with apt.<br>

```
sudo apt update && sudo apt install curl -y
sudo curl -sSL https://raw.githubusercontent.com/ros/rosdistro/master/ros.key -o /usr/share/keyrings/ros-archive-keyring.gpg
```
<img src= "https://github.com/user-attachments/assets/36b3795f-494a-4377-bb68-55e31f179990" alt= "image" width= 400>

- Then add the repository to your sources list. <br>

```
echo "deb [arch=$(dpkg --print-architecture) signed-by=/usr/share/keyrings/ros-archive-keyring.gpg] http://packages.ros.org/ros2/ubuntu $(. /etc/os-release && echo $UBUNTU_CODENAME) main" | sudo tee /etc/apt/sources.list.d/ros2.list > /dev/null
```

<img src= "https://github.com/user-attachments/assets/3b5d8a33-6969-4e68-9a9d-884e00f08626" alt= "image" width= 400>

## Install ROS2 packages
- https://github.com/user-attachments/assets/3b5d8a33-6969-4e68-9a9d-884e00f08626
```
sudo apt update
```
- ROS 2 packages are built on frequently updated Ubuntu systems. It is always recommended that you ensure your system is up to date before installing new packages.

```
sudo apt upgrade
```

- ROS-Base Install (Bare Bones): Communication libraries, message packages, command line tools. No GUI tools.
```
sudo apt install ros-foxy-desktop python3-argcomplete
```
> [!NOTE]
> This will take time.

<img src= "https://github.com/user-attachments/assets/1db6d731-97ad-41a2-afc6-5fae79943d3e" alt= "image" width= 400>

- Development tools: Compilers and other tools to build ROS packages
```
sudo apt install ros-dev-tools
```
<img src= "https://github.com/user-attachments/assets/5d19e271-34a3-4d9d-92db-bed04b41648f" alt= "image" width= 400>

## Environment Setup

- Set up your environment by sourcing the following file.

```
# Replace ".bash" with your shell if you're not using bash
# Possible values are: setup.bash, setup.sh, setup.zsh
source /opt/ros/foxy/setup.bash
```

<img src= "https://github.com/user-attachments/assets/b52770f5-271a-4061-b56d-afc042db0019" alt= "image" width= 400>

## Try some examples 

The provided commands demonstrate a basic example of inter-process communication in ROS 2 (Robot Operating System 2) using the talker and listener nodes. These nodes are implemented in both C++ and Python, showing the flexibility of ROS 2 in supporting multiple programming languages. <br>

- If you installed ros-foxy-desktop above you can try some examples.

- In one terminal, source the setup file and then run a C++ talker:

```
source /opt/ros/foxy/setup.bash
ros2 run demo_nodes_cpp talker
```

- The talker node continuously publishes messages with incrementing numbers.
- Each message is prefixed with "Hello World:" followed by a unique integer.

------------------------------------------------------------------------------------------

- In another terminal source the setup file and then run a Python listener:
```
source /opt/ros/foxy/setup.bash
ros2 run demo_nodes_py listener
```
- The listener node receives and prints the messages published by the talker.
- Each received message is prefixed with "I heard:" followed by the content of the message.

> [!NOTE]
> You should see the talker saying that it’s Publishing messages and the listener saying I heard those messages. This verifies both the C++ and Python APIs are working properly. Hooray!

**output:**

<img src= "https://github.com/user-attachments/assets/56787c34-752f-4c35-95be-a5380d7005ab" alt= "image" width= 400>

> [!NOTE]
> This won't stop unless you typed ctr + c.



















