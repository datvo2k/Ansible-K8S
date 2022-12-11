nodes = [
  { :hostname => 'kubernetes-master',  :ip => '192.168.70.2', :ram => 4096 },
  { :hostname => 'kubernetes-node1',  :ip => '192.168.70.3', :ram => 2048 },
  { :hostname => 'kubernetes-node2',  :ip => '192.168.70.4', :ram => 2048 },
]

Vagrant.configure("2") do |config|
  nodes.each do |node|
    config.vm.define node[:hostname] do |nodeconfig|
      nodeconfig.vm.box = "bento/ubuntu-20.04";
      nodeconfig.vm.hostname = node[:hostname] + ".box"
      nodeconfig.vm.network :private_network, ip: node[:ip]
      memory = node[:ram] ? node[:ram] : 256;
      nodeconfig.vm.provider :virtualbox do |vb|
        vb.customize [
          "modifyvm", :id,
          "--memory", memory.to_s,
          "--cpus", "2"
        ]
      end
    end
  end
end