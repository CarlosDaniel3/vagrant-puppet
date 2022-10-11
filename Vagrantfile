#Author: CarryOn Tech
Vagrant.configure("2") do |config|

#Informando ao Vagrant que vamos utilizar uma máquina ubuntu
    config.vm.box = "ubuntu/trusty64"

    #Configurando a VM de aplicação
    config.vm.define:app do |app_config|
        app_config.vm.network "forwarded_port", guest: 80, host:8090
        #Instalando o Puppet na VM
        app_config.vm.provision "shell", inline: "sudo apt-get update && sudo apt-get install -y puppet"
        #Informando ao Vagrant para prosseguir com o provisionamento utilizando o puppet
        app_config.vm.provision "puppet" do |puppet|
            puppet.manifest_file = "app.pp"
        end
        #Utilizando o Virtualbox como provider (Onde a VM será criada => Virtualbox)
        app_config.vm.provider:virtualbox do |v|
            v.memory = 1024
            v.cpus = 1
        end
    end
end



