
# ROS-Dump
Notes and guides for ROS packages

## How to ROS Map

These instructions guide you on how to create a map using ROS (Robot Operating System). Follow these steps to successfully map your environment.

1. **Start ROS System:** Start the ROS system by running the following command. Ensure that Navibee is not running as it may interfere (verify with Shaune regarding Navibee's map input).
    ```bash
    sudo systemctl start gr-startup@0
    ```

2. **Launch LiDAR Sensor:** Launch the LiDAR sensor with the following command:
    ```bash
    roslaunch gr_bringup gr_sick_scan_ncs_combined.launch
    ```

3. **Verify LiDAR Data:** Double-check the LiDAR topic name and ensure that data is being published on this topic and can be read on the PC side.

4. **Configure SLAM Toolbox:** Navigate to the "slam_toolbox" package using the following command:
    ```bash
    roscd slam_toolbox
    ```
    Go to the "config" folder and open the YAML file for the launch file you intend to use. Update the LiDAR scan topic to the correct value. By default, it may be "/scan," but for our purposes, you may need to rename it to "/lidar/scan."

5. **Launch SLAM Toolbox:** Launch the slam_toolbox with the appropriate launch file. You can choose from options like "lifelong.launch," "online_async.launch," etc. Replace `(launch file name)` with your chosen launch file.
    ```bash
    roslaunch slam_toolbox (launch file name).launch
    ```

6. **Set Up RVIZ:** Open RVIZ on your laptop. Ensure that the fixed frame is set to "odom" or "map" and that the LaserScan topic is free from errors. Avoid using "/base_link" as the fixed frame, as it moves with the robot.

7. **Visualize the Map:** Check that the "/map" topic is being published by "/slam_toolbox" and can be visualized in RViz.

8. **Update and Save the Map:** Move the robot around and observe the map updating. Once you are satisfied with the map, you can save it using the following command. Replace `<map_name>` with your desired map name.
    ```bash
    rosrun map_server map_saver -f <map_name>
    ```

9. **Edit the Map (Optional):** For further map editing, you can use GIMP or other image editing tools.

Ensure you have the necessary permissions and configurations set up in your ROS environment before executing these commands.
