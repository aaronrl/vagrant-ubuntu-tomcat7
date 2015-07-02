# vagrant-ubuntu-tomcat7
A vagrant box for Tomcat7 using only a shell provisioner.

The Vagrantfile uses the 64-bit Ubuntu 14.04 ubuntu/trusty64 Vagrant box image.  It maps the default Tomcat7 web port 8080 to the hosts port 4880.

The following packages are installed during the provisioning step:
* tomcat7
* tomcat7-docs
* tomcat7-admin
* git
* ant
* htop
* vim
* default-jdk

The provisioner also sets up a default user for the manager webapp.  The username is 'vagrant' and password is 'vagrant'.  It is granted the 'manager-gui', 'manager-script', 'manager-jmx', 'manager-status', and 'admin-gui' roles.
