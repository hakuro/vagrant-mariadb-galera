# -*- mode: ruby -*-
# vi: set ft=ruby :

VAGRANTFILE_API_VERSION = "2"

Vagrant.configure(VAGRANTFILE_API_VERSION) do |config|
  config.vm.provision :ansible do |ansible|
    ansible.groups = {
      "db" => ["mariadb1", "mariadb2", "mariadb3"],
    }
    ansible.playbook = "provisioning/playbook.yml"
    ansible.limit = 'all'
  end

  config.vm.define :mariadb1 do |server|
      server.vm.box = "centos65"
      server.vm.hostname = "mariadb1"
      server.vm.network :private_network, ip:"192.168.50.11"

      server.vm.provider "virtualbox" do |vb|
          vb.customize ["modifyvm", :id, "--memory", "1024", "--cpus", "2"]
          vb.name = "CentOS-6.5-MariaDB1"
      end
  end

  config.vm.define :mariadb2 do |server|
      server.vm.box = "centos65"
      server.vm.hostname = "mariadb2"
      server.vm.network :private_network, ip:"192.168.50.12"

      server.vm.provider "virtualbox" do |vb|
          vb.customize ["modifyvm", :id, "--memory", "1024", "--cpus", "2"]
          vb.name = "CentOS-6.5-MariaDB2"
      end
  end

  config.vm.define :mariadb3 do |server|
      server.vm.box = "centos65"
      server.vm.hostname = "mariadb3"
      server.vm.network :private_network, ip:"192.168.50.13"

      server.vm.provider "virtualbox" do |vb|
          vb.customize ["modifyvm", :id, "--memory", "1024", "--cpus", "2"]
          vb.name = "CentOS-6.5-MariaDB3"
      end
  end
end
