# Installing ROS Noetic on Ubuntu

## Prerequisites

Before installing ROS Noetic, ensure that you have:
- **Ubuntu 20.04 (Focal Fossa)** installed.
- A **non-root user** with `sudo` privileges.
- An **internet connection**.

## Step 1: Set Up Sources and Keys

1. Configure your system to allow packages from `packages.ros.org`:
   ```sh
   sudo apt update
   sudo apt install curl
   curl -sSL 'http://repo.ros2.org/repos.key' | sudo apt-key add -
   sudo sh -c 'echo "deb http://packages.ros.org/ros/ubuntu $(lsb_release -sc) main" > /etc/apt/sources.list.d/ros-latest.list'
   ```
2. Update the package index:
   ```sh
   sudo apt update
   ```

## Step 2: Install ROS Noetic

### Option 1: Install Full Desktop Version

This includes ROS, Rviz, demos, and navigation tools.
```sh
sudo apt install ros-noetic-desktop-full
```

### Option 2: Install Basic ROS

If you want only the base packages without extra tools:
```sh
sudo apt install ros-noetic-ros-base
```

## Step 3: Initialize `rosdep`

`rosdep` allows you to install dependencies easily.

```sh
sudo apt install python3-rosdep
sudo rosdep init
rosdep update
```

## Step 4: Set Up Environment Variables

Add the following to your `~/.bashrc` to set up your ROS environment automatically:
```sh
echo "source /opt/ros/noetic/setup.bash" >> ~/.bashrc
source ~/.bashrc
```

If using `zsh`, replace `~/.bashrc` with `~/.zshrc`.

## Step 5: Install Dependencies for Building Packages

```sh
sudo apt install python3-rosinstall python3-rosinstall-generator python3-wstool build-essential
```

## Step 6: Verify Installation

Run the following command to check if ROS is installed:
```sh
roscore
```
If ROS is installed correctly, you should see output confirming that `roscore` is running.

## Next Steps
- Learn ROS commands: `roscd`, `rosls`, `rostopic`
- Create a ROS workspace: [Official Guide](http://wiki.ros.org/ROS/Tutorials/InstallingandConfiguringROSEnvironment)

---

For more details, visit the [ROS Noetic Wiki](http://wiki.ros.org/noetic/Installation/Ubuntu).
