# Decentralized Robotics (DeRo) ![Coming Soon](https://img.shields.io/badge/Coming%20Soon-8A2BE2)
Decentralized Robotics is a Ranch Hand Robotics LLC project developing tools, interfaces, and networking components that connect robots and people over traditional and mesh networks. It spans high-bandwidth teleoperation and low-bandwidth telemetry and command and control, including civilian radio stacks such as LoRa and Wi-Fi HaLow.

DeRo is in early development, and setup instructions are evolving. Early access is available to Ranch Hand Robotics LLC sponsors through [GitHub Sponsors](https://github.com/sponsors/ranch-hand-robotics). See [Sponsor early access](docs/About/Support.md#sponsor-early-access) for how sponsors can request access.

Follow [Ranch Hand Robotics LLC on X (@rh_robotics)](https://x.com/rh_robotics).

Decentralized Robotics does not replace traditional DDS based ROS 2 communication, but rather augments it with a secure and decentralized cryptographic identity and communication channel using [libp2p](https://libp2p.io) and the [Interplanetary Filesystem](http://ipfs.io).

This project consists of several components:

- `RosWeb3Bridge` – an implementation of the [ROS bridge protocol](https://github.com/RobotWebTools/rosbridge_suite/blob/ros2/ROSBRIDGE_PROTOCOL.md) over libp2p.

- `dero` – a command line interface for provisioning Robots and associating users.

- `dero_web` – a Web Application, hosted on IPFS, for monitoring or controlling your robot using libp2p swarm.

- `ROS2.ts` - a Typescript library for interacting with ROS 2 from a web browser or a node.js application.

- `babylon_ros` - a Typescript library which connects to a ROS 2 bridge using ROS2.ts and renders the robot and UI in 3D and WebXR using Babylon.js.

## Working on the website

The site uses MkDocs Material with a custom DeRo landing page and a shared Flat Dark Earth theme. The existing documentation and GitHub Pages deployment remain in place.

1. Create and activate a Python virtual environment outside the repository.
2. Install the site dependencies with `python -m pip install -r requirements.txt`.
3. Preview locally with `python -m mkdocs serve` (defaults to `http://127.0.0.1:8000`). Template changes are watched automatically.
4. Validate before publishing with `python -m mkdocs build --strict --site-dir /tmp/dero-site` on Linux, or choose another output directory outside the repository on other platforms.

### Where to edit

- `overrides/home.html`: landing-page content, navigation, network diagram, and calls to action.
- `docs/stylesheets/home.css`: responsive homepage layout and styling, scoped to the custom template.
- `docs/stylesheets/extra.css`: shared documentation colors and responsive video styles.
- `docs/assets/dero-mark.svg` and `docs/assets/rhr-rover.svg`: local vector artwork. The robot illustration follows the supplied Ranch Hand Robotics LLC reference, including its front/top lifting assembly.
- `docs/index.md`: homepage metadata and searchable summary. Keep its heading anchors aligned with the template; YAML front matter must not use tabs.
- `mkdocs.yml`: documentation navigation and theme configuration.

The homepage uses native HTML menus and expandable component details, with no JavaScript required. Fonts and illustrations do not require external services; the embedded introduction video uses YouTube's privacy-enhanced player. Radio diagrams and the rover are conceptual illustrations, not live telemetry or performance claims. Keep the early-development notice visible until the project is ready for wider access.

