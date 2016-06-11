Vagrant.configure(2) do |config|

  config.vm.box = "ubuntu/trusty64"
  config.vm.hostname="macubuntua"

  config.vm.network "private_network", ip: "192.168.59.4"
  
  config.vm.provider "virtualbox" do |v|
      v.name = "macubuntua"  
      v.memory = 2048
      v.cpus = 1
  end
  
  # shared directory
  config.vm.synced_folder "/Users/kiwenlau/ubuntu", "/home/vagrant/mac"
  
  # install docker 1.11.0
  config.vm.provision "shell", inline: <<-SHELL
     apt-get update
     apt-get install apt-transport-https ca-certificates
     apt-key adv --keyserver hkp://p80.pool.sks-keyservers.net:80 --recv-keys 58118E89F3A912897C070ADBF76221572C52609D
     echo deb https://apt.dockerproject.org/repo ubuntu-trusty main > /etc/apt/sources.list.d/docker.list
     apt-get update;
     apt-get install -y -q docker-engine=1.11.0-0~trusty
     usermod -aG docker vagrant
  SHELL

end
