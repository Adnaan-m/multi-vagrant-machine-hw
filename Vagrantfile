# Install required plugins
required_plugins = ["vagrant-hostsupdater"]
required_plugins.each do |plugin|
    exec "vagrant plugin install #{plugin}" unless Vagrant.has_plugin? plugin
end

Vagrant.configure("2") do |config|

    config.vm.define "app1" do |app1|
    app1.vm.box = "ubuntu/xenial64"
    app1.vm.network "private_network", ip: "192.168.10.100"
    app1.vm.synced_folder ".", "/home/ubuntu/app"
    app1.vm.provision "shell", path: "environment/app/provision.sh", privileged: false
end

    config.vm.define "db1" do |db1|
    db1.vm.box = "ubuntu/xenial64"
    db1.vm.network "private_network", ip: "192.168.10.150"
    db1.vm.provision "shell", path: "environment/db/provision.sh", privileged: false
end
end
