BOX_IMAGE = 'bento/ubuntu-16.04'
#NODE_COUNT = 2
Vagrant.configure("2") do |config|
config.vm.define "ulitka.local" do |subconfig|
  config.vm.box = "bento/ubuntu-16.04"
  config.vm.hostname = "ulitka"
  config.vm.network :private_network, ip: "192.168.31.249"
  config.vm.provider :virtualbox do |vb|
         vb.customize ["modifyvm", :id, "--cableconnected0", "on"]
         vb.memory = "2000"
	 vb.gui = true
   end
#  id_rsa_pub = File.read("#{Dir.home}/.ssh/id_rsa.pub")
   config.vm.provision "shell", inline: <<-SHELL
     SHELL
  end
config.vm.define "ulitka1.local" do |subconfig|
  config.vm.box = "bento/ubuntu-16.04"
  config.vm.hostname = "ulitka1"
  config.vm.network :private_network, ip: "192.168.31.250"
  config.vm.provider :virtualbox do |vb|
	 vb.customize ["modifyvm", :id, "--cableconnected0", "on"]
         vb.memory = "2000"
	 vb.gui = true
    end
#  id_rsa_pub = File.read("#{Dir.home}/.ssh/id_rsa.pub")
  config.vm.provision "shell", inline: <<-SHELL
   SHELL
   end

config.vm.define "ulitka2.local" do |subconfig|
config.vm.box = "bento/ubuntu-16.04"
  config.vm.hostname = "ulitka2"
  config.vm.network :private_network, ip: "192.168.31.251"
  config.vm.provider :virtualbox do |vb|
	 vb.customize ["modifyvm", :id, "--cableconnected0", "on"]
         vb.memory = "2000"
	 vb.gui = true
    end
#  id_rsa_pub = File.read("#{Dir.home}/.ssh/id_rsa.pub")
  config.vm.provision "shell", inline: <<-SHELL
   SHELL
   end
 end



#Vagrant.configure(2) do |config|

#  id_rsa_pub = File.read("#{Dir.home}/.ssh/id_rsa.pub")
#  config.vm.provision "copy ssh public key", type: "shell",
#    inline: "touch /home/vagrant/.ssh/authorized_keys_test"
#    inline: "echo \"#{id_rsa_pub}\" >> /home/vagrant/.ssh/authorized_keys_test" 


