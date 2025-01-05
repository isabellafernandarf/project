Vagrant.configure("2") do |config|
  # Define a box
  config.vm.box = "ubuntu/jammy64"

  # Redirecionamento de portas
  config.vm.network "forwarded_port", guest: 80, host: 8081

  # Configuração de rede
  config.vm.network "private_network", ip: "192.168.56.101"

  # Provisionamento
  config.vm.provision "shell", inline: <<-SHELL
    echo "Atualizando o sistema..."
    sudo apt-get update

    echo "Instalando Docker e ferramentas essenciais..."
    sudo apt-get install -y docker.io net-tools

    echo "Configurando Docker para o usuário 'vagrant'..."
    sudo usermod -aG docker vagrant

    echo "Instalando Docker Compose..."
    sudo curl -L "https://github.com/docker/compose/releases/download/v2.24.1/docker-compose-$(uname -s)-$(uname -m)" -o /usr/local/bin/docker-compose
    sudo chmod +x /usr/local/bin/docker-compose

    echo "Verificando instalação do Docker..."
    docker --version || echo "Erro: Docker não instalado corretamente"

    echo "Verificando instalação do Docker Compose..."
    docker-compose --version || echo "Erro: Docker Compose não instalado corretamente"

    echo "Inicializando o projeto..."
    cd /srv/www
    docker-compose up -d || echo "Erro ao executar docker-compose"
  SHELL

  # Configuração de sincronização
  config.vm.synced_folder "./", "/srv/www", exclude: [".vagrant/", ".git/", "node_modules/"]

  # Configuração de recursos da VM
  config.vm.provider "virtualbox" do |vb|
    vb.memory = "1024"
    vb.cpus = 2
  end
end
