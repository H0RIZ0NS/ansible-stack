Vagrant.configure(2) do |config|
  config.vm.box = 'ubuntu/bionic64'

  config.vm.provider 'virtualbox' do |vb|
    vb.cpus = 1
    vb.memory = 1024
  end

  config.vm.network :forwarded_port, host: 2222, guest: 22, id: 'ssh'

  config.vm.synced_folder '.', '/vagrant', disabled: true

  config.vm.provision 'shell', inline: <<~SHELL
    apt-get update
    apt-get install -y \
      python \
      python-apt
    adduser vagrant sudo
    deluser --remove-home ubuntu || true
  SHELL
end
