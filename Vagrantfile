IMAGE_NAME="bento/ubuntu-16.04"
WORKERS=4

Vagrant.configure("2") do |config|

        config.vm.provider 'virtualbox' do |v|
                v.memory = 1024
                v.cpus = 2
        end
        config.vm.define "k8s_master" do |master|
                master.vm.box = IMAGE_NAME
                master.vm.network :public_network, :bridge => 'enp0s25', :use_dhcp_assigned_default_route => true, ip: "192.168.0.30"

                master.vm.hostname = "k8s-master"
                master.vm.provision "ansible" do |ansible|
                        ansible.playbook = "master-playbook.yaml"
                        ansible.extra_vars = {
                                node_ip: "192.168.0.30",
                        }
                end
        end
        (1..WORKERS).each do |i|
                config.vm.define "node-#{i}" do |node|
                        node.vm.box = IMAGE_NAME
                        node.vm.network :public_network, :bridge => "enp0s25", :use_dhcp_assigned_default_route => true, ip: "192.168.0.#{i + 30}"
                        node.vm.hostname = "node-#{i}"
                        node.vm.provision "ansible" do |ansible|
                                ansible.playbook = "node-playbook.yaml"
                                ansible.extra_vars = {
                                    node_ip: "192.168.0.#{i + 30}",
                                }
                        end
                end
        end
end
