IMAGE = "bento/ubuntu-20.04"
Vagrant.configure("2") do |config|
    config.vm.provision "shell", inline: <<-SHELL
        apt-get update -y
        echo "172.16.73.100  master-node" >> /etc/hosts
        echo "172.16.73.11  worker-node01" >> /etc/hosts
        echo "172.16.73.12  worker-node02" >> /etc/hosts
    SHELL
    
    config.vm.define "master" do |master|
      master.vm.box = IMAGE
      master.vm.hostname = "master-node"
      master.vm.network "private_network", ip: "172.16.73.100"
      master.vm.provider "vmware_desktop" do |vb|
          vb.memory = 6048
          vb.cpus = 2
          vb.vmx["virtualhw.version"] = 18
          vb.gui = true
      end
      master.vm.provision "shell", path: "scripts/common.sh"
      master.vm.provision "shell", path: "scripts/master.sh"
    end

    (1..2).each do |i|
  
    config.vm.define "node0#{i}" do |node|
      node.vm.box = IMAGE
      node.vm.hostname = "worker-node0#{i}"
      node.vm.network "private_network", ip: "172.16.73.1#{i}"
      node.vm.provider "vmware_desktop" do |vb|
          vb.memory = 3048
          vb.cpus = 1
          vb.vmx["virtualhw.version"] = 18
          vb.gui = true
      end
      node.vm.provision "shell", path: "scripts/common.sh"
      node.vm.provision "shell", path: "scripts/node.sh"
     end
    end
  end
