# -*- mode: ruby -*-
# vi: set ft=ruby :

# Vagrantfile API/syntax version. Don't touch unless you know what you're doing!
VAGRANTFILE_API_VERSION = "2"

Vagrant.configure(VAGRANTFILE_API_VERSION) do |config|
  config.vm.box = "chef/centos-7.0"
  config.vm.synced_folder ".", "/home/vagrant/ansible-playbooks", owner: "vagrant", group: "users", mount_options: ["dmode=755", "fmode=644"]
  config.vm.provision 'shell', inline: "yum -y install {epel-release,ansible}"
end
