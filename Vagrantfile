Vagrant.configure('2') do |config|
  config.vm.box      = 'rails-vagrant'
  config.vm.hostname = 'rails-vagrant'

  # Ubuntu 12.04.4 LTS
  config.vm.box_url  = 'http://files.vagrantup.com/precise32.box'


  ### Private network and nfs folder sharing 

  config.vm.synced_folder "projects", "/home/vagrant/projects", :nfs => true
  config.vm.network "private_network", ip: "192.168.255.2"

  ### Public network and traditional folder sharing
  ### A rails server on a development environment is somewhat slow using this setup.
  ### But nfs folder sharing needs private networking, so there isn't much I can do about it (AFAIK).
  ### Uses dhcp so hit ifconfig after ssh'ing into the box if you want to know the ip
  # config.vm.synced_folder "projects", "/home/vagrant/projects"
  # config.vm.network "public_network", :bridge => 'en1: Wi-Fi (AirPort)'

  config.vm.provision "puppet" do |puppet|
    puppet.module_path = "modules"
  end
end
