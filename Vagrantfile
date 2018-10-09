# -*- mode: ruby -*-
# vi: set ft=ruby :

# Vagrantfile API/syntax version. Don't touch unless you know what you're doing!

Vagrant.configure(2) do |config|

  # set to false, if you do NOT want to check the correct VirtualBox Guest Additions version when booting this box

  config.vm.box = "bento/centos-7.5"
#  config.vm.box = "bento/ubuntu-18.04"
#  config.vm.box = "bento/debian-9.5"

TIME = Time.now.strftime('test-%Y-%m-%d')
 
config.vm.define "#{TIME}", primary: true do |node|
   node.vm.hostname = "#{TIME}"
   node.vm.synced_folder('.', '/Vagrantfiles', type: 'rsync')
   node.ssh.shell = "bash -c 'BASH_ENV=/etc/profile exec bash'"
   node.vm.network :private_network, ip: "172.16.10.133"
   node.vm.provider :esxi do |lb|
       lb.memory = 1024
   end
 end

  config.vm.provider :vmware_esxi do |esxi, overrider|
    #
    #   Provider settings
    #
    esxi.esxi_hostname = '10.10.1.10'
    esxi.esxi_username = 'vagrant'
    esxi.esxi_password = 'env:'
    #esxi.esxi_hostport = 22
    esxi.esxi_virtual_network = 'VM Network'
    #esxi.esxi_disk_store = 'DS_001'
    #esxi.esxi_resource_pool = '/Vagrant'
    #esxi.guest_memsize = '4096'
    #esxi.guest_numvcpus = '2'
  end
  config.vm.provision :shell,
    :keep_color => true,
    :path => "setup.sh"
end
