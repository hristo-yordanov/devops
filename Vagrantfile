# -*- mode: ruby -*-
# vi: set ft=ruby :



ENV['VAGRANT_DEFAULT_PROVIDER'] = 'virtualbox'
Vagrant.configure(2) do |cnfg|
  # cnfg.vm.provision :shell, :inline => "ulimit -n 65536"
  cnfg.vm.define 'elkb' do |elkb|
#    elk.vm.box = 'fedora/27-cloud-base'
#    elk.vm.box_version = "20171105"
    elkb.vm.box = 'centos/7'
    elkb.vm.box_url = elkb.vm.box

#    mvm.vm.box_url = mvm.vm.box
#    mvm.vm.network "private_network", ip: "192.168.77.77"
    elkb.vm.network "forwarded_port", guest: 9200, host: 9200
    elkb.vm.network "forwarded_port", guest: 5601, host: 5601
    #elkb.vm.network "private_network", ip: "192.168.99.99"
    elkb.vm.provider 'virtualbox' do |prv|
#      prv.nested = true
      prv.memory = 2048
      prv.cpus = 2
#     prv.gui = true
    end
    cnfg.vm.provision "ansible" do |ansible|
        ansible.playbook = "playbook.yml"
#        ansible.extra_vars = {
#          ansible_python_interpreter: "/usr/bin/python3.6"
#        }
#        ansible.extra_vars = {
#          openshift_cluster:ENV['CLSTR'],
#          openshift_token:ENV['TKN']
#        }
    end
  end
end
