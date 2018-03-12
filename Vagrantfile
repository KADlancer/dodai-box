# -*- mode: ruby -*-
# vi: set ft=ruby :

# All Vagrant configuration is done below. The "2" in Vagrant.configure
# configures the configuration version (we support older styles for
# backwards compatibility). Please don't change it unless you know what
# you're doing.
Vagrant.configure("2") do |config|
  config.vm.box = "ubuntu/trusty64"

  # Disable automatic box update checking. If you disable this, then
  # boxes will only be checked for updates when the user runs
  # `vagrant box outdated`. This is not recommended.
   config.vm.box_check_update = false


  # firstspirit server configurationvag
  config.vm.define "dodai-box", primary: true do | m |

$core_script = <<SCRIPT
curl -sL https://deb.nodesource.com/setup_7.x | sudo -E bash -
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


    m.vm.hostname = "dodai-box"
    m.vm.network "forwarded_port", guest: 80, host: 8453 # port "BASE" / 8453 is only for the base project itself
    # forwarded ports for browser sync
    #m.vm.network "forwarded_port", guest: 3000, host: 3000
    #m.vm.network "forwarded_port", guest: 3001, host: 3001

    m.vm.provider "dodai-box" do |vb|
      vb.memory = "4096"
    end

    config.vm.provision "shell",inline: $core_script

  end


end
