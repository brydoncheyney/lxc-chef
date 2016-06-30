# Vagrantfile API/syntax version
VAGRANTFILE_API_VERSION = '2'

required_plugins = %w(vagrant-omnibus)

required_plugins.each do |plugin|
  system "vagrant plugin install #{plugin}" unless Vagrant.has_plugin? plugin
end

Vagrant.configure(VAGRANTFILE_API_VERSION) do |config|

  config.vm.box = 'cheyneb/centos-6-64-lxc'

  config.ssh.insert_key = false

  #config.omnibus.chef_version = :latest
  config.omnibus.chef_version = '12.8.1'

  config.vm.define :default do |instance|
    if Vagrant.has_plugin?('vagrant-hosts')
      instance.vm.provision :hosts
    end

    instance.vm.provision :chef_solo do |chef|
      chef.cookbooks_path = %w(chef/cookbooks ../external-cookbooks)
      chef.add_recipe 'a'
      chef.add_recipe 'b'
      chef.add_recipe 'd'
      #chef.log_level = :debug
    end
  end
  
end
