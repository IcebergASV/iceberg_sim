# iceberg_sim
ROS2 Gazebo simulation package for use with ardupilot_gz and ardupilot_sitl_models packages. This package lets us extend models and worlds in the ardupilot packages for our own purposes.

## Dependancies

Using ros2 humble and Gazebo Garden.

Follow [these instructions](https://app.gitbook.com/o/vtYvioW5qkBb75Erv7gv/s/Ri7hG2C5rQ2UhdgzVUlC/ros2/setting-up-ardupilot-sim) to setup the ardupilot gazebo simulation. You will install all dependancies by following these steps. 

## Install and Build

Navigate to your ros2 workspace src directory:

```
cd ros2_ws/src/
```

Clone the package:
```
git clone git@github.com:IcebergASV/iceberg_sim.git
```

Add the path to the GZ_SIM_RESOURCE_PATH in your bashrc. After setting up the ardupilot packages, your `GZ_SIM_RESOURCE_PATH` should look like this in your bashrc:

```
export GZ_SIM_RESOURCE_PATH=$HOME/ros2_ws/src/ardupilot_gazebo/models:$HOME/ros2_ws/src/ardupilot_gazebo/worlds:$HOME/ros2_ws/src/iceberg_sim/models:$GZ_SIM_RESOURCE_PATH
```
Don't forget to modify the path if your workspace is not in the home directory. 

Build the workspace
```
cd ros2_ws/
colcon build --symlink-install
```
Source the workspace
```
source install/setup.bash
```

## Usage

Launch gazebo:
```
ros2 launch iceberg_sim wildthumper_empty_world.launch.py 
```
Launch mavros:
```
ros2 launch mavros apm.launch
```
Launch MAVProxy:
```
mavproxy.py --console --aircraft test --master=:14550
```

You can now use [MAVProxy](https://ardupilot.org/mavproxy/) to control the robot. 





