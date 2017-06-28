# -*- mode: ruby -*-
# vi: set ft=ruby :
 
# All Vagrant configuration is done below. The "2" in Vagrant.configure
# configures the configuration version (we support older styles for
# backwards compatibility). Please don't change it unless you know what
# you're doing.
Vagrant.configure(2) do |config|
 
config.hostmanager.enabled = true
config.hostmanager.manage_host = true
config.hostmanager.manage_guest = true
config.hostmanager.ignore_private_ip = false
config.hostmanager.include_offline = true
 
 
 
cached_addresses = {}
config.hostmanager.ip_resolver = proc do |vm, resolving_vm|
  if cached_addresses[vm.name].nil?
    if hostname = (vm.ssh_info && vm.ssh_info[:host])
      vm.communicate.execute("/sbin/ifconfig eth1 | grep 'inet addr' | tail -n 1 | egrep -o '[0-9\.]+' | head -n 1 2>&1") do |type, contents|
        cached_addresses[vm.name] = contents.split("\n").first[/(\d+\.\d+\.\d+\.\d+)/, 1]
      end
    end
  end
  cached_addresses[vm.name]
end
 
 
#This is sets the name of the vm
config.vm.define "dev-db" do |elk|
 
      #This sets the type of VM to install. In this case the OS is Ubuntu running 64 bit Trusty
      elk.vm.box = "ubuntu/trusty64"
 
      #The hostname you want the vm to have.
      elk.vm.hostname = "ansible-dev.pgh.com"
      elk.vm.network "public_network"
 
 
      elk.vm.provider "virtualbox" do |vb|
       vb.cpus = 1
       vb.customize ["modifyvm", :id, "--natdnshostresolver1", "on"]
       vb.gui = true
       vb.memory = "512"
      end
   end  
end