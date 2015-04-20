# -*- mode: ruby -*-
# vi: set ft=ruby :

Vagrant.configure(2) do |config|
  config.vm.box = "ubuntu/trusty64"

  config.ssh.forward_agent = true

  # config.vm.network :forwarded_port, guest: 80, host: 8080
  # config.vm.network :forwarded_port, guest: 3000, host: 4000

  config.vm.synced_folder ".", "/vagrant"

  config.vm.provider :virtualbox do |v|
    cpu_count = 2
    if RUBY_PLATFORM =~ /darwin/
      cpu_count = `sysctl -n hw.ncpu`.to_i
    elsif RUBY_PLATFORM =~ /linux/
      cpu_count = `nproc`.to_i
    end

    v.cpus = cpu_count
    v.memory = 2048
  end

  # config.vm.provision :puppet do |puppet|
  # end

  # Each team member can install his own development environment on a vagrant
  # box used in the co-development.
  config.vm.provision :shell, path: "~/.vagrant-shell", privileged: false
end
