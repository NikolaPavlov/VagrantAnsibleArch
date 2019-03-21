Vagrant.configure("2") do |config|
    config.vm.box = "archlinux/archlinux"
    config.vm.network :private_network, ip: "192.168.111.111"
    config.vm.hostname = "archy-official"
    config.vm.define "archy-official"
    config.vm.provider :virtualbox do |vb|
        vb.name = "archy-official"
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
