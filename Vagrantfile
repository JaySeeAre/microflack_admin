# -*- mode: ruby -*-
# vi: set ft=ruby :

$script = <<SCRIPT
# make sure scripts have the executable bit set (Windows may not preserve this bit)
chmod +x /tmp/setup-host.sh /tmp/setup-all-in-one.sh

# install base dependencies (run as root)
/tmp/setup-host.sh

# install microflack (run as user ubuntu)
exec su -c /tmp/setup-all-in-one.sh -l ubuntu
SCRIPT

Vagrant.configure("2") do |config|
  config.vm.box = "bento/ubuntu-16.04"
  config.vm.network "private_network", ip: "192.168.33.10"
  config.vm.provider "hyperv" do |h|
    h.memory = "1536"
  end
  config.vm.provision "file", source: "install/setup-host.sh", destination: "/tmp/setup-host.sh"
  config.vm.provision "file", source: "install/setup-all-in-one.sh", destination: "/tmp/setup-all-in-one.sh"
  config.vm.provision "shell", inline: $script
end
