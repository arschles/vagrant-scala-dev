# -*- mode: ruby -*-
# vi: set ft=ruby :

VAGRANTFILE_API_VERSION = "2"

$script = <<SCRIPT
apt-get update
apt-get -y install openjdk-6-jdk
wget http://www.scala-lang.org/files/archive/scala-2.11.2.deb
dpkg -i scala-2.11.2.deb
apt-get -y update
apt-get -y install scala

wget http://dl.bintray.com/sbt/debian/sbt-0.13.5.deb
dpkg -i sbt-0.13.5.deb
apt-get -y update
apt-get -y install sbt
SCRIPT

Vagrant.configure(VAGRANTFILE_API_VERSION) do |config|
    config.vm.define "scala", primary: true do |scala|
        scala.vm.box = "hashicorp/precise64"
        scala.vm.provision "shell", inline: $script
    end

    config.vm.provider "virtualbox" do |vb|
        vb.memory = 2048
        vb.customize ["modifyvm", :id, "--cpuexecutioncap", "50"]
    end
end
