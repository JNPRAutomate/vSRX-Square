# -*- mode: ruby -*-
# vi: set ft=ruby :

# Vagrantfile API/syntax version. Don't touch unless you know what you're doing!
VAGRANTFILE_API_VERSION = "2"

require "vagrant-host-shell"
require "vagrant-junos"

Vagrant.configure(VAGRANTFILE_API_VERSION) do |config|

#vSRX 1
  config.vm.define "srx1" do |srx|
    srx.vm.box = "juniper/ffp-12.1X47-D20.7"
    srx.vm.hostname = "SRX1"
    srx.vm.network "private_network",
                   ip: "10.1.2.1",
                   nic_type: 'virtio',
                   virtualbox__intnet: "1-to-2"
    srx.vm.network "private_network",
                   ip: "10.1.3.1",
                   nic_type: 'virtio',
                   virtualbox__intnet: "1-to-3"
    srx.vm.network "private_network",
                   ip: "10.1.4.1",
                   nic_type: 'virtio',
                   virtualbox__intnet: "1-to-4"


    srx.vm.synced_folder "", "/vagrant", disabled: true

    srx.vm.provider "virtualbox" do |v|
      # increase RAM to support AppFW and IPS
      # comment out to make it run at 2GB
      v.customize ["modifyvm", :id, "--memory", "2048"]
      v.check_guest_additions = false
    end

    #VMware configuration
    srx.vm.provider "vmware_fusion" do |v|
      v.vmx["memsize"] = "2048"
      v.vmx["ethernet1.generatedAddress"] = nil
      v.vmx["ethernet1.connectionType"] = "custom"
      v.vmx["ethernet1.present"] = "TRUE"
      v.vmx["ethernet1.vnet"] = "vmnet0"
      v.vmx["ethernet2.generatedAddress"] = nil
      v.vmx["ethernet2.connectionType"] = "custom"
      v.vmx["ethernet2.present"] = "TRUE"
      v.vmx["ethernet2.vnet"] = "vmnet1"
      v.vmx["ethernet3.generatedAddress"] = nil
      v.vmx["ethernet3.connectionType"] = "custom"
      v.vmx["ethernet3.present"] = "TRUE"
      v.vmx["ethernet3.vnet"] = "vmnet2"
      v.vmx["ethernet4.generatedAddress"] = nil
      v.vmx["ethernet4.connectionType"] = "custom"
      v.vmx["ethernet4.present"] = "TRUE"
      v.vmx["ethernet4.vnet"] = "vmnet3"
    end

    #
    srx.vm.provision "file", source: "vSRX-configs/vsrx1-inital.cfg", destination: "/cf/root/vsrx1-inital.cfg"
    srx.vm.provision "file", source: "vSRX-configs/nopolicy.cfg", destination: "/cf/root/nopolicy.cfg"
    srx.vm.provision :host_shell do |host_shell|
      # provides the inital configuration
      host_shell.inline = 'vagrant ssh srx1 -c "/usr/sbin/cli -f /cf/root/vsrx1-inital.cfg"'
    end
  end

  #vSRX 2
    config.vm.define "srx2" do |srx|
      srx.vm.box = "juniper/ffp-12.1X47-D20.7"
      srx.vm.hostname = "SRX2"
      srx.vm.network "private_network",
                     ip: "10.1.2.2",
                     nic_type: 'virtio',
                     virtualbox__intnet: "1-to-2"
      srx.vm.network "private_network",
                     ip: "10.2.3.2",
                     nic_type: 'virtio',
                     virtualbox__intnet: "2-to-3"
      srx.vm.network "private_network",
                     ip: "10.2.4.2",
                     nic_type: 'virtio',
                     virtualbox__intnet: "2-to-4"


      srx.vm.synced_folder "", "/vagrant", disabled: true

      srx.vm.provider "virtualbox" do |v|
        # increase RAM to support AppFW and IPS
        # comment out to make it run at 2GB
        v.customize ["modifyvm", :id, "--memory", "2048"]
        v.check_guest_additions = false
      end

      #VMware configuration
      srx.vm.provider "vmware_fusion" do |v|
        v.vmx["memsize"] = "2048"
        v.vmx["ethernet1.generatedAddress"] = nil
        v.vmx["ethernet1.connectionType"] = "custom"
        v.vmx["ethernet1.present"] = "TRUE"
        v.vmx["ethernet1.vnet"] = "vmnet0"
        v.vmx["ethernet2.generatedAddress"] = nil
        v.vmx["ethernet2.connectionType"] = "custom"
        v.vmx["ethernet2.present"] = "TRUE"
        v.vmx["ethernet2.vnet"] = "vmnet1"
        v.vmx["ethernet3.generatedAddress"] = nil
        v.vmx["ethernet3.connectionType"] = "custom"
        v.vmx["ethernet3.present"] = "TRUE"
        v.vmx["ethernet3.vnet"] = "vmnet2"
        v.vmx["ethernet4.generatedAddress"] = nil
        v.vmx["ethernet4.connectionType"] = "custom"
        v.vmx["ethernet4.present"] = "TRUE"
        v.vmx["ethernet4.vnet"] = "vmnet3"
      end

      #
      srx.vm.provision "file", source: "vSRX-configs/vsrx2-inital.cfg", destination: "/cf/root/vsrx2-inital.cfg"
      srx.vm.provision "file", source: "vSRX-configs/nopolicy.cfg", destination: "/cf/root/nopolicy.cfg"
      srx.vm.provision :host_shell do |host_shell|
        # provides the inital configuration
        host_shell.inline = 'vagrant ssh srx2 -c "/usr/sbin/cli -f /cf/root/vsrx2-inital.cfg"'
      end
    end

    #vSRX 3
      config.vm.define "srx3" do |srx|
        srx.vm.box = "juniper/ffp-12.1X47-D20.7"
        srx.vm.hostname = "SRX3"
        srx.vm.network "private_network",
                       ip: "10.1.3.3",
                       nic_type: 'virtio',
                       virtualbox__intnet: "1-to-3"
        srx.vm.network "private_network",
                       ip: "10.3.4.3",
                       nic_type: 'virtio',
                       virtualbox__intnet: "3-to-4"
        srx.vm.network "private_network",
                       ip: "10.2.3.3",
                       nic_type: 'virtio',
                       virtualbox__intnet: "2-to-3"


        srx.vm.synced_folder "", "/vagrant", disabled: true

        srx.vm.provider "virtualbox" do |v|
          # increase RAM to support AppFW and IPS
          # comment out to make it run at 2GB
          v.customize ["modifyvm", :id, "--memory", "2048"]
          v.check_guest_additions = false
        end

        #VMware configuration
        srx.vm.provider "vmware_fusion" do |v|
          v.vmx["memsize"] = "2048"
          v.vmx["ethernet1.generatedAddress"] = nil
          v.vmx["ethernet1.connectionType"] = "custom"
          v.vmx["ethernet1.present"] = "TRUE"
          v.vmx["ethernet1.vnet"] = "vmnet0"
          v.vmx["ethernet2.generatedAddress"] = nil
          v.vmx["ethernet2.connectionType"] = "custom"
          v.vmx["ethernet2.present"] = "TRUE"
          v.vmx["ethernet2.vnet"] = "vmnet1"
          v.vmx["ethernet3.generatedAddress"] = nil
          v.vmx["ethernet3.connectionType"] = "custom"
          v.vmx["ethernet3.present"] = "TRUE"
          v.vmx["ethernet3.vnet"] = "vmnet2"
          v.vmx["ethernet4.generatedAddress"] = nil
          v.vmx["ethernet4.connectionType"] = "custom"
          v.vmx["ethernet4.present"] = "TRUE"
          v.vmx["ethernet4.vnet"] = "vmnet3"
        end

        #
        srx.vm.provision "file", source: "vSRX-configs/vsrx3-inital.cfg", destination: "/cf/root/vsrx3-inital.cfg"
        srx.vm.provision "file", source: "vSRX-configs/nopolicy.cfg", destination: "/cf/root/nopolicy.cfg"
        srx.vm.provision :host_shell do |host_shell|
          # provides the inital configuration
          host_shell.inline = 'vagrant ssh srx3 -c "/usr/sbin/cli -f /cf/root/vsrx3-inital.cfg"'
        end
      end

      #vSRX 3
        config.vm.define "srx4" do |srx|
          srx.vm.box = "juniper/ffp-12.1X47-D20.7"
          srx.vm.hostname = "SRX4"
          srx.vm.network "private_network",
                         ip: "10.1.4.4",
                         nic_type: 'virtio',
                         virtualbox__intnet: "1-to-4"
          srx.vm.network "private_network",
                         ip: "10.3.4.4",
                         nic_type: 'virtio',
                         virtualbox__intnet: "3-to-4"
          srx.vm.network "private_network",
                         ip: "10.2.4.4",
                         nic_type: 'virtio',
                         virtualbox__intnet: "2-to-4"


          srx.vm.synced_folder "", "/vagrant", disabled: true

          srx.vm.provider "virtualbox" do |v|
            # increase RAM to support AppFW and IPS
            # comment out to make it run at 2GB
            v.customize ["modifyvm", :id, "--memory", "2048"]
            v.check_guest_additions = false
          end

          #VMware configuration
          srx.vm.provider "vmware_fusion" do |v|
            v.vmx["memsize"] = "2048"
            v.vmx["ethernet1.generatedAddress"] = nil
            v.vmx["ethernet1.connectionType"] = "custom"
            v.vmx["ethernet1.present"] = "TRUE"
            v.vmx["ethernet1.vnet"] = "vmnet0"
            v.vmx["ethernet2.generatedAddress"] = nil
            v.vmx["ethernet2.connectionType"] = "custom"
            v.vmx["ethernet2.present"] = "TRUE"
            v.vmx["ethernet2.vnet"] = "vmnet1"
            v.vmx["ethernet3.generatedAddress"] = nil
            v.vmx["ethernet3.connectionType"] = "custom"
            v.vmx["ethernet3.present"] = "TRUE"
            v.vmx["ethernet3.vnet"] = "vmnet2"
            v.vmx["ethernet4.generatedAddress"] = nil
            v.vmx["ethernet4.connectionType"] = "custom"
            v.vmx["ethernet4.present"] = "TRUE"
            v.vmx["ethernet4.vnet"] = "vmnet3"
          end

          #
          srx.vm.provision "file", source: "vSRX-configs/vsrx4-inital.cfg", destination: "/cf/root/vsrx4-inital.cfg"
          srx.vm.provision "file", source: "vSRX-configs/nopolicy.cfg", destination: "/cf/root/nopolicy.cfg"
          srx.vm.provision :host_shell do |host_shell|
            # provides the inital configuration
            host_shell.inline = 'vagrant ssh srx4 -c "/usr/sbin/cli -f /cf/root/vsrx4-inital.cfg"'
          end
        end
end
