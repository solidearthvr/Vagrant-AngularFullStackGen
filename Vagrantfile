Vagrant.configure("2") do |config|
  config.vm.box = "ubuntu/trusty64"
  config.vm.box_version = "20170313.0.6"
  config.vm.box_check_update = false
  config.vm.provider "virtualbox" do |vb|
    vb.customize ["modifyvm", :id, "--memory", "1024"]
  end
  config.vm.provision "shell", path: "node.sh"
  config.vm.provision "shell", path: "npmGlobals.sh"
  config.vm.provision "shell", path: "git.sh"
  config.vm.provision "shell", path: "mongodb.sh"
  config.vm.provision "shell", path: "result.sh"
  config.vm.synced_folder "vagrantHome/", "/home/vagrant/shared"
end
