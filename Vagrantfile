Vagrant.configure("2") do |config|
  # Atualizando para a última versão do Ubuntu
  config.vm.box = "ubuntu/jammy64"  # Para Ubuntu 22.04 LTS (mais recente no momento)

  # Redirecionamento de porta
  config.vm.network "forwarded_port", guest: 80, host: 8081  # Mapeia porta 80 da VM para 8081 no host

  # Configuração de rede
  config.vm.network "private_network", ip: "192.168.56.101"  # IP estático para evitar conflitos de DHCP

  # Script de provisionamento
  config.vm.provision "shell", inline: <<-SHELL
    # ...existing code...
    sudo apt-get update
    sudo apt-get install -y docker.io net-tools
    sudo usermod -aG docker vagrant
    sudo curl -L "https://github.com/docker/compose/releases/download/v2.24.1/docker-compose-$(uname -s)-$(uname -m)" -o /usr/local/bin/docker-compose
    sudo chmod +x /usr/local/bin/docker-compose
    # ...existing code...
  SHELL

  # Timeout para boot (ajuda em conexões lentas)
  config.vm.boot_timeout = 1200

  # Desabilita a pasta compartilhada padrão
  config.vm.synced_folder ".", "/vagrant", disabled: true

  # Sincroniza a pasta do projeto com a VM
  config.vm.synced_folder "./", "/srv/www", exclude: [".vagrant/", ".git/", "node_modules/"]  # Exclui arquivos/folders desnecessários

  # Configura recursos de hardware da VM
  config.vm.provider "virtualbox" do |vb|
    vb.memory = "1024"   # Memória RAM (ajuste conforme necessidade)
    vb.cpus = 2          # Número de CPUs
  end
end
