
require 'rbconfig'

Vagrant.configure(2) do |config|
  
  config.vm.provider "virtualbox" do |vb|
    vb.customize ["modifyvm", :id, "--memory", "512"]
  end

  config.vm.box = "insaneworks/centos"

  config.vm.define "ansbox" do |ansbox|
    ansbox.vm.provision "shell", inline: <<-SHELL
      echo 'LANG="en_US.UTF-8"' > /etc/sysconfig/i18n
      yum install -y https://dl.fedoraproject.org/pub/epel/6/x86_64/epel-release-6-8.noarch.rpm
      yum install -y ansible
    SHELL
    ansbox.vm.network "private_network", ip: "192.168.31.54"
  end

  config.vm.define "empty" do |empty|
    empty.vm.network "private_network", ip: "192.168.31.55"
  end

end
