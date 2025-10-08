This file shows how to setup vscode debugger for ROS2 cpp

1. install neccessary package, like ROS2 "[Robot Developer Extention](https://marketplace.visualstudio.com/items?itemName=Ranch-Hand-Robotics.rde-pack)"
2. create corresponding workspace
3. pkg cmake list can see the sample
4. setting.json example
    add "ros.distro": "humble",
        "ros.rosSetupScript":"${workspaceFolder}/install/setup.zsh"
5. launch file example, if using launch file, a little different
6. colcon build:
    ```
    colcon build \
        --cmake-args  -DCMAKE_BUILD_TYPE=RelWithDebInfo\
        -Wall -Wextra -Wpedantic \
        -DCMAKE_EXPORT_COMPILE_COMMANDS=ON \
        --symlink-install
    ```
8. environment settings:
   Using command to load ros environment at first then start vscode
   ```
   source /opt/ros/humble/setup.zsh(or setup.bash)
   source /（workspace path / (ros package work space path) / install/setup.zsh(or setup.bash)
   code .
   ```
