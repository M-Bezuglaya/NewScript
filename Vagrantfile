BOX_IMAGE = 'bento/ubuntu-16.04'
NODE_COUNT = 1
Vagrant.configure("2") do |config|
  config.vm.box = "bento/ubuntu-16.04"
  config.vm.hostname = "ulitka"
  config.vm.network :private_network, ip: "192.168.56.42"
  id_rsa_pub = File.read("#{Dir.home}/.ssh/id_rsa.pub") 
  config.vm.provision "shell", inline: <<-SHELL
    echo \"#{id_rsa_pub}\" >> /home/vagrant/.ssh/authorized_keys
   SHELL

  config.vm.provider :virtualbox do |vb|
    vb.customize [
      "modifyvm", :id,
      "--cpuexecutioncap", "50",
      "--memory", "256",
]


#Vagrant.configure(2) do |config|

#  id_rsa_pub = File.read("#{Dir.home}/.ssh/id_rsa.pub")
#  config.vm.provision "copy ssh public key", type: "shell",
#    inline: "touch /home/vagrant/.ssh/authorized_keys_test"
#    inline: "echo \"#{id_rsa_pub}\" >> /home/vagrant/.ssh/authorized_keys_test" 
 end
end
