# -*- mode: ruby -*-
# vi: set ft=ruby :

VAGRANTFILE_API_VERSION = "2"

Vagrant.configure(VAGRANTFILE_API_VERSION) do |config|

  config.vm.box = "nZac/base-ubuntu-lts"

  config.vm.network :private_network, ip: "192.168.30.10"

  config.vm.synced_folder ENV.fetch("SKOSHAPPS", "") , "/opt/apps", type: "nfs"

  config.vm.provision "ansible" do |ansible|
    ansible.playbook = "provision/site.yml"
    ansible.inventory_path = "provision/inventory"
    ansible.limit = "all"
    if ENV.fetch("TAGS", "") != ""
        ansible.tags = ENV["TAGS"]
    end
    ansible.extra_vars = {
        "mysql_host_ips"=> ["192.168.30.1"]
    }
  end

end

