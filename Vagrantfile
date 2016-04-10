########################################################################################################################
## Vagrant Configuration File
## --------------------------
##
## See README.md at https://github.com/aaronsaray/local-dev-server for documentation
########################################################################################################################

## Require 1.8 or above
Vagrant.require_version ">= 1.8.0"

## This manages hosts - and is necessary for the multiple hosts option and managing /etc/hosts properly
unless Vagrant.has_plugin?("vagrant-hostsupdater")
    raise 'vagrant-hostsupdater is not installed! Run "vagrant plugin install vagrant-hostsupdater"'
end

## Get the YAML module
require 'yaml'

## Load configuration file
config = YAML.load_file('config.yml')

## Main init
Vagrant.configure("2") do |box|

    ##network stuff
    box.vm.hostname = config["hostname"]
    box.vm.network "private_network", ip: config["private_network_ip"]

    ## the purpose of this is only local dev, so you can stay "bleeding edge"
    box.vm.box = "ubuntu/trusty64"  ## ubuntu/precise64

    ## sync up shared folder owned by vagrant, group of www-data, and changing permission to 775 persistently
    box.vm.synced_folder ".", "/vagrant", owner: "www-data", group: "www-data", mount_options: ["dmode=775,fmode=664"]

    ## Use virtualbox as the provider
    box.vm.provider :virtualbox do |vb|
        ## performance upgrades
        vb.customize ["modifyvm", :id, "--natdnshostresolver1", "on"]
        vb.customize ["modifyvm", :id, "--natdnsproxy1", "on"]

        ## MB of memory
        vb.memory = config["available_ram_mb"]
        vb.name = config["hostname"]
    end

    ## Provision with Ansible
    box.vm.provision "ansible" do |ansible|
        ansible.playbook = "ansible/playbook.yml"

        ## only "ok" for local dev boxes
        ansible.host_key_checking = false

        ## pass the server name into ansible
        ansible.extra_vars = {
            server_hostname: config["hostname"]
        }
    end
end