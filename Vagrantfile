# -*- mode: ruby -*-
# vi: set ft=ruby :

boxes = {
  "ansible-java-centos6.local" => "centos/6",
  "ansible-java-centos7.local" => "centos/7",
  "ansible-java-ubuntu1404.local" => "bento/ubuntu-14.04",
  "ansible-java-ubuntu1604.local" => "bento/ubuntu-16.04"
}

# All Vagrant configuration is done below. The "2" in Vagrant.configure
# configures the configuration version. Don't change it unless you know what
# you're doing.
Vagrant.configure('2') do |config|
  # The most common configuration options are documented and commented below.
  # For a complete reference, please see the online documentation at
  # https://docs.vagrantup.com.

  boxes.each do |box_name, box|
    config.vm.define box_name do |machine|
      # Every Vagrant development environment requires a box. You can search for
      # boxes at https://atlas.hashicorp.com/search.
      machine.vm.box = box

      machine.vm.hostname = box_name

      # Disable automatic box update checking. If you disable this, then
      # boxes will only be checked for updates when the user runs
      # `vagrant box outdated`. This is not recommended.
      # config.vm.box_check_update = false

      # Create a forwarded port mapping which allows access to a specific port
      # within the machine from a port on the host machine. Below,
      # accessing "localhost:8080" will access port 80 on the guest machine.
      # config.vm.network "forwarded_port", guest: 80, host: 8080

      # Create a private network, which allows host-only access to the machine
      # using a specific IP.
      # config.vm.network "private_network", ip: "192.168.33.10"

      # Share an additional folder to the guest VM. The first argument is
      # the path on the host to the actual folder. The second argument is
      # the path on the guest to mount the folder. And the optional third
      # argument is a set of non-required options.
      # config.vm.synced_folder "../data", "/vagrant_data"

      # Disable automatic SSH key inserts
      # config.ssh.insert_key = false

      # Provider-specific configuration.
      machine.vm.provider 'virtualbox' do |vb|
        vb.gui = false
        vb.memory = '512'
        # Use virtualized IO NIC
        vb.customize ['modifyvm', :id, '--nictype1', 'virtio']
      end

      # Ansible provisioning.
      machine.vm.provision 'ansible' do |ansible|
        ansible.playbook = 'tests/test.yml'
        ansible.sudo = true
        ansible.verbose = ENV['ANSIBLE_VERBOSE'] ||= 'vvv'
      end
    end
  end
end
