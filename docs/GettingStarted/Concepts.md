This guide will provide a high level overview of concepts needed to set up your robots and users. 

## Cryptographic identity
At the root of Decentralized Robotics, and libp2p is a *cryptographic identity*, which forms the basis of securing, authenticating and authorizing access in the decentralized peer-to-peer network.

A Cryptographic identity contains 3 components:

- a Public Key, which can be shared with others.
- a Private Key, which must be kept secret. The private key 'proves' that the public key belongs to the holder of the private key.
- a p2p address, which is generated from the public key and is used to discover the node on the network. The p2p address is also used to by the operator or admin applications. 

Each Robot and each user will have a cryptographic identity. The robot's identity is generated during provisioning. The user's identity is generated separately and the p2p ID is added to the robot allow list. 

For DeRo, the output of identity creation is a json text file, which contains the 3 components. The user is responsible for storing this json file in a secure location. The public key and p2p address can be shared with others[^1]. 

In IPFS (and the technology it is built on libp2p) terminology, the cryptographic identity is called a [peer identity](https://docs.ipfs.tech/concepts/identity/).

## Create Users
You can use the Command Line tool to create users. This will output a json file with a cryptographic identity. This file can be created by the end user, but an administrator needs to add the user's p2p address to the robot's allow list.

```bash
dros user create -f user.json
```

## Provision a Robot
During initial install of a robot, it needs to be provisioned. This is done by running `dero init`. This will generate a private key and store it in the robot's local storage. 

A Robot also needs to be informed of what users can access it, as well as what roles they have. This is done by running `dero user add`. This will add the user's p2p address to the robot's allow list. 

## Role Based Access Control  ![future](https://img.shields.io/badge/future-8A2BE2)
Users of a robot are assigned a role at provisioning time. 

Several roles are available:
- `administrator` - can add and remove users, and change roles. An `administrator` is also an operator
- `operator` - can connect to the robot and control it.
- `monitor` - can connect to the robot and view it's status, but not control it. In ROS, this means a `monitor` can subscribe, but not publish.
- `restricted` - can connect to the robot, but only subscribe to topics that are explicitly allowed.

Restricted users need to be given explicit access to topics. More details are provided in the `dero` command line documentation.

## Role-Based Access Control lists on Blockchain ![future](https://img.shields.io/badge/future-8A2BE2)
User access lists are currently stored on the robot. However, in the future, these lists can be stored on a blockchain. This will allow for more flexible access control, controlling multiple robots, as well as the ability to revoke access remotely.


## Private Relays ![future](https://img.shields.io/badge/future-8A2BE2)
By default, the robot and operator applications will use the [public bootstrap nodes on libp2p network](https://blog.ipfs.tech/2023-rust-libp2p-based-ipfs-bootstrap-node/).

However, both can be configured to use private relays. This is done by running the `dero relay` command. This will set the robot's relay to the provided p2p address. The p2p address is used to discover the relay on the network. The p2p address is also used to connect to the relay using the operator or admin application.


## Administrative Web App ![future](https://img.shields.io/badge/future-8A2BE2)
The administrative application is available through [admin.decentralizedrobotics.xyz](https://admin.decentralizedrobotics.xyz)



[^1]: Hardware token storage is being investigated for future releases.




