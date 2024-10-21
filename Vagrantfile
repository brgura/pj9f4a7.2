Vagrant.configure("2") do |config|
  config.vm.box = "debian/bullseye64"
  config.vm.hostname = "brgura.fjeclot.net"
  config.vm.provider "virtualbox" do |v|
    # v.gui = true
    v.name = "pj9f4a7.2_brgura"
    v.memory = 2048
    v.cpus = 2
    v.customize ['modifyvm', :id, '--clipboard', 'bidirectional']
    config.vm.synced_folder "../codi", "/var/www/html"     
  end

  config.vm.network "public_network"

  config.vm.network "forwarded_port", guest: 80, host: 8000
  config.vm.network "forwarded_port", guest: 443, host: 8443
  
  config.vm.provision "shell", inline: <<-SHELL
    sudo apt-get update -y
    sudo apt-get install -y net-tools
    sudo apt-get install -y apache2 apache2-doc
    sudo apt-get install -y libapache2-mod-php
    sudo apt-get install -y php7.3 
    sudo apt-get install -y mriadb-server
    sudo apt-get install -y mriadb-client
    sudo apt-get install -y php7.4-mysql
    sudo apt-get install -y composer
    sudo apt-get install -y aptitude    
  SHELL

end
