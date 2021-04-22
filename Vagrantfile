## -*- mode: ruby -*-
# vi: set ft=ruby :

# All Vagrant configuration is done below. The "2" in Vagrant.configure
# configures the configuration version (we support older styles for
# backwards compatibility). Please don't change it unless you know what
# you're doing.

# bloque de configuracion estandar requerrido en todos los archivo
Vagrant.configure("2") do |config|
 # The most common configuration options are documented and commented below.
 # For a complete reference, please see the online documentation at
 # https://docs.vagrantup.com.

 # Every Vagrant development environment requires a box. You can search for
 # boxes at https://vagrantcloud.com/search.
 #configuracion del .vm box
 config.vm.box = "ubuntu/bionic64"
 config.vm.box_version = "~> 20200304.0.0"
#configuracion .vmbox crea puerto desde nuestra maquina local
 config.vm.network "forwarded_port", guest: 8000, host: 8000
#bloqueo de provision.. ejecutar scrips cuando se crea servidor por primera vez
 config.vm.provision "shell", inline: <<-SHELL
   systemctl disable apt-daily.service
   systemctl disable apt-daily.timer
# aquí esta línea de actualización que actualizará el repositorio local con
#todos los paquetes disponibles para que podamos
#instalar Python 3 virtual env y zip
   sudo apt-get update
   sudo apt-get install -y python3-venv zip
#crear archivo bash
   touch /home/vagrant/.bash_aliases
   if ! grep -q PYTHON_ALIAS_ADDED /home/vagrant/.bash_aliases; then
     echo "# PYTHON_ALIAS_ADDED" >> /home/vagrant/.bash_aliases
     echo "alias python='python3'" >> /home/vagrant/.bash_aliases
   fi
 SHELL
end
