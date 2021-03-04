# -*- mode: ruby -*-
# vi: set ft=ruby :

VAGRANTFILE_API_VERSION = "2"

Vagrant.configure(VAGRANTFILE_API_VERSION) do |config|
  config.vm.box = "geerlingguy/ubuntu2004"
  config.vm.synced_folder '.', '/vagrant', disabled: true
  config.ssh.insert_key = false

  config.vm.provider :virtualbox do |v|
    v.memory = 2048
    v.cpus = 2
  end

  # Gitea server.
  config.vm.define "gitea" do |logs|
    logs.vm.hostname = "gitea.localdomain"
    logs.vm.network :private_network, ip: "192.168.9.90"

    logs.vm.provision :ansible do |ansible|
      ansible.playbook = "provisioning/gitea/main-dev.yml"
      ansible.inventory_path = "provisioning/gitea/inventory.yml"
      ansible.become = true
    end
  end

end
