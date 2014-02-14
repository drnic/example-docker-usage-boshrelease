# -*- mode: ruby -*-
# # vi: set ft=ruby :

Vagrant.configure("2") do |config|
  config.vm.box = "ubuntu-12.04.3-amd64"
  config.vm.box_url = "https://oss-binaries.phusionpassenger.com/vagrant/boxes/ubuntu-12.04.3-amd64-vbox.box"

  # docker-registry
  config.vm.network "forwarded_port", guest: 4243, host: 4243, auto_correct: true
  config.vm.network "forwarded_port", guest: 5000, host: 5000, auto_correct: true

  config.vm.provision "shell", path: 'scripts/prepare_vagrant_docker.sh'
end
