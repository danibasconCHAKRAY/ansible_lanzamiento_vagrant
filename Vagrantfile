# -*- mode: ruby -*-
# vi: set ft=ruby :

Vagrant.configure(2) do |config|
 config.vm.box = "bento/centos-7.5"
 config.vm.define "apim", primary: true do |apim|
   config.vm.hostname = "apim"
#   apim.vm.network :private_network, ip: "192.168.26.101", netmask: "255.255.255.0"
   apim.vm.synced_folder('.', '/Vagrantfiles', type: 'rsync')
   apim.ssh.shell = "bash -c 'BASH_ENV=/etc/profile exec bash'"
   apim.vm.provision "ansible" do |ansible|
       ansible.compatibility_mode = "1.8"
       ansible.playbook = "provisioning/playbook.yml"
   end
 end
end
