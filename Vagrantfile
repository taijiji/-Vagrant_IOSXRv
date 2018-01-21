# -*- mode: ruby -*-
# vi: set ft=ruby :

Vagrant.configure("2") do |config|
  config.vm.define :iosxrv1 do |iosxrv1|
    iosxrv1.vm.box = "IOS-XRv"
    iosxrv1.vm.network :private_network, virtualbox__intnet: "link1", auto_config: false
    iosxrv1.vm.provision "file", source: "configs/xrconf.txt", destination: "/home/vagrant/xrconf.txt"

    iosxrv1.vm.provision "shell" do |s|
      s.path =  "./scripts/apply_config.sh"
      s.args = ["/home/vagrant/xrconfig"]
    end
  end
end