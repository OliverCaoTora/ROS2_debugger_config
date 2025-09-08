This file shows how to setup vscode debugger for ROS2 cpp

1. install neccessary package
2. create corresponding workspace
3. pkg cmake list can see the sample
4. setting.json example
    add "ros.distro": "humble",
        "ros.rosSetupScript":"${workspaceFolder}/install/setup.zsh"
5. launch file example, if using launch file, a little different
6. colcon build:
'''
colcon build \
    --cmake-args  -DCMAKE_BUILD_TYPE=RelWithDebInfo\
    -Wall -Wextra -Wpedantic \
    -DCMAKE_EXPORT_COMPILE_COMMANDS=ON \
    --symlink-install
'''