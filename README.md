### Report: Installing ROS Noetic and ROS2 Foxy on a MacBook with an i3 Processor

This report details the steps I followed to install and run ROS Noetic and ROS2 Foxy on my MacBook with an i3 processor. The goal was to learn how to set up both versions of ROS and use the `turtlesim` package to control a virtual robot.

#### Tools and Requirements
1. **Operating System**: macOS
2. **Homebrew**: A package manager for macOS
3. **Docker**: For running ROS Noetic
4. **ROS Noetic** (via Docker)
5. **ROS2 Foxy**

### Part 1: Installing ROS Noetic using Docker

#### Steps:

1. **Install Homebrew**:
   I started by installing Homebrew, which simplifies the installation of software on macOS. In the terminal, I ran:
   ```bash
   /bin/bash -c "$(curl -fsSL https://raw.githubusercontent.com/Homebrew/install/HEAD/install.sh)"
   ```

2. **Install Docker**:
   Next, I used Homebrew to install Docker:
   ```bash
   brew install --cask docker
   ```

3. **Start Docker**:
   After installing Docker, I opened it from the Applications folder and ensured it was running.

4. **Pull the ROS Noetic Docker Image**:
   I pulled the ROS Noetic image by running:
   ```bash
   docker pull osrf/ros:noetic-desktop-full
   ```

5. **Run the ROS Noetic Docker Container**:
   I started a new container with the ROS Noetic image:
   ```bash
   docker run -it --rm osrf/ros:noetic-desktop-full
   ```

6. **Install the `turtlesim` Package**:
   Inside the Docker container, I updated the package list and installed `turtlesim`:
   ```bash
   apt-get update
   apt-get install ros-noetic-turtlesim
   ```

7. **Run the `turtlesim` Node**:
   - In the Docker container terminal, I started the ROS core:
     ```bash
     roscore
     ```
   - I opened another terminal within the same Docker container and ran the `turtlesim` node:
     ```bash
     rosrun turtlesim turtlesim_node
     ```

8. **Control the Turtle**:
   - In a new terminal within the Docker container, I ran the teleop key node to control the turtle:
     ```bash
     rosrun turtlesim turtle_teleop_key
     ```
   - I used the arrow keys to control the turtle.

### Part 2: Installing ROS2 Foxy

#### Steps:

1. **Install Homebrew**:
   Since I had already installed Homebrew in the previous steps, I moved on to the next step. If Homebrew wasn’t already installed, I would have run:
   ```bash
   /bin/bash -c "$(curl -fsSL https://raw.githubusercontent.com/Homebrew/install/HEAD/install.sh)"
   ```

2. **Install Dependencies**:
   Using Homebrew, I installed the required dependencies:
   ```bash
   brew install python3 cmake tinyxml2 poco
   ```

3. **Install ROS2 Foxy**:
   I added the ROS2 tap and installed ROS2 Foxy:
   ```bash
   brew tap ros2/ros2
   brew install ros-foxy-desktop
   ```

4. **Source the ROS2 Setup Script**:
   To configure my environment, I sourced the setup script:
   ```bash
   source /opt/ros/foxy/setup.bash
   ```

5. **Install the `turtlesim` Package**:
   Using the ROS2 package manager, I installed `turtlesim`:
   ```bash
   sudo apt update
   sudo apt install ros-foxy-turtlesim
   ```

6. **Run the `turtlesim` Node**:
   - I sourced the ROS2 setup script to ensure the environment was correctly configured:
     ```bash
     source /opt/ros/foxy/setup.bash
     ```
   - I ran the `turtlesim` node:
     ```bash
     ros2 run turtlesim turtlesim_node
     ```

7. **Control the Turtle**:
   - I opened a new terminal, sourced the ROS2 setup script, and ran the teleop key node:
     ```bash
     source /opt/ros/foxy/setup.bash
     ros2 run turtlesim turtle_teleop_key
     ```
   - I used the arrow keys to control the turtle.

### Conclusion

By following these steps, I successfully installed and ran both ROS Noetic and ROS2 Foxy on my MacBook with an i3 processor. Using Docker for ROS Noetic allowed me to bypass the lack of native support on macOS, while ROS2 Foxy was installed directly using Homebrew. I was able to use the `turtlesim` package in both environments to control a virtual turtle, gaining a better understanding of ROS systems and their applications in robotics.


