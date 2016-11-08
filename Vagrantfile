# -*- mode: ruby -*-
# vi: set ft=ruby :

# Combined with a little bit more Ruby, this makes it very easy to embed your
# shell scripts directly within your Vagrantfile.
# I understand that if you are not familiar with Ruby, the above may seem very
# advanced or foreign. But do not fear, what it is doing is quite simple:
#   the script is assigned to a global variable $script. This global variable
#   contains a string which is then passed in as the inline script to the Vagrant configuration.
# This script is used later and run always
$script = <<SHELL
   sudo su vagrant -c '/usr/local/lib/npm/bin/pm2 restart all'
SHELL

# All Vagrant configuration is done below. The "2" in Vagrant.configure
# configures the configuration version (we support older styles for
# backwards compatibility). Please don't change it unless you know what
# you're doing.
Vagrant.configure("2") do |config|
  # The most common configuration options are documented and commented below.
  # For a complete reference, please see the online documentation at
  # https://docs.vagrantup.com.

  # Every Vagrant development environment requires a box. You can search for
  # boxes at https://atlas.hashicorp.com/search.
  config.vm.box = "kraeml/ubuntu_de"
  #config.vm.box = "test"

  # Disable automatic box update checking. If you disable this, then
  # boxes will only be checked for updates when the user runs
  # `vagrant box outdated`. This is not recommended.
  # config.vm.box_check_update = false

  # Falls vbguest-plugin bitte Guest nachladen
  if Vagrant.has_plugin?("vagrant-vbguest") then
    config.vbguest.auto_update = true
  end

  # Create a forwarded port mapping which allows access to a specific port
  # within the machine from a port on the host machine. In the example below,
  # accessing "localhost:8080" will access port 80 on the guest machine.
  # For webserver nginx
  config.vm.network "forwarded_port", guest: 80, host: 8080
  # For Jupyter
  config.vm.network "forwarded_port", guest: 8888, host: 8888
  # For Cloud9
  config.vm.network "forwarded_port", guest: 8181, host: 8181
  # For node-red
  config.vm.network "forwarded_port", guest: 1880, host: 1880
  # For nodejs webserver on port 3000
  config.vm.network "forwarded_port", guest: 3000, host: 3000
  # For flask webserver on port 5000
  config.vm.network "forwarded_port", guest: 5000, host: 5000

  # Create a private network, which allows host-only access to the machine
  # using a specific IP.
  config.vm.network "private_network", ip: "192.168.6.10"

  # Create a public network, which generally matched to bridged network.
  # Bridged networks make the machine appear as another physical device on
  # your network.
  # config.vm.network "public_network"

  # Share an additional folder to the guest VM. The first argument is
  # the path on the host to the actual folder. The second argument is
  # the path on the guest to mount the folder. And the optional third
  # argument is a set of non-required options.
  config.vm.synced_folder "projekte", "/home/vagrant/www"

  # Provider-specific configuration so you can fine-tune various
  # backing providers for Vagrant. These expose provider-specific options.
  # Example for VirtualBox:
  #
   config.vm.provider "virtualbox" do |vb|
     # Display the VirtualBox GUI when booting the machine
     vb.gui = true

     # Customize the amount of memory on the VM:
     vb.memory = "1024"
     vb.customize ["modifyvm", :id, "--cpus", 2]
     vb.name = "itec_ubuntu_de"
     vb.customize ["modifyvm", :id, "--cpuexecutioncap", "75"]
     vb.linked_clone = true if Vagrant::VERSION =~ /^1.8/
   end
  #
  # View the documentation for the provider you are using for more
  # information on available options.

  # Enable provisioning with a shell script. Additional provisioners such as
  # Puppet, Chef, Ansible, Salt, and Docker are also available. Please see the
  # documentation for more information about their specific syntax and use.
  # config.vm.provision "shell", inline: $script, run: "always"
end
