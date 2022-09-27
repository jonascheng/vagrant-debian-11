$dockercompose = <<-SCRIPT
sudo curl -L "https://github.com/docker/compose/releases/download/1.29.2/docker-compose-$(uname -s)-$(uname -m)" -o /usr/local/bin/docker-compose
sudo chmod +x /usr/local/bin/docker-compose
sudo ln -s /usr/local/bin/docker-compose /usr/bin/docker-compose
SCRIPT

Vagrant.configure("2") do |config|
  if Vagrant.has_plugin?("vagrant-vbguest")
    config.vbguest.auto_update = false
  end
  
  config.vm.box = "debian/bullseye64"

  # Linux bullseye 5.10.0-13-amd64 #1 SMP Debian 5.10.106-1 (2022-03-17) x86_64 GNU/Linux
  # config.vm.box_version = "11.20220328.1"

  # Linux bullseye 5.10.0-8-amd64 #1 SMP Debian 5.10.46-4 (2021-08-03) x86_64 GNU/Linux
  config.vm.box_version = "11.20210829.1"

  config.vm.provision "docker"
  config.vm.provision "shell", inline: $dockercompose

  # config.vm.define "web" do |node|
  #   node.vm.network "private_network", type: "dhcp"
  # end
end
