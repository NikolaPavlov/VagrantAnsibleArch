Vagrant.configure("2") do |config|
    config.vm.box = "archlinux/archlinux"
    config.vm.network :private_network, ip: "192.168.111.111"
    # config.vm.network :public_network
    # config.vm.network "forwarded_port", host: 8080, guest: 80
    config.vm.hostname = "archy"
    config.vm.define "archy"
    config.vm.provider :virtualbox do |vb|
        vb.name = "archy"
    end

    ####### Provision #######

    # Ansible need python on the guest machine to be able to work
    config.vm.provision "shell", inline: "which python || sudo pacman -S python --noconfirm"

    config.vm.provision "ansible" do |ansible|
        ansible.compatibility_mode = '2.0'
        ansible.playbook = "provision/playbook.yml"
        ansible.verbose = true
    end
end
