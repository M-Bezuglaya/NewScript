Vagrant.configure("2") do |config|
  config.vm.define "ulitka1" do |subconfig|
     subconfig.vm.box = "bento/ubuntu-20.04"
     subconfig.vm.hostname = "ulitka1"
     subconfig.vm.network :private_network, ip: "192.168.31.250"
     subconfig.vm.provision "shell", inline: <<-SHELL
      echo /home/ulitka/.ssh/id_rsa.pub >> /home/ulitka/NewScript/public_keys
      echo /home/ulitka/NewScript/public_keys >> /home/vagrant/.ssh/authorized_keys

     SHELL

     subconfig.vm.provider :virtualbox do |vb|
      vb.name = "ulitka1"
      vb.gui = false
      vb.memory = "1024"
   end
      subconfig.vm.provision "file", source: "/home/ulitka/.ssh/id_rsa.pub", destination: "~/.ssh/authorized_keys"
 #    id_rsa_pub = File.read("#{Dir.home}/.ssh/id_rsa.pub")
      subconfig.vm.provision "shell", inline: <<-SHELL
      echo '[main]' >> /etc/hosts
      echo '192.168.31.249 ulitka puppet' >> /etc/hosts
      echo '192.168.31.250 ulitka1' >> /etc/hosts
      sudo apt-get install -y ntp
      wget https://apt.puppetlabs.com/puppet6-release-focal.deb
      dpkg -i puppet6-release-focal.deb
      sudo apt-get update -y
      sudo apt-get install puppet-agent -y
      echo '[main]' >> /etc/puppetlabs/puppet/puppet.conf
      echo 'certname = ulitka1' >> /etc/puppetlabs/puppet/puppet.conf
      echo 'server = ulitka' >> /etc/puppetlabs/puppet/puppet.conf
      echo 'runinterval = 150' >> /etc/puppetlabs/puppet/puppet.conf
      sudo systemctl start puppet
      sudo systemctl enable puppet
 #    systemctl status puppet

  SHELL

  end

  config.vm.define "ulitka" do |subconfig|
     subconfig.vm.box = "bento/ubuntu-20.04"
     subconfig.vm.hostname = "ulitka"
     subconfig.vm.network :private_network, ip: "192.168.31.249"
     subconfig.vm.provision "shell", inline: <<-SHELL
       echo /home/ulitka/.ssh/id_rsa.pub >> /home/ulitka/NewScript/public_keys
       echo /home/ulitka/NewScript/public_keys >> /home/vagrant/.ssh/authorized_keys

      SHELL

     subconfig.vm.provider :virtualbox do |vb|
       vb.name = "ulitka"
       vb.gui = false
       vb.memory = "1024"
   end
     subconfig.vm.provision "file", source: "/home/ulitka/.ssh/id_rsa.pub", destination: "~/.ssh/authorized_keys"
 #   id_rsa_pub = File.read("#{Dir.home}/.ssh/id_rsa.pub")
     subconfig.vm.provision "shell", inline: <<-SHELL
     echo '[main]' >> /etc/hosts
     echo '192.168.31.249 ulitka puppet' >> /etc/hosts
     echo '192.168.31.250 ulitka1' >> /etc/hosts
     sudo apt-get install -y ntp
     sudo apt-get install -y
     sudo apt-get update -y
     wget https://apt.puppetlabs.com/puppet6-release-focal.deb
     dpkg -i puppet6-release-focal.deb
     sudo apt-get update -y
     sudo apt-get install puppetserver -y
     sed -i 's/.*JAVA_ARGS.*/JAVA_ARGS="-Xms512m -Xmx512m -Djruby.logger.class=com.puppetlabs.jruby_utils.jruby.Slf4jLogger"/' /etc/default/puppetserver
     echo '[main]' >> /etc/puppetlabs/puppet/puppet.conf
     echo 'certname = ulitka' >> /etc/puppetlabs/puppet/puppet.conf
     echo 'server = ulitka' >> /etc/puppetlabs/puppet/puppet.conf
     sudo systemctl start puppetserver
     sudo systemctl enable puppetserver
#    systemctl status puppetserver
     sleep 120 
 
     sudo /opt/puppetlabs/bin/puppetserver ca list --all
     sudo /opt/puppetlabs/bin/puppetserver ca sign --all
     sudo /opt/puppetlabs/bin/puppet agent --test
 
   SHELL


  end

