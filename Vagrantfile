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
end

