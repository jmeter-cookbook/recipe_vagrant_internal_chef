Vagrant.configure "2" do |config|

  # See https://github.com/mitchellh/vagrant/wiki/Available-Vagrant-Boxes for more boxes.
  config.vm.box     = "precise64_base"
  config.vm.box_url = "http://files.vagrantup.com/precise64.box"

  config.vm.provider "virtualbox" do |vm|
    vm.customize ["modifyvm", :id, "--nictype1", "Am79C973", "--memory", "1536", "--cpus", "2", "--ioapic", "on"]
    vm.customize ["modifyvm", :id, "--rtcuseutc", "on"]
  end

  ## forward some ports
  config.vm.network :public_network

  config.vm.provision :chef_solo do |chef|
    chef.cookbooks_path = ["cookbooks"]
    chef.log_level      = :debug

    chef.add_recipe     "apt"
    chef.add_recipe     "git"
    chef.add_recipe     "java::openjdk7"
    chef.add_recipe     "jmeter"
  end
end
