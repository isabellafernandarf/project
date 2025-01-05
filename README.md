# Project

Trabalho final - Roitier

## Estrutura do Projeto

Este projeto contém vários componentes, incluindo servidores web, DHCP e DNS, configurados usando Docker e Docker Compose.

### Arquivos e Diretórios

- `website/index.html`: Página web simples usando Bootstrap.
- `Dockerfile.dhcp`: Dockerfile para configurar um servidor DHCP.
- `Dockerfile.client`: Dockerfile para configurar um cliente web usando Nginx.
- `Dockerfile.apache`: Dockerfile para configurar um servidor web Apache.
- `docker-compose.yml`: Arquivo de configuração do Docker Compose para orquestrar os containers.
- `configs/named.conf.options`: Configuração do servidor DNS.
- `configs/httpd.conf`: Configuração do servidor Apache.
- `configs/dhcp.conf`: Configuração do servidor DHCP.
- `bootstrap.sh`: Script de inicialização para configurar o ambiente.
- `README.md`: Este arquivo de documentação.

## Descrição dos Arquivos

### `website/index.html`

Página HTML simples que utiliza Bootstrap para estilização.

### `Dockerfile.dhcp`

Dockerfile para configurar um servidor DHCP usando a imagem base do Ubuntu.

### `Dockerfile.client`

Dockerfile para configurar um cliente web usando Nginx.

### `Dockerfile.apache`

Dockerfile para configurar um servidor web Apache.

### `docker-compose.yml`

Arquivo de configuração do Docker Compose para orquestrar os containers de web, DHCP, DNS e cliente.

### `configs/named.conf.options`

Configuração do servidor DNS, incluindo encaminhadores e permissões de consulta.

### `configs/httpd.conf`

Configuração do servidor Apache, incluindo módulos carregados, diretórios e políticas de segurança.

### `configs/dhcp.conf`

Configuração do servidor DHCP, incluindo sub-rede, intervalo de IPs e opções de rede.

### `bootstrap.sh`

Script de inicialização para configurar o ambiente, incluindo a instalação de pacotes necessários e configuração do Docker e Docker Compose.

## Como Usar

1. Clone o repositório:
    ```bash
    git clone https://github.com/usuario/projeto.git
    cd projeto
    ```

2. Execute o script de inicialização:
    ```bash
    ./bootstrap.sh
    ```

3. Inicie os containers usando Docker Compose:
    ```bash
    docker-compose up -d
    ```

4. Acesse o servidor web no navegador:
    - Apache: `http://localhost:8080`
    - Nginx: `http://localhost:8081`
