# Robot

This guide will walk you through the steps to install the RosWeb3Bridge your robot and to provision it with a routable cryptographic identity and set up user access. Before using this guide, please read the [Concepts](Concepts.md) guide.

## Robot Setup ![Coming Soon](https://img.shields.io/badge/Coming%20Soon-8A2BE2)

> NOTE: This guide represents the ideal flow, not as implemented yet. Please check back later.

=== "Linux"

    ```bash
    # Install Node.js
    curl -s https://deb.nodesource.com/setup_24.x | sudo bash
    sudo apt install -y nodejs

    # Source ROS 2 Humble or later
    source /opt/ros/humble/setup.bash

    :: Provision your Robot
    npm install dero
    dero init

    :: Add an Operator
    dero user add --id user_p2p_address --role administrator

    :: This will output the Robot's p2p address which can be used for discovery.

    npm install rosweb3bridge
    ros2web3bridge
    ```

=== "Windows"

    ```bat
    :: Install Node.js LTS
    winget install nodejs

    :: Install Git
    winget install git

    :: https://docs.ros.org/en/kilted/Installation/Windows-Install-Binary.html

    cd C:\pixi_ws
    pixi shell
    call C:\pixi_ws\ros2-windows\local_setup.bat

    :: Provision your Robot
    npm install dero
    dero init

    :: This will output the Robot's p2p address which can be used for discovery.

    npm install rosweb3bridge
    ros2web3bridge
    ```
