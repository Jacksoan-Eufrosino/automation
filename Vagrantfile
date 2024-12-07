machines = {
  "ubuntu" => {
    "memory" => "512",
    "cpu" => "1",
    "ip" => "10",
    #"image" => "centos/stream9"
    "image" => "ubuntu/trusty64"
  }
}

Vagrant.configure("2") do |config|

  machines.each do |name, conf|
    config.vm.define "#{name}" do |machine|
      machine.vm.box = "#{conf["image"]}"
      machine.vm.hostname = "#{name}.jacksoan.example"
      machine.vm.network "private_network", ip: "192.168.56.#{conf["ip"]}"
      machine.vm.provider "virtualbox" do |vb|
        vb.name = "#{name}"
        vb.memory = "#{conf["memory"]}"
        vb.cpus = "#{conf["cpu"]}"
      end
    config.vm.provision "ansible" do |ansible|
      ansible.playbook = "playbook.yml"
    end
  end
end
end
