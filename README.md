# Kernel update
<h2>Создание ВМ с помощью vagrant</h2>
1) Cоздаем Vagrantfile<br>
2) Запускаем виртуальную машину
<pre>vagrant up</pre>
3) Подключаемся по ssh к ВМ
<pre>vagrant ssh</pre>
4) Проверяем версию ядра
<pre>[root@kernel-uptade vagrant]# uname -r
4.18.0-516.el8.x86_64
</pre>

<h2>Обновляем ядро</h2>
1) Подключаем репозиторий 
<pre>sudo yum install -y https://www.elrepo.org/elrepo-release-8.el8.elrepo.noarch.rpm </pre>
2) Устанаваливаем последнее ядро из подключенного репозитория
<pre>sudo yum --enablerepo elrepo-kernel install kernel-ml -y</pre>
3) Обновляем конфигурацию загрузчика 
<pre>sudo grub2-mkconfig -o /boot/grub2/grub.cfg</pre>
4) Выбираем загрузку нового ядра по умолчанию
<pre>sudo grub2-set-default 0</pre>
5) Перезагружаем ВМ
<pre>sudo reboot</pre>
6) Проверяем версию ядра
<pre>[vagrant@kernel-uptade ~]$ uname -r
6.5.10-1.el8.elrepo.x86_64</pre>
7) Обновление завершено.

<h2>Обновления ядра с помощью Vagrant+shell</h2>
Добавлен Vagrantfile, который при запуске сразу обновляет ядро
