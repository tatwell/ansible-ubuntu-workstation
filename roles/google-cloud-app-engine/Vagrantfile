# -*- mode: ruby -*-
# vi: set ft=ruby :

Vagrant.configure(2) do |config|
  # Set box type.
  config.vm.box = "ubuntu/trusty64"

  # Run Ansible to provision the Vagrant guest.
  config.vm.provision :ansible do |ansible|
    ansible.playbook = "test/playbook.yml"
  end

end
