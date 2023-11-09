This page decsribes a way to quickly establish a libp2p connection between a computer and your robot using an SSH tunnel. 
You can route DDS Router traffic over this tunnel to connect to your robot's DDS network, or use the Visual Studio Code ROS Extension to remotely debug your robot.

> NOTE: The IPFS Swarm stream used below is considered experimental, pending more documentation and testing. 

=== "Robot Setup"

    === "Linux"

        (If you are on Jetson or Raspberry Pi, replace amd64 below with arm64)
        ```bash
        wget https://dist.ipfs.tech/kubo/v0.24.0/kubo_v0.24.0_linux-amd64.tar.gz
        tar -xvzf kubo_v0.24.0_linux-amd64.tar.gz
        cd kubo
        sudo bash install.sh
        ipfs init
        ```
        Take node of the `peer identity:`. This is the 'routable cryptographic address' of your robot. You will need this to connect to your robot through the swarm.

        ```bash

        ipfs config --json Swarm.RelayClient.Enabled true
        ipfs config --json Experimental.Libp2pStreamMounting true

        ipfs daemon
        ```

        In another terminal window, configure the Stream Listener, which forwards from the `/x/ssh` protocol to the local SSH server. (The protocol name `/x/ssh` is arbitrary, but must be the same on the robot and clients):
    
        ```bash
        ipfs p2p listen /x/ssh /ip4/127.0.0.1/tcp/22
        ```

    === "Windows"

        ```powershell
        wget https://dist.ipfs.tech/kubo/v0.24.0/kubo_v0.24.0_windows-amd64.zip -Outfile kubo_v0.24.0.zip
        Expand-Archive -Path kubo_v0.24.0.zip -DestinationPath C:\opt\kubo
        C:\opt\kubo\ipfs init

        ```
        Take node of the `peer identity: 12D3XXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXX`. This is the 'routable cryptographic address' of your robot. You will need this to connect to your robot through the swarm.

        ```powershell
        ipfs config --json Swarm.RelayClient.Enabled true
        ipfs config --json Experimental.Libp2pStreamMounting true

        ipfs daemon
        ```

        In another terminal window, configure the Stream Listener, which forwards from the `/x/ssh` protocol to the local SSH server. (The protocol name `/x/ssh` is arbitrary, but must be the same on the robot and clients):

        ```powershell
        ipfs p2p listen /x/ssh /ip4/127.0.0.1/tcp/22
        ```

=== "Client Setup"
    Recall the `peer identity` of your robot from the setting up the robot. You will need this to connect to your robot through the swarm.

    === "Linux"

        (If you are on Jetson or Raspberry Pi, replace amd64 below with arm64)
        ```bash
        wget https://dist.ipfs.tech/kubo/v0.24.0/kubo_v0.24.0_linux-amd64.tar.gz
        tar -xvzf kubo_v0.24.0_linux-amd64.tar.gz
        cd kubo
        sudo bash install.sh
        ipfs init
        ```

        ```bash

        ipfs config --json Swarm.RelayClient.Enabled true
        ipfs config --json Experimental.Libp2pStreamMounting true

        ipfs daemon
        ```

        In another terminal window:
        ```bash
        ipfs p2p forward /x/ssh /ip4/127.0.0.1/tcp/2222 /p2p/12D3XXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXX
        ```

    === "Windows"

        ```powershell
        wget https://dist.ipfs.tech/kubo/v0.24.0/kubo_v0.24.0_windows-amd64.zip -Outfile kubo_v0.24.0.zip
        Expand-Archive -Path kubo_v0.24.0.zip -DestinationPath C:\opt\kubo
        C:\opt\kubo\ipfs init
        ipfs config --json Swarm.RelayClient.Enabled true
        ipfs config --json Experimental.Libp2pStreamMounting true

        ipfs daemon
        ```

        In another terminal window:
        ```powershell
        ipfs p2p forward /x/ssh /ip4/127.0.0.1/tcp/2222 /p2p/12D3XXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXX
        ```

## SSH to your Robot
You can now open an SSH connection to your robot using the following command:
```bash
ssh -p 2222 user@127.0.0.1
```

or use Visual Studio Code's remote extension pack to connect to your robot.

The way this works is that the SSH client will attempt to connect to a local port, which is actually serviced by the client side IPFS daemon. IPFS will then access the set of computers running the libp2p swarm network to locate the shortest connection to your robot, even if it is behind a NAT, firewall, or over cellular. 

On the Robot side, the IPFS daemon will unpackage the SSH connection and forward it to the local SSH server.




## References
- [IPFS Kubo](https://docs.ipfs.tech/concepts/kubo/)
- [IPFS Swarm](https://docs.ipfs.tech/concepts/swarm/)
- [IPFS Relay](https://docs.ipfs.tech/concepts/relay/)
- [IPFS Libp2p Stream Mounting](https://github.com/ipfs/kubo/blob/master/docs/experimental-features.md#ipfs-p2p)
