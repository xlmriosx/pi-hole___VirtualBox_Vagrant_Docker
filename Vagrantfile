# Vagrantfile for setting up Pi-hole with a static IP
# https://github.com/pi-hole/docker-pi-hole.git
Vagrant.configure("2") do |config|
    # Define the base box
    config.vm.box = "alvistack/ubuntu-23.10"  # You can change the base box if desired
  
    # Assign a static IP address to the VM
    config.vm.network "private_network", ip: "10.10.10.10"  # Update IP as needed
    # Optional: Set hostname
    config.vm.hostname = "pihole-vm"

    # Set the VM name and other settings
    config.vm.provider "virtualbox" do |vb|
      vb.name = "pihole-vm"
      vb.memory = "2048"  # Allocate 1 GB of RAM
      vb.cpus = 2         # Assign 1 CPU
    end
    config.vm.provision "file", source: "./docker-compose.yml", destination: "/home/vagrant/docker-compose.yml"

    # Provision the VM with Pi-hole installation
    config.vm.provision "shell", inline: <<-SHELL
        sudo usermod -aG sudo vagrant
        sudo chmod -R g+rwx /var
        sudo apt-get update
        sudo apt-get install ca-certificates curl
        sudo install -m 0755 -d /etc/apt/keyrings
        sudo curl -fsSL https://download.docker.com/linux/ubuntu/gpg -o /etc/apt/keyrings/docker.asc
        sudo chmod a+r /etc/apt/keyrings/docker.asc

        # Add the repository to Apt sources:
        echo \
        "deb [arch=$(dpkg --print-architecture) signed-by=/etc/apt/keyrings/docker.asc] https://download.docker.com/linux/ubuntu \
        $(. /etc/os-release && echo "$VERSION_CODENAME") stable" | \
        sudo tee /etc/apt/sources.list.d/docker.list > /dev/null
        sudo apt-get update
        sudo apt-get install docker-ce docker-ce-cli containerd.io docker-buildx-plugin docker-compose-plugin -y
        sudo systemctl stop systemd-resolved
        sudo systemctl disable systemd-resolved

        sudo mv /etc/resolv.conf /etc/resolv.conf.backup
        sudo echo "nameserver 8.8.8.8  # Google DNS" > /etc/resolv.conf

        sudo systemctl restart docker
        sudo dig registry-1.docker.io

        sudo docker compose up -d
        sleep 30
        sudo docker logs pihole | grep password | head -n 1
    SHELL
  
  end
  