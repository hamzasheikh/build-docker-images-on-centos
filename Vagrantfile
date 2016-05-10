required_plugins = %w( vagrant-vbguest vagrant-vlan )
required_plugins.each do |plugin|
  system "vagrant plugin install #{plugin}" unless Vagrant.has_plugin? plugin
end

Vagrant.configure('2') do |config|

  config.vm.provider 'virtualbox' do |v|
    v.memory = 4096
    v.cpus = 4
  end

  config.vm.define 'centos-docker' do |centos_docker|
      centos_docker.vm.box = 'centos/7'
      centos_docker.vm.network 'private_network', ip: '192.168.240.2'

      centos_docker.vm.provision "ansible" do |ansible|
        ansible.verbose = "v"
        ansible.playbook = "./ansible/playbook.yaml"
      end
  end
end
