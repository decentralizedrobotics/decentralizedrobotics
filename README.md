# Decetralized Robotics (DeRo) ![Coming Soon](https://img.shields.io/badge/Coming%20Soon-8A2BE2)
Software and components for secure serverless monitoring and control your ROS 2 based robots using Web 3 technology.

Decentralized Robotics does not replace traditional DDS based ROS 2 communication, but rather augments it with a secure and decentralized cryptographic identity and communication channel using [libp2p](https://libp2p.io) and the [Interplanetary Filesystem](http://ipfs.io).

This project consists of several components:

- `RosWeb3Bridge` – an implementation of the [ROS bridge protocol](https://github.com/RobotWebTools/rosbridge_suite/blob/ros2/ROSBRIDGE_PROTOCOL.md) over libp2p.

- `dero` – a command line interface for provisioning Robots and associating users.

- `dero_web` – a Web Application, hosted on IPFS, for monitoring or controlling your robot using libp2p swarm.

- `ROS2.ts` - a Typescript library for interacting with ROS 2 from a web browser or a node.js application.

- `babylon_ros` - a Typescript library which connects to a ROS 2 bridge using ROS2.ts and renders the robot and UI in 3D and WebXR using Babylon.js.

- `dero_sharp` - a transport for [ROS#](https://github.com/siemens/ros-sharp), which uses [dotnet-libp2p](https://github.com/NethermindEth/dotnet-libp2p). Designed toallow Unity or other C# Applicationsto visualize and control robots without centralized servers. ![Future](https://img.shields.io/badge/Future-8A2BE2)
