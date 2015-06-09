vSRX Square
=================

A topology containing two vSRXs that can be used to interoperate with each other

Topology
========

The topology consists of four VMs: Client, Server, and two vSRXs. Thes vSRX are set in between the client and the server. The two vSRX can be used to test various connections between each other such as MPLS, IPsec, and dynamic routing. Both the client and the server have appropriate routes pointing to the vSRXs so they can access each other through the vSRXs.

```
TBD
```

### Vagrant Note

Do to the inner workings of Vagrant each host has a virtual NIC connected back to the host running the virtual machines. This allows Vagrant to provision and control each VM over the SSH protocol. These interfaces are depicted on the topology above.

To use this lab with VMware Fusion or Workstation you must first purchase and install the Vagrant VMware Plugin.

[Vagrant VMware Plugin](https://www.vagrantup.com/vmware)

**VM Access Information**

-	[VM Host Passwords](https://github.com/JNPRAutomate/vSRX-Square/blob/master/docs/vmpasswords.md)
