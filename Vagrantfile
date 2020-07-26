Vagrant.configure("2") do |config|

  config.vm.box = "ubuntu/bionic64"

  config.vm.define "beacon_node" do |machine|
    machine.vm.network "private_network", ip: "172.17.177.21"
  end

  config.vm.define "validator1" do |machine|
    machine.vm.network "private_network", ip: "172.17.177.22"
  end

  config.vm.define 'controller' do |machine|
    machine.vm.network "private_network", ip: "172.17.177.11"

    machine.vm.provision :ansible_local do |ansible|
      ansible.playbook         = "playbooks/start_all.yml"
      ansible.verbose          = true
      ansible.install          = true
      ansible.inventory_path   = "inventory-vagrant"
      ansible.limit            = "all"
      ansible.galaxy_role_file = "requirements.yml"
      ansible.extra_vars       = {
        github_user_pubkeys: []
      }
    end
  end

end
