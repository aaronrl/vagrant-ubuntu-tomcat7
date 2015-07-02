# -*- mode: ruby -*-
# vi: set ft=ruby :

$script = <<SCRIPT
echo I am provisioning...

echo Running aptitude updates
sudo apt-get update
echo Upgrading Ubuntu installation
sudo apt-get -y upgrade
echo Installing packages for Tomcat installation
sudo apt-get -y install tomcat7 tomcat7-docs tomcat7-admin default-jdk git ant htop vim 

echo Recreating tomcat-users.xml with default user
rm /etc/tomcat7/tomcat-users.xml
echo "<?xml version='1.0' encoding='utf-8'?>" > /etc/tomcat7/tomcat-users.xml
echo "<tomcat-users>" >> /etc/tomcat7/tomcat-users.xml
echo '<user username="vagrant" password="vagrant" roles="manager-gui,admin-gui,manager-script,manager-jmx,manager-status" />' >> /etc/tomcat7/tomcat-users.xml
echo "</tomcat-users>" >> /etc/tomcat7/tomcat-users.xml

echo Assigning tomcat7 group to tomcat-users.xml
sudo chgrp tomcat7 /etc/tomcat7/tomcat-users.xml

echo Restarting tomcat7 service
sudo service tomcat7 restart

echo Ending provisioning
date > /etc/vagrant_provisioned_at
SCRIPT

Vagrant.configure("2") do |config|
  config.vm.box = "ubuntu/trusty64"
  config.vm.provision "shell", inline: $script

  config.vm.network :forwarded_port, guest: 8080, host: 4880
end
