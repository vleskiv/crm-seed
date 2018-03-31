kk# -*- mode: ruby -*-
# vi: set ft=ruby :

### configuration parameters ###
# which host port to forward box HTTP port to
LOCAL_HTTP_PORT = "8080"
# Vagrant base box to use
BOX_BASE = "centos/7"
# amount of RAM for Vagrant box
BOX_RAM_MB = "1024"
# number of CPUs for Vagrant box
BOX_CPU_COUNT = "1"
# project folder path
PROJECT_FOLDER = "/interviewtasks/crm-seed/"
### /configuration parameters ###

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
  config.vm.hostname = "centos74task3"
  #config.vm.network "forwarded_port", guest: 80, host: LOCAL_HTTP_PORT

  # Create a public network, which generally matched to bridged network.
  # Bridged networks make the machine appear as another physical device on
  # your network.
  config.vm.network "public_network"
  
  # Share an additional folder to the guest VM. The first argument is
  # the path on the host to the actual folder. The second argument is
  # the path on the guest to mount the folder. And the optional third
  # argument is a set of non-required options.
  # config.vm.synced_folder "../data", "/vagrant_data"
  ### Run "vagrant plugin install vagrant-vbguest" for mounts with type: "virtualbox" (on the host OS)
  ### config.vm.synced_folder ".", PROJECT_FOLDER , type: "virtualbox"
  ### config.vm.synced_folder ".", PROJECT_FOLDER

  # Provider-specific configuration so you can fine-tune various
  # backing providers for Vagrant. These expose provider-specific options.
  # Example for VirtualBox:
  #
  config.vm.provider "virtualbox" do |vb|
  vb.gui = true                 # Display the VirtualBox GUI when booting the machine
  vb.name = "centos74task3"     # Name of the virtual machine in VirtualBox
  vb.memory = BOX_RAM_MB        # Customize the amount of memory on the VM
  vb.cpus = BOX_CPU_COUNT       # Customize cpu cores
  end
  
  # Enable provisioning with a shell script. Additional provisioners such as
  # Puppet, Chef, Ansible, Salt, and Docker are also available. Please see the
  # documentation for more information about their specific syntax and use.
  
$script = <<SCRIPT
    echo "[install software] Let's go..."
		sudo yum install -y git ansible
	echo "[install software] Done!"
	echo "[update code] Begin..."
	    ROOT_FOLDER=/interviewtasks/crm-seed
		echo Root folder is $ROOT_FOLDER/
		if [ -d $ROOT_FOLDER/.git ];then echo "Code is present, nothing to do.";else echo "Code not found in" $ROOT_FOLDER/ "Begin downloading from github..." && sudo mkdir -p $ROOT_FOLDER/ && sudo chown -R vagrant:vagrant $ROOT_FOLDER/.. && rm -rf $ROOT_FOLDER/* && mkdir -p $ROOT_FOLDER/.git && cd $ROOT_FOLDER/ && git clone --bare https://github.com/vleskiv/crm-seed.git .git && git config --unset core.bare && git reset --hard && git checkout task3 && echo "[update code] Done!";
		fi
SCRIPT
  
  config.vm.provision "shell", inline: $script,
    run: "always"	# always run this provision (shell)
  
  # Run ansible (not work on Windows host)
  # config.vm.provision "ansible", playbook: "myname.yml"
  
  end

