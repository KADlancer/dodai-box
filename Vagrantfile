# -*- mode: ruby -*-
# vi: set ft=ruby :





# Vagrantfile API/syntax version (we support older styles for backwards compatibility).
# Don't touch unless you know what you're doing!
VAGRANTFILE_API_VERSION = "2"



$core_script = <<SCRIPT
curl -sL https://deb.nodesource.com/setup_9.x | sudo -E bash -
sudo apt-get install -y nodejs
sudo apt-get install -y build-essential
sudo npm install -g yarn
mkdir /home/vagrant/node_modules
chown vagrant:vagrant /home/vagrant/node_modules
rm -rf /vagrant/node_modules
ln -s /home/vagrant/node_modules /vagrant/node_modules
sudo apt-get install -y apache2 php5 libapache2-mod-php5 php5-mcrypt
sudo rm -rf /var/www/html
sudo ln -s /vagrant /var/www/html
SCRIPT


Vagrant.configure(VAGRANTFILE_API_VERSION) do |config|
  # All Vagrant configuration is done here. The most common configuration
  # options are documented and commented below. For a complete reference,
  # please see the online documentation at vagrantup.com.

  config.vm.box = "ubuntu/trusty64"


  # Usually, host locale environment variables are passed to guest.
  # It may cause failures if the guest software do not support host locale.
  # One possible solution is override locale in the Vagrantfile:
  # ENV["LC_ALL"] = "de_DE.UTF-8"
  ENV["LC_ALL"] = "en_US.UTF-8"


  # Disable automatic box update checking. If you disable this, then
  # boxes will only be checked for updates when the user runs
  # `vagrant box outdated`. This is not recommended.
   config.vm.box_check_update = false


  # Multi-Machine server configuration
  # read https://www.vagrantup.com/docs/multi-machine/ for more details
  config.vm.define "dodai-box", primary: true do | m |


  # The hostname the machine should have. Defaults to nil. If nil, Vagrant will
  # not manage the hostname. If set to a string, the hostname will be set on boot.
  m.vm.hostname = "dodai-box"


  # Create a forwarded port mapping which allows access to a specific port
  # within the machine from a port on the host machine. In the example below,
  # accessing "localhost:8080" will access port 80 on the guest machine.
  # config.vm.network :forwarded_port, guest: 80, host: 8080
  # IMPORTANT: port "BASE" / 8453 is only for the base project itself
  # -> change when starting new projects by cloning this
  m.vm.network "forwarded_port", guest: 8453, host: 8453


  # forwarded ports for browser sync


  m.vm.provider "dodai-box" do |vb|
    vb.customize ["modifyvm", :id, "--cpuexecutioncap", "75"]
    vb.memory = "4096"
    vb.cpus = 2
  end

  config.vm.provision "shell",inline: $core_script

  end


end
