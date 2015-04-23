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
    JYTHON_VERSION=2.7-rc3
    wget -O /tmp/jython-installer.jar "http://search.maven.org/remotecontent?filepath=org/python/jython-installer/$JYTHON_VERSION/jython-installer-$JYTHON_VERSION.jar"
    java -jar /tmp/jython-installer.jar -s -d /opt/jython
    /opt/jython/bin/pip install virtualenv

    echo 'PATH=/opt/jython/bin:$PATH' >> /etc/profile
    
    su - vagrant -c "git clone https://github.com/jythontools/pip.git --depth 1"
    su - vagrant -c "git clone https://github.com/jythontools/setuptools.git --depth 1"
    su - vagrant -c "virtualenv venv --no-setuptools"
  SHELL
end
