# -*- mode: ruby -*-
# vi: set ft=ruby :

class FixGuestAdditions < VagrantVbguest::Installers::Linux
    def install(opts=nil, &block)
        communicate.sudo("yum update kernel -y; yum install -y gcc binutils make perl bzip2 kernel-devel kernel-headers", opts, &block)
        super
    end
end

Vagrant.configure(2) do |config|
  config.vm.box = "centos/7"
  config.vbguest.installer = FixGuestAdditions

  config.vm.provision "ansible" do |ansible|
    ansible.verbose = "vvv"
    ansible.playbook = "provisioning/playbook.yml"
    ansible.sudo = "true"
  end


  config.vm.provider "virtualbox" do |v|
	  v.memory = 256
  end

  config.vm.define "ns01" do |ns01|
    ns01.vm.network "private_network", ip: "192.168.50.10", virtualbox__intnet: "dns"
    ns01.vm.hostname = "ns01"
  end

  config.vm.define "ns02" do |ns02|
    ns02.vm.network "private_network", ip: "192.168.50.11", virtualbox__intnet: "dns"
    ns02.vm.hostname = "ns02"
  end

  config.vm.define "client1" do |client1|
    client1.vm.network "private_network", ip: "192.168.50.15", virtualbox__intnet: "dns"
    client1.vm.hostname = "client1"
  end
  config.vm.define "client2" do |client2|
    client2.vm.network "private_network", ip: "192.168.50.14", virtualbox__intnet: "dns"
    client2.vm.hostname = "client2"
  end
end
