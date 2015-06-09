vSRX Back To Back
=================

A topology containing two vSRXs that can be used to interoperate with each other

Topology
========

The topology consists of four VMs: Client, Server, and two vSRXs. Thes vSRX are set in between the client and the server. The two vSRX can be used to test various connections between each other such as MPLS, IPsec, and dynamic routing. Both the client and the server have appropriate routes pointing to the vSRXs so they can access each other through the vSRXs.

```
          +--------------------+
 <--------+                    |
      eth0|   Client           | +
   To host|                    | | Route to 192.168.0.0/24
          +---------+----------+ v
                    | eth1
                    | 172.16.0.10/24
                    |
                    | 172.16.0.1/24
                    | ge-0/0/1.0
          +---------+----------+
 <--------+                    |
ge-0/0/0.0|  vSRX1             | +
   To host|                    | | Route to 192.168.0.0/24
          +---------+----------+ v
                    | ge-0/0/2.0
                    | 10.0.0.1/24
                    |
                    | 10.0.0.2/24
                    | ge-0/0/2.0
          +---------+----------+ ^
 <--------+                    | | Route to 172.16.0.0/24
ge-0/0/0.0|  vSRX2             | +
   To host|                    |
          +--------------------+
                    |ge-0/0/1.0
                    |192.168.0.1/24
                    |
                    |192.168.0.10/24
                    |eth1
          +--------------------+ ^
 <--------+                    | | Route to 172.16.0.0/24
      eth0|   Server           | +
   To host|                    |
          +--------------------+
```

### Vagrant Note

Do to the inner workings of Vagrant each host has a virtual NIC connected back to the host running the virtual machines. This allows Vagrant to provision and control each VM over the SSH protocol. These interfaces are depicted on the topology above.

To use this lab with VMware Fusion or Workstation you must first purchase and install the Vagrant VMware Plugin.

[Vagrant VMware Plugin](https://www.vagrantup.com/vmware)

**VM Access Information**

-	[VM Host Passwords](https://github.com/JNPRAutomate/vSRX-BackToBack/blob/master/docs/vmpasswords.md)
