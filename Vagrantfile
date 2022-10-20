# create a Virtual Machine using Vagrant
# Virtual box 
# vagrant 
# ruby - dev-kit
# test the installation 
# vagrant
# ruby --version

# creating a VM with Linux OS using Ubuntu 16.04LTS

# 
Vagrant.configure("2") do |config|
    config.vm.define "app" do |app|
      app.vm.box = "ubuntu/bionic64"
      app.vm.network "private_network", ip: "192.168.10.100"
      app.vm.synced_folder ".", "/home/vagrant/app" # change it to your home location 
      app.vm.provision "shell", path: "environment/provision.sh", privileged: false
                                     # provide path for your provision.sh 
    end
  
    config.vm.define "db" do |db|
      db.vm.box = "ubuntu/bionic64"
      db.vm.network "private_network", ip: "192.168.10.150"
      
    end
  end
  
  # exit out of your vm
# run vagrant reload from your localhost - from same location
# where your vagrantfile
# vagrant ssh
# sudo apt-get install nginx -y
