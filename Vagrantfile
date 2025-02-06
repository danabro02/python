Vagrant.configure("2") do |config|
  config.vm.box = "debian/bullseye64"

  config.vm.provider "virtualbox" do |vb|
    vb.memory = "2048"
    vb.linked_clone = true
  end

  config.vm.provision "update", type: "shell", inline: <<-SHELL
    apt-get update 
  SHELL

  config.vm.define "prueba" do |prueba|
    prueba.vm.hostname = "prueba"
    prueba.vm.network "private_network", ip: "192.168.56.10"

    prueba.vm.provision "bind9-install", type: "shell", inline: <<-SHELL
        apt-get install -y bind9 bind9-utils bind9-doc
    SHELL
  end
end