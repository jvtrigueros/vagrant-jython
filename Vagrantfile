# -*- mode: ruby -*-
# vi: set ft=ruby :

Vagrant.configure(2) do |config|
  config.vm.box = "ubuntu/trusty64"

  # config.vm.provider "virtualbox" do |vb|
  #   # Display the VirtualBox GUI when booting the machine
  #   vb.gui = true
  #
  #   # Customize the amount of memory on the VM:
  #   vb.memory = "1024"
  # end

  # Define a Vagrant Push strategy for pushing to Atlas. Other push strategies
  # such as FTP and Heroku are also available. See the documentation at
  # https://docs.vagrantup.com/v2/push/atlas.html for more information.
  # config.push.define "atlas" do |push|
  #   push.app = "YOUR_ATLAS_USERNAME/YOUR_APPLICATION_NAME"
  # end

  config.vm.provision "shell", inline: <<-SHELL
    apt-get update
    apt-get install -y openjdk-7-jdk git
    wget -O /tmp/jython-installer.jar "http://search.maven.org/remotecontent?filepath=org/python/jython-installer/2.7-rc3/jython-installer-2.7-rc3.jar"
    java -jar /tmp/jython-installer.jar -s -d /opt/jython
    /opt/jython/bin/pip install virtualenv
    
    su - vagrant -c "git clone https://github.com/jythontools/pip.git --depth 1"
    su - vagrant -c "git clone https://github.com/jythontools/setuptools.git --depth 1"
    su - vagrant -c "/opt/jython/bin/virtualenv venv --no-setuptools"
  SHELL
end
