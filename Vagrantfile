$pre_provision = <<SCRIPT
sudo apt update
sudo apt upgrade -y
SCRIPT

Vagrant.configure("2") do |config|
    config.vm.box = "ubuntu/focal64"

    config.vm.define "edn"

    config.vm.network "forwarded_port", guest: 8000, host: 8000

    config.vm.provision "shell", inline: $pre_provision
    config.vm.provision "ansible" do |ansible|
        ansible.compatibility_mode = "2.0"
        ansible.playbook = "playbook.yaml"
    end
end
