Vagrant.configure("2") do |config|
    config.vm.box = "centos/7"

    config.vm.network "forwarded_port", guest: 80, host: 8080

    $puppet_install = "
        sudo rpm -ivh /vagrant/files/puppetlabs-release-el-7.noarch.rpm
        sudo yum -y install puppet
    "

    config.vm.provision "shell", inline:$puppet_install

    config.vm.provision :puppet do |puppet|
        puppet.manifests_path = ["vm", "/vagrant/puppet/"] 
        puppet.manifest_file  = "manifests"
    end

    config.vm.provision "ansible" do |ansible|
        ansible.playbook = "emptyplaybook.yml"
    end
end
