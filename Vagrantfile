# -*- mode: ruby -*-


require 'yaml'
servers = YAML.load_file('OSname.yml')
API_VERSION = "2"
Vagrant.configure(API_VERSION) do |config|
  servers.each do | servers |
    config.vm.define servers["name"] do |machine|
      machine.vm.box = servers["box"]
      machine.vm.network "private_network", ip: servers["box_ip"]
      machine.vm.provider :virtualbox do |vb|
      machine.vm.provision :ansible do |ansible|
        vb.name = servers["name"]
        vb.memory = servers["memory"]
        vb.cpus = servers["cpu"]
      ansible.playbook = servers["provision"]
      end
    end
  end
end
end
