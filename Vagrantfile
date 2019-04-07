# -*- mode: ruby -*-
# vi: set ft=ruby :

# All Vagrant configuration is done below. The "2" in Vagrant.configure
# configures the configuration version (we support older styles for
# backwards compatibility). Please don't change it unless you know what
# you're doing.
Vagrant.configure("2") do |config|
  config.vm.box = "duckfez/centos-7"

  config.vm.provision "shell", inline: <<-SHELL
    wget https://download.splunk.com/products/splunk/releases/7.2.5.1/linux/splunk-7.2.5.1-962d9a8e1586-linux-2.6-x86_64.rpm > /dev/null 2>&1
    yum localinstall -y splunk-7.2.5.1-962d9a8e1586-linux-2.6-x86_64.rpm
    cp /vagrant/rules.d/99-splunk.rules /etc/polkit/rules.d
    cp /vagrant/bin/polkit_splunk /usr/local/bin/polkit_splunk
    chmod 755 /usr/local/bin/polkit_splunk
    systemctl restart polkit
  SHELL
end
