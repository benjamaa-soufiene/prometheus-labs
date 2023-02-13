Vagrant.configure("2") do |config|  
#  config.vm.provider "virtualbox"
  config.vm.provider "virtualbox" do |v|
        v.customize ["modifyvm", :id, "--memory", "4096"]
  end

  config.vm.define "ansible" do |ansible|
    ansible.vm.box = "generic/ubuntu2004"
    ansible.vm.hostname = "ansible"
    ansible.vm.network :private_network, ip: "192.168.56.10"
  end

  config.vm.provision "shell", inline: <<-SHELL
    sudo systemctl disable systemd-resolved
    sudo rm -rf /etc/run/systemd/resolve/stub-resolv.conf /etc/resolv.conf
    sudo echo "nameserver  8.8.8.8" > /etc/resolv.conf
  SHELL

end
