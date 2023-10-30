Vagrant.configure("2") do |config|
  config.vm.box = "debian/bullseye64"
  config.vm.hostname = "gp1f4a7blue.fjeclot.net"
  config.vm.provider "virtualbox" do |v|
    v.name = "gp1f4a7blue" 
    v.memory = 2048
    v.cpus = 2
    v.customize ['modifyvm', :id, '--clipboard', 'bidirectional']
  end

  config.vm.network "public_network", type: "dhcp", bridge: "nombre_de_la_teua_xarxa"
  config.vm.synced_folder "../codi", "/home/vagrant/gp1f4a7/codi"  # Ajusta la ruta de la carpeta compartida si és diferent

  config.vm.provision "shell", inline: <<-SHELL    
    sudo apt-get update -y
    sudo apt-get upgrade -y
    sudo apt-get install -y aptitude
    sudo apt-get install -y net-tools
    sudo apt-get install -y zip
    sudo apt-get install -y unzip
    sudo apt-get install -y git
    sudo apt-get install -y curl
    sudo curl -fsSL https://download.docker.com/linux/debian/gpg | sudo gpg --dearmor -o /usr/share/keyrings/docker-archive-keyring.gpg
    sudo echo "deb [arch=amd64 signed-by=/usr/share/keyrings/docker-archive-keyring.gpg] https://download.docker.com/linux/debian $(lsb_release -cs) stable" | sudo tee /etc/apt/sources.list.d/docker.list > /dev/null
    sudo apt-get update -y
    sudo apt-get install -y docker-ce docker-ce-cli containerd.io
    sudo usermod -aG docker vagrant
    sudo apt-get install -y docker-compose
    apt-get install -y docker.io
    sudo chown -R vagrant:vagrant /home/vagrant/gp1f4a7
    usermod -aG docker vagrant
  SHELL
end