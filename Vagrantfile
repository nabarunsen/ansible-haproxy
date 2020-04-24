# -*- mode: ruby -*-
# vi: set ft=ruby :

VAGRANTFILE_API_VERSION = "2"

Vagrant.configure(VAGRANTFILE_API_VERSION) do |config|
    config.vm.box = "centos/7"
      config.ssh.insert_key = false
      config.vm.provider "virtualbox" do |v|
      v.memory = 2048
    end

    config.vm.box_check_update = false
      config.vm.define "master1" do |node|
  		node.vm.network "private_network", ip: "172.42.42.15"
  		node.vm.hostname = "master1"
  		node.vm.provision :shell, inline: "cat /vagrant/ssh-key.pub >> .ssh/authorized_keys"
        node.vm.provision :shell, inline: "cat /vagrant/id_rsa.pub >> .ssh/authorized_keys"
        node.vm.provision :shell, inline: "sudo sed -i 's/PasswordAuthentication no/PasswordAuthentication yes/g' /etc/ssh/sshd_config"
        node.vm.provision :shell, inline: "sudo systemctl restart sshd"
  		config.vm.provider :virtualbox do |vb|
  			vb.customize ["modifyvm", :id, "--memory", "2024"]
  		end
	  end

    config.vm.define "master2" do |node|
  		node.vm.network "private_network", ip: "172.42.42.16"
  		node.vm.hostname = "master2"
        node.vm.provision :shell, inline: "cat /vagrant/ssh-key.pub >> .ssh/authorized_keys"
        node.vm.provision :shell, inline: "cat /vagrant/id_rsa.pub >> .ssh/authorized_keys"
        node.vm.provision :shell, inline: "sudo sed -i 's/PasswordAuthentication no/PasswordAuthentication yes/g' /etc/ssh/sshd_config"
        node.vm.provision :shell, inline: "sudo systemctl restart sshd"
  		config.vm.provider :virtualbox do |vb|
  			vb.customize ["modifyvm", :id, "--memory", "2024"]
  		end
	  end

	config.vm.define "master2" do |node|
  		node.vm.network "private_network", ip: "172.42.42.17"
  		node.vm.hostname = "master3"
        node.vm.provision :shell, inline: "cat /vagrant/ssh-key.pub >> .ssh/authorized_keys"
        node.vm.provision :shell, inline: "cat /vagrant/id_rsa.pub >> .ssh/authorized_keys"
        node.vm.provision :shell, inline: "sudo sed -i 's/PasswordAuthentication no/PasswordAuthentication yes/g' /etc/ssh/sshd_config"
        node.vm.provision :shell, inline: "sudo systemctl restart sshd"
  		config.vm.provider :virtualbox do |vb|
  			vb.customize ["modifyvm", :id, "--memory", "2024"]
  		end
	  end
end