end





#Vagrant.configure("2") do |config|
#  config.vm.define "ulitka.local" do |subconfig|
#     subconfig.vm.box = "bento/ubuntu-20.04"
#     subconfig.vm.hostname = "ulitka"
#     subconfig.vm.network :private_network, ip: "192.168.31.249"

#     subconfig.vm.provision "shell", inline: <<-SHELL
#       echo /home/ulitka/.ssh/id_rsa.pub >> /home/ulitka/NewScript/public_keys
#       echo /home/ulitka/NewScript/public_keys >> /home/vagrant/.ssh/authorized_keys

#      SHELL

#   config.vm.provider :virtualbox do |vb|
#     vb.name = "ulitka"
#     vb.gui = false
#     vb.memory = "1024"
#   end

#     id_rsa_pub = File.read("#{Dir.home}/.ssh/id_rsa.pub")
#     subconfig.vm.provision "shell", inline: <<-SHELL
#     echo '[main]' >> /etc/hosts
#     echo '192.168.31.249 ulitka puppet' >> /etc/hosts
#     echo '192.168.31.250 ulitka1' >> /etc/hosts
#     apt-get install -y ntp
#     apt-get install -y
#     apt-get update -y
#     wget https://apt.puppetlabs.com/puppet6-release-focal.deb
#     dpkg -i puppet6-release-focal.deb
#     apt-get update -y
#     apt-get install puppetserver -y
#     sed -i 's/.*JAVA_ARGS.*/JAVA_ARGS="-Xms512m -Xmx512m -Djruby.logger.class=com.puppetlabs.jruby_utils.jruby.Slf4jLogger"/' /etc/default/puppetserver
#     echo '[main]' >> /etc/puppetlabs/puppet/puppet.conf
#     echo 'certname = ulitka' >> /etc/puppetlabs/puppet/puppet.conf
#     echo 'server = ulitka' >> /etc/puppetlabs/puppet/puppet.conf
#     systemctl start puppetserver
#     systemctl enable puppetserver
#     systemctl status puppetserver

#   SHELL

#     subconfig.vm.provision "file", source: "/home/ulitka/.ssh/id_rsa.pub", destination: "~/.ssh/authorized_keys"
#  end

#     config.vm.define "ulitka1.local" do |subconfig|
#     subconfig.vm.box = "bento/ubuntu-20.04"
#     subconfig.vm.hostname = "ulitka1"
#     subconfig.vm.network :private_network, ip: "192.168.31.250"

#    subconfig.vm.provision "shell", inline: <<-SHELL
#      echo /home/ulitka/.ssh/id_rsa.pub >> /home/ulitka/NewScript/public_keys
#      echo /home/ulitka/NewScript/public_keys >> /home/vagrant/.ssh/authorized_keys

#     SHELL

#    subconfig.vm.provider :virtualbox do |vb|
#      vb.name = "ulitka1"
#      vb.gui = false
#      vb.memory = "1024"
#   end

#      id_rsa_pub = File.read("#{Dir.home}/.ssh/id_rsa.pub")
#      subconfig.vm.provision "shell", inline: <<-SHELL
#      echo '[main]' >> /etc/hosts
#      echo '192.168.31.249 ulitka puppet' >> /etc/hosts
#      echo '192.168.31.250 ulitka1' >> /etc/hosts
#      apt-get install -y ntp
#      wget https://apt.puppetlabs.com/puppet6-release-focal.deb
#      dpkg -i puppet6-release-focal.deb
#      apt-get update -y
#      apt-get install puppet-agent -y
#      echo '[main]' >> /etc/puppetlabs/puppet/puppet.conf
#      echo 'certname = ulitka1' >> /etc/puppetlabs/puppet/puppet.conf
#      echo 'server = ulitka' >> /etc/puppetlabs/puppet/puppet.conf
#      echo 'runinterval=200' >> /etc/puppetlabs/puppet/puppet.conf
#      systemctl start puppet
#      systemctl enable puppetserver
#      systemctl status puppet
  
#  SHELL
#    subconfig.vm.provision "file", source: "/home/ulitka/.ssh/id_rsa.pub", destination: "~/.ssh/authorized_keys"

#  end

#end



	
