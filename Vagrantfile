Vagrant.configure("2") do |config|
  HOSTS=3
  (1..HOSTS).each do |swarm_node|
    node_name = "docker#{swarm_node}"
    config.vm.define node_name do |cnode|
        cnode.vm.box = "centos/7"
        cnode.vm.network "private_network", ip: "192.168.44.#{100 + swarm_node}"
        cnode.vm.hostname = node_name
        cnode.vm.provider :virtualbox do |vbox|
            vbox.linked_clone = true
            vbox.name = node_name
            vbox.memory = 2048
            vbox.cpus = 2
        end
        cnode.vm.synced_folder '.', '/vagrant', disabled: true
        # All vms have been provisioned. Run Ansible
        if swarm_node == HOSTS
            cnode.vm.provision :ansible do |ansible|
            ansible.limit = "all" # Connect to all machines
            ansible.playbook = "swarm.yml"
        end
    end
   end
  end
end
