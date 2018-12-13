Vagrant.configure("2") do |config|
  # config.vm.box = "ubuntu/trusty64"
  config.vm.box = "ubuntu/bionic64"
  # config.vm.box_version = "20170313.0.6"
  # config.vm.box_check_update = false
  config.vm.provider "virtualbox" do |vb|
    vb.customize ["modifyvm", :id, "--memory", "1024"]
  end

  # Create a private network, which allows host-only access to the machine
  # using a specific IP.
  config.vm.network "private_network", ip: "192.168.33.10"

  
  config.vm.synced_folder "vagrantHome/", "/home/vagrant/shared"
  # Enable provisioning with a shell script. Additional provisioners such as
  # Puppet, Chef, Ansible, Salt, and Docker are also available. Please see the
  # documentation for more information about their specific syntax and use.
  config.vm.provision "shell", inline: <<-SHELL
    # mongodb
    apt-key adv --keyserver hkp://keyserver.ubuntu.com:80 --recv 9DA31620334BD75D9DCB49F368818C72E52529D4
    echo "deb [ arch=amd64 ] https://repo.mongodb.org/apt/ubuntu trusty/mongodb-org/4.0 multiverse" | sudo tee /etc/apt/sources.list.d/mongodb-org-4.0.list
    apt-get update
    apt-get install -y mongodb-org

    # nodejs
    curl -sL https://deb.nodesource.com/setup_6.x | sudo -E bash -
    apt-get install -y nodejs
    
    # YeoMan, Angular Fullstack & Gulp
    npm install -g yo generator-angular-fullstack gulp-cli

    # git
    apt-get install -y git
  SHELL
  config.vm.provision "shell", path: "result.sh"
end
