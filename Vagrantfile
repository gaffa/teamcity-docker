# -*- mode: ruby -*-
# vi: set ft=ruby :
 
# Vagrantfile API/syntax version. Don't touch unless you know what you're doing!
VAGRANTFILE_API_VERSION = "2"

Vagrant.configure(VAGRANTFILE_API_VERSION) do |config|

  config.vm.box = "precise64"
  config.vm.box_url = "https://cloud-images.ubuntu.com/vagrant/precise/current/precise-server-cloudimg-amd64-vagrant-disk1.box"

  config.vm.define vm_name = "teamcityhost" do |config|

    config.vm.hostname = "teamcityhost"
    config.vm.network :private_network, ip: "172.17.8.2"

    config.vm.provider "virtualbox" do |v|
        v.memory = 4096
        v.cpus = 2
    end

    # share folder with host
    config.vm.synced_folder ".", "/home/core/share"

    # expose ports
    config.vm.network :forwarded_port, guest: 8111, host: 8111, auto_correct: true
  end

  config.vm.provision "docker" do |d|
  end
end