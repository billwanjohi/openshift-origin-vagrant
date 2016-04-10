# -*- mode: ruby -*-
# vi: set ft=ruby :

Vagrant.configure(2) do |config|
  config.vm.box = 'puppetlabs/centos-7.2-64-nocm'
  config.vm.hostname = 'centos-openshift'
  config.vm.network 'forwarded_port', guest: 8443, host: 8443
  config.vm.network 'forwarded_port', guest: 8080, host: 8080
  config.vm.network 'private_network', type: 'dhcp'

  # https://www.vagrantup.com/docs/provisioning/ansible_local.html
  config.vm.provision 'ansible_local' do |ansible|
    ansible.playbook = 'playbook.yml'
    ansible.verbose = true
  end

  # TODO: move this to ansible
  # https://www.vagrantup.com/docs/provisioning/docker.html
  config.vm.provision 'docker' do |d|
    # https://docs.openshift.org/latest/getting_started/administrators.html#running-in-a-docker-container
    d.run 'openshift/origin',
      cmd: "start",
      args: "--privileged --pid=host --net=host \
        -v /:/rootfs:ro \
        -v /var/run:/var/run:rw \
        -v /sys:/sys \
        -v /var/lib/docker:/var/lib/docker:rw \
        -v /var/lib/origin/openshift.local.volumes:/var/lib/origin/openshift.local.volumes \
        -v /var/log:/var/log"
  end
end
