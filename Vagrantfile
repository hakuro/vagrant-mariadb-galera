# -*- mode: ruby -*-
# vi: set ft=ruby :

VAGRANTFILE_API_VERSION = "2"

Vagrant.configure(VAGRANTFILE_API_VERSION) do |config|
  numNodes = 3
  r = 1..numNodes
  (r.first).upto(r.last).each do |i|
    config.vm.define "mariadb#{i}" do |node|
      node.vm.box = "lyrical-centos65-64"
      node.vm.box_url = "http://www.lyricalsoftware.com/downloads/centos65.box"
      node.vm.provider "virtualbox" do |vb|
        vb.customize ["modifyvm", :id, "--memory", "1024", "--cpus", "2"]
        vb.name = "CentOS-6.5-MariaDB#{i}"
      end

      node.vm.hostname = "mariadb#{i}"
      node.vm.network :private_network, ip:"192.168.50.1#{i}"

      node.vm.provision :ansible do |ansible|
        ansible.groups = {
          "db" => ["mariadb#{i}"],
        }
        ansible.verbose = "vv"
        ansible.sudo = true
        ansible.playbook = "provisioning/playbook.yml"
        ansible.limit = 'all'
      end
    end
  end
end
