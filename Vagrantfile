# -*- mode: ruby -*-
# vi: set ft=ruby :

$num_instances ||= 3
$instance_name_prefix ||= "hadoop"
$vm_memory ||= 2048
$vm_cpus ||= 1

Vagrant.configure("2") do |config|
  (1..$num_instances).each do |i|
    config.vm.define $instance_name_prefix+"#{i}" do |node|
      node.vm.network "private_network", ip: "172.16.251.7#{i}"
      node.vm.hostname =$instance_name_prefix+"#{i}" 
      node.vm.box = "ubuntu/focal64"
      #node.ssh.username = 'vagrant'
      #node.ssh.password="vagrant"
      #node.ssh.keys_only=false
      node.ssh.insert_key = false
      # 设置内存、CPU
      node.vm.provider "virtualbox" do |h|
          h.name=$instance_name_prefix+"#{i}"
          h.memory = $vm_memory
          h.cpus = $vm_cpus
      end
    end
  end
end