
This guide will walk you through the steps to install the RosWeb3Bridge your robot and to provision it with a routable cryptographic identity and set up user access. Before using this guide, please read the [Concepts](Concepts.md) guide.


## Robot Setup
=== "Linux"

    ```bash
    # Install Node.js 18.x
    curl -s https://deb.nodesource.com/setup_18.x | sudo bash
    sudo apt install -y nodejs

    # Source ROS 2 Humble
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
    :: Install Chocolatey
    @powershell -NoProfile -ExecutionPolicy Bypass -Command "iex ((New-Object System.Net.WebClient).DownloadString('https://community.chocolatey.org/install.ps1'))" && SET "PATH=%PATH%;%ALLUSERSPROFILE%\chocolatey\bin"

    :: Install Node.js 18.x
    choco install nodejs-lts

    :: Install Git
    choco install git

    :: Source ROS 2 Humble
    call C:\opt\ros\humble\x64\setup.bat

    :: Provision your Robot
    npm install dero
    dero init

    :: This will output the Robot's p2p address which can be used for discovery.

    npm install rosweb3bridge
    ros2web3bridge
    ```
