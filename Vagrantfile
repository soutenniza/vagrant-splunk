VAGRANTFILE_API_VERSION = "2"

$script = <<SCRIPT
sudo su -
cd /vagrant/
rpm -i splunk-6.2.4-271043-linux-2.6-x86_64.rpm
cat /vagrant/inputs.txt >> /opt/splunk/etc/system/default/inputs.conf
/opt/splunk/bin/splunk start --accept-license
SCRIPT

Vagrant.configure(VAGRANTFILE_API_VERSION) do |config|

  config.vm.network "private_network", ip: "192.168.13.37"
  config.vm.box = "centos6464"
  config.vm.network "forwarded_port", guest: 8000, host: 8000
  config.vm.network "forwarded_port", guest: 7004, host: 7004
  config.vm.network "forwarded_port", guest: 7005, host: 7005
  config.vm.box_url = "https://github.com/2creatives/vagrant-centos/releases/download/v6.4.2/centos64-x86_64-20140116.box"
  config.vm.provision "shell", inline: $script

end
