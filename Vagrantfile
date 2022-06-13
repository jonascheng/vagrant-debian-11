$dockercompose = <<-SCRIPT
sudo curl -L "https://github.com/docker/compose/releases/download/1.29.2/docker-compose-$(uname -s)-$(uname -m)" -o /usr/local/bin/docker-compose
sudo chmod +x /usr/local/bin/docker-compose
sudo ln -s /usr/local/bin/docker-compose /usr/bin/docker-compose
SCRIPT

Vagrant.configure("2") do |config|
  config.vm.box = "debian/bullseye64"
  config.vm.box_version = "11.20220328.1"
  config.vm.provision "docker"
  config.vm.provision "shell", inline: $dockercompose

  config.vm.define "web" do |node|
    node.vm.network "private_network", type: "dhcp"
  end
end