# -*- mode: ruby -*-
# vi: set ft=ruby :

# Vagrantfile API/syntax version. Don't touch unless you know what you're doing!

Vagrant.configure(2) do |config|

  # set to false, if you do NOT want to check the correct VirtualBox Guest Additions version when booting this box
  if defined?(VagrantVbguest::Middleware)
    config.vbguest.auto_update = true
  end

  config.vm.box = "bento/centos-7.5"

 config.vm.define "apim", primary: true do |apim|
   config.vm.hostname = "apim"
   apim.vm.synced_folder('.', '/Vagrantfiles', type: 'rsync')
   apim.ssh.shell = "bash -c 'BASH_ENV=/etc/profile exec bash'"
   apim.vm.network :private_network, ip: "172.16.10.130"
   apim.vm.provider :esxi do |lb|
       lb.memory = 2048
   end
 end


#  config.vm.provision :shell,
#    :keep_color => true,
#    :path => "setup.sh"
end
