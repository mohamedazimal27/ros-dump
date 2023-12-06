# GR-100 Readme

This repository contains instructions and commands for setting up and running the GR-100 navigation and mapping system.

## Stopping Services
To stop the necessary services, run the following command:
```bash
sudo systemctl stop bc-bringup-src@0.service NaviBeeStartup@1.service NaviBeerobotmanager@{1..2}.service
```
To ensure the services have stopped, check their status:
```bash
sudo systemctl status bc-bringup-src@0.service NaviBeeStartup@1.service NaviBeerobotmanager@{1..2}.service
```
## Starting Navigation Mode
To start the system in navigation mode (mode 1), use the command:
```bash
sudo systemctl start bc-bringup-src@1.service
# Note: 0 - Navigation mode, 1 - Mapping mode
```
Check the status of the service to ensure it's running:

```bash
sudo systemctl status bc-bringup-src@1.service
# Ensure that the service is running
```
## ROS Configuration
Open a new terminal and run roscore.
```bash
roscore
```
Then, use the following command to check scanner and map topics:
```bash
rostopic list
# Check for scanner and map topics
```
## Visualization with RViz
Check RViz to visualize the map.
```bash
ssh user@robot_ip  -X # ssh user@192.168.0.10 -X
rviz
```
The map will start publishing automatically. 
The mapping speed is set to 0.15 m/s, and the turbo speed is 0.3 m/s. Don't change this parameter as it is recommended by slam_toolbox
