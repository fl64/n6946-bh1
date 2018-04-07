Vagrant.configure("2") do |config|
  
  config.ssh.private_key_path =  ["~/.ssh/id_rsa", "~/.vagrant.d/insecure_private_key"]
  config.ssh.insert_key = false


  config.ssh.forward_agent = true

  config.vm.box_check_update = false
  config.vm.box = "generic/centos7" 
  config.vm.define "wtf" do |wtf|
    wtf.vm.hostname = 'wtf'
    wtf.vm.network :"private_network", ip: "10.0.0.100", :name => 'vboxnet0', :adapter => 2
    wtf.vm.provision "file", source: "~/.ssh/id_rsa.pub", destination: "~/.ssh/authorized_keys"
    wtf.vm.provision "shell", inline: "grubby --update-kernel=ALL --args='vga=789'"
    wtf.vm.provider :virtualbox do |vb|
      vb.name = "wtf"
      vb.linked_clone = true
    end
  end
end