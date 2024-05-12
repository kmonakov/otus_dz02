# otus_dz02
kernel update

# Рядом лежит Vagrantfile, которым поднимал виртуалку, соответственно.
# ставил из локального файла, скачал, добавил бокс в Vagrant
  vagrant box add --name 'centos8s' /c/users/kirill/Downloads/65f2c95f-c675-447a-98d0-6014d42a139d
# Проверил, что он залился и доступен, параллельно поменял имя в конфиге и закомментил указание версии, с ней не взлетало
  vagrant box list | grep centos
# Поднял виртуалку
  vagrant up
# Подключился к виртуалке по SSH
  vagrant ssh
# Проверил версию ядра
  uname -r
  4.18.0-513.el8.x86_64
# Обновил ядро из elrepo
  sudo yum install -y https://www.elrepo.org/elrepo-release-8.el8.elrepo.noarch.rpm 
  sudo yum --enablerepo elrepo-kernel install kernel-ml -y
# Обновил загрузчик, поставил новое ядро загружаться по умолчанию, отправил перезагружаться
  sudo grub2-mkconfig -o /boot/grub2/grub.cfg
  sudo grub2-set-default 0
  sudo reboot
# Проверил версию ядра после перезагрузки
  uname -r
  6.8.9-1.el8.elrepo.x86_64
