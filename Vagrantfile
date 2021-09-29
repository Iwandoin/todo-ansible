Vagrant.configure(2) do |config|
  config.vm.box = "centos/8" #"bento/ubuntu-20.04" #
  config.vm.box_check_update = true
  config.vm.network "forwarded_port", guest: 80, host: 8080 # Webserver port

  config.vm.provider "virtualbox" do |vb|
    vb.memory = "2048"
  end

  config.vm.provision "ansible" do |ansible|
    ansible.playbook = "./b.yml"
  end

  config.vm.provider :virtualbox do |vb|
    vb.customize ["modifyvm", :id, "--natdnshostresolver1", "on"]
    vb.customize ["modifyvm", :id, "--natdnsproxy1", "on"]
  end
end

