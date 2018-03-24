# -*- mode: ruby -*-
# vi: set ft=ruby :

# All Vagrant configuration is done below. The "2" in Vagrant.configure
# configures the configuration version (we support older styles for
# backwards compatibility). Please don't change it unless you know what
# you're doing.
Vagrant.configure("2") do |config|
  # The most common configuration options are documented and commented below.
  # For a complete reference, please see the online documentation at
  # https://docs.vagrantup.com.

  # Every Vagrant development environment requires a box. You can search for
  # boxes at https://app.vagrantup.com/boxes/search.
  config.vm.box = "centos/7"
  config.vm.hostname = "centos74task2"
  config.vm.network "forwarded_port", guest: 80, host: 8080

  # Create a public network, which generally matched to bridged network.
  # Bridged networks make the machine appear as another physical device on
  # your network.
  # config.vm.network "public_network"

  # Share an additional folder to the guest VM. The first argument is
  # the path on the host to the actual folder. The second argument is
  # the path on the guest to mount the folder. And the optional third
  # argument is a set of non-required options.
  # config.vm.synced_folder "../data", "/vagrant_data"
  ### Run "vagrant plugin install vagrant-vbguest" for mounts with type: "virtualbox" (on the host OS)
  ### config.vm.synced_folder ".", "/interviewtasks/crm-seed" , type: "virtualbox"

  # Provider-specific configuration so you can fine-tune various
  # backing providers for Vagrant. These expose provider-specific options.
  # Example for VirtualBox:
  #
  config.vm.provider "virtualbox" do |vb|
  vb.gui = true             # Display the VirtualBox GUI when booting the machine
  vb.name = "centos74task2"
  vb.memory = "1024"        # Customize the amount of memory on the VM
  end
  
  # Enable provisioning with a shell script. Additional provisioners such as
  # Puppet, Chef, Ansible, Salt, and Docker are also available. Please see the
  # documentation for more information about their specific syntax and use.
  
    $script = <<SCRIPT
    echo "[install software] Let's go..."
		sudo yum install -y git ansible
	echo "[install software] Done!"
	
	
	echo "[update code] Begin..."
		sudo mkdir -p /interviewtasks/crm-seed/ && sudo chown vagrant:vagrant /interviewtasks/crm-seed/ && git clone https://github.com/vleskiv/crm-seed.git /interviewtasks/crm-seed && /interviewtasks/crm-seed && git checkout task2
    echo "[update code] Done!"
	
	
#	echo "[run ansible] Let's play books..."
#		
#	echo "[run ansible] Done!"
	
    SCRIPT
  
  config.vm.provision "shell", inline: $script
  
  # Run ansible
  config.vm.provision "ansible", playbook: "myname.yml"
  
  end
  