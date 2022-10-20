# Virtualisation
## Dev Env
### Vagrant
- check internet connectivity `sudo apt-get update`
- Run upgrade `sudo apt-get upgrade -y`
- Where am i `pwd` give you your current location
- Whomai `uname` or `uname -a`
- How to create a file in linux `touch filename` & `nano filename`
- How to check file/folder available in current location `ls` or to check all files hidden files as well `ls -a`
- How to create a folder `mkdir fodler-name`
- How navigate to the folder `cd folder-name`
- How to navigate back/out `cd ..` or `cd` Enter
- How to delete a file/folder `rm -rf file/foldername`
- Research how to copy file from 1 location to another
- copy test.txt into app folder
- How to navigate between OS & VM `exit` Enter
- for Admin access `sudo` switch to admin user `sudo su`
- change permission `chmod instruction file-name` i.e `chmod 700 test.text`
- Currently running process `top` & `ps aux`
- To remove any process `kill PID` - `kill 7`
- how to delete folder/hidden folder `ls -a`
- print last 3 lines from the test.txt
- print first 3 lines from the test.txt
- print last 10 lines from the test.txt
- print last  lines from the test.txt
- Research how to use `| pipe` & `grep` & `sort`
- `ps aux` short list by name
- How to create/run a process in the background & foreground, create/run a process in both areas
- kill the process that you created
- Install `nginx` in our VM
- create a `private-network` betweek localhost&vm
- allocate an IP address - for mac users 
- `sudo apt-get install nginx -y`
- How to check a tool/software status in linux `sudo systemctl status nginx`
- How to restart a process in Linux `
- Mac ip ranges `192.168.56.10` `192.168.56.11` `192.168.56.12`
- `vagrant reload` or `vagrant destroy` then `vagrant up` 
- `rm -rf .vagrant` then `vagrant up`
- `vagrant destroy` then `vagrant status`cd ..
- How to run node app in the background `nohup node app.js > /dev/null 2>&1 &`
- Remove the default `sudo rm /etc/nginx/sites-available/default`
- replace it with your own file `sudo cp existing-location /etc/nginx/sites-available/default`
-   `sudo nginx -t`
-   Restart `sudo systemctl restart nginx`
-   Enable  `sudo systemctl restart nginx`
- access nginx logs `/var/log/nginx`
  
### Linux Env Var
- sysntax NAME=SHAHRUKH
- How to check exiting env var `env` 
- `export` to create env var
  
### Creating 2 VMs
```
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
  ```
- mongodb set up
```
 be careful of these keys, they will go out of date
sudo apt-key adv --keyserver hkp://keyserver.ubuntu.com:80 --recv D68FA50FEA312927
echo "deb https://repo.mongodb.org/apt/ubuntu xenial/mongodb-org/3.2 multiverse" | sudo tee /etc/apt/sources.list.d/mongodb-org-3.2.list

sudo apt-get update -y
sudo apt-get upgrade -y

# sudo apt-get install mongodb-org=3.2.20 -y
sudo apt-get install -y mongodb-org=3.2.20 mongodb-org-server=3.2.20 mongodb-org-shell=3.2.20 mongodb-org-mongos=3.2.20 mongodb-org-tools=3.2.20
```