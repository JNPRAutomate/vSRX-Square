vSRX Square
=================

A topology containing two vSRXs that can be used to interoperate with each other

Topology
========

The topology consists of four VMs: four vSRXs. Thes vSRX are configured in a star topology where each node is connected to each other.

```

SRX1--------------SRX3
 | \             / |
 |  | _ _ _ _____| |
 |  _______X_ _ _  |
 | /             \ |
SRX2--------------SRX4

```

## Interface Naming

### Access Note

For NETCONF testing each node has its NETCONF port exposed via port forwarding.

- vSRX1 - 8831
- vSRX2 - 8832
- vSRX3 - 8833
- vSRX4 - 8834

### Vagrant Note

Do to the inner workings of Vagrant each host has a virtual NIC connected back to the host running the virtual machines. This allows Vagrant to provision and control each VM over the SSH protocol. These interfaces are depicted on the topology above.

To use this lab with VMware Fusion or Workstation you must first purchase and install the Vagrant VMware Plugin.

[Vagrant VMware Plugin](https://www.vagrantup.com/vmware)

**VM Access Information**

-	[VM Host Passwords](https://github.com/JNPRAutomate/vSRX-Square/blob/master/docs/vmpasswords.md)
