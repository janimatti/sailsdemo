Vagrant.configure("2") do |config|
  #Uncomment to enable virtualmachine boot debug
  #config.vm.provider "virtualbox" do |v|
  #  v.gui = true
  #end

  config.vm.provider "virtualbox" do |v|
    v.customize ["modifyvm", :id, "--memory", "2048"]
  end

  config.vm.define :sailsdemo do |config|
    #config.vm.network :forwarded_port, host: 4567, guest: 80
    #config.vm.synced_folder ".", "/vagrant", :nfs => true
    config.vm.synced_folder ".", "/vagrant", :nfs => { :mount_options => ['dmode=770','fmode=770'] }
    config.vm.box = "precise64"
    config.vm.box_url = "http://files.vagrantup.com/precise64.box"
    config.vm.network :private_network, ip: "192.168.111.127"
    config.vm.provision :ansible do |ansible|
      ansible.verbose = "vvvv"
      ansible.playbook = "provisioning/playbook.yml"
      ansible.inventory_path = "provisioning/ansible_hosts"
    end
  end
end