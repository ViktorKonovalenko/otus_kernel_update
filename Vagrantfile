# -*- mode: ruby -*-
# vi: set ft=ruby :

#Параметры указываются в цикле

Vagrant.configure("2") do |config|

  #Указываем, какую ОС мы будем использовать
  config.vm.box = "generic/centos8s"
  # Задаем hostname
  config.vm.hostname = "kernel-uptade"
  #Указываем настройки спецификации ВМ
  #Указывается в отдельном цикле
  config.vm.provider "virtualbox" do |vb|
     # Указываем количество ОЗУ и ядер процессора
     vb.memory = "1024"
     vb.cpus = "2"
  end
  config.vm.provision "shell", inline: <<-SHELL
      sudo yum install -y https://www.elrepo.org/elrepo-release-8.el8.elrepo.noarch.rpm
      yum --enablerepo elrepo-kernel install kernel-ml -y
      grub2-mkconfig -o /boot/grub2/grub.cfg
      grub2-set-default 0
      echo "Grub update done."
      shutdown -r now
  SHELL
end
