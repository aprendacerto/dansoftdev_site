# Boompe LMS
Este é o repositório principal do Boompe, o qual serve como ponto de partida para o projeto.
Aqui estão localizadas as principais funcionalidades desenvolvidas até o momento. 
Com o objetivo de adicionar novos recursos ao longo do tempo, foram criados micro-serviços em repositórios separados. 
Assim, a solução do Boompe é composta por vários projetos interconectados, que utilizam nossa SDK para comunicação.

## Tecnologias
---
- `PHP:` 7.3.*
- `MySQL:` 8.0.*
- `Redis:` 5.0.3
- `GrayLog:` 1.4.*
- `RabbitMQ:` 2.3.2
- `Boompe SDK:` 1.2.*
- `PHP composer:` 2.5.8
- `Genius CSS Framework:` 1.0.4
- `Bootstrap CSS version:` 3.1.1
- `Docker:` 2.x
- `docker compose:` 2.18.x

### Configurando o ambiente local
---
Execute os comandos abaixo se estiver configurando o seu ambiente de desenvolvimento pela primeira vez.

### Instalando o Git e o Gitflow
```bash
# Lubuntu 18.04
sudo apt update
sudo apt install git git-flow -y
```

### Instalando o ownCloud
```bash
# Lubuntu 18.04
echo 'deb https://download.owncloud.com/desktop/ownCloud/stable/latest/linux/Ubuntu_20.04/ /' | sudo tee -a /etc/apt/sources.list.d/owncloud.list
sudo apt update
sudo apt install owncloud-client -y
```

### Instalando os atalhos de comando carregados do ownCloud
```bash
# Lubuntu 18.04
# -----------------------------------------------------------------------------------------
# INSTRUCOES
# 1 - alterar as variaveis abaixo CAMINHO_PROJETOS e CAMINHO_INFRA_COMANDOS
# 2 - abrir o terminal do linux ou o git bash
# 3 - vi ~/.bashrc
# 4 - copiar este conteudo e adicionar no arquivo
# 5 - source ~/.bashrc
# -----------------------------------------------------------------------------------------

# Variaveis
# -----------------------------------------------------------------------------------------
export CAMINHO_PROJETOS="/exemplo /c/projetos"
export CAMINHO_INFRA_COMANDOS="exemplo /c/owncloud/desenvolvimento/infra/comandos"

# Importacao dos comandos
# -----------------------------------------------------------------------------------------
test -f "$CAMINHO_INFRA_COMANDOS/git.sh" 			&& . "$CAMINHO_INFRA_COMANDOS/git.sh"
test -f "$CAMINHO_INFRA_COMANDOS/docker.sh" 		&& . "$CAMINHO_INFRA_COMANDOS/docker.sh"
test -f "$CAMINHO_INFRA_COMANDOS/navegacao.sh" 		&& . "$CAMINHO_INFRA_COMANDOS/navegacao.sh"
test -f "$CAMINHO_INFRA_COMANDOS/utilitarios.sh" 	&& . "$CAMINHO_INFRA_COMANDOS/utilitarios.sh"

```

### Instalando o Docker e docker compose
```bash
# Lubuntu 18.04
#
# Docker
curl -fsSL https://download.docker.com/linux/ubuntu/gpg | sudo apt-key add -
sudo add-apt-repository \
   "deb [arch=amd64] https://download.docker.com/linux/ubuntu \
   $(lsb_release -cs) \
   stable"
sudo apt update
sudo apt install docker-ce docker-ce-cli containerd.io -y
sudo usermod -aG docker NOME_DO_USUARIO
# Tem que fazer logoff e login do usuario novamente
systemctl start docker
systemctl enable docker
#
# Docker-compose
sudo curl -L "https://github.com/docker/compose/releases/download/1.24.0/docker-compose-$(uname -s)-$(uname -m)" -o /usr/local/bin/docker-compose
sudo chmod +x /usr/local/bin/docker-compose
docker-compose --version
```

### Criando a rede no Docker
```bash
docker network create --subnet=172.22.0.0/16 dansoftdev_network_internal
```

### Adicionando os dominios locais
Adicione o contéudo abaixo no arquivo de host conforme o seu sistema operacional.
```bash
# Linux
/etc/hosts 
# Mac
/private/etc/hosts
# Windows
c:\Windows\System32\Drivers\etc\hosts
```

```bash
# Conteúdo
127.0.0.1   local-ai.boompeapp.com
127.0.0.1   local-billing.boompeapp.com
127.0.0.1   local-cdn1.boompeapp.com
127.0.0.1   local-chat.boompeapp.com
127.0.0.1   local-converter.boompeapp.com
127.0.0.1   local-coupon.boompeapp.com
127.0.0.1   local-dashboard.boompeapp.com
127.0.0.1   local-email.boompeapp.com
127.0.0.1   local-exam.boompeapp.com
127.0.0.1   local-fact.boompeapp.com
127.0.0.1   local-log.boompeapp.com
127.0.0.1   local-notification.boompeapp.com
127.0.0.1   local-portal.boompeapp.com
127.0.0.1   local-registration.boompeapp.com
127.0.0.1   local-reward.boompeapp.com
127.0.0.1   local-sdk.boompeapp.com
127.0.0.1   local-search.boompeapp.com
127.0.0.1   local-sso.boompeapp.com
127.0.0.1   local.boompeapp.com
127.0.0.1   local-webconference.boompeapp.com
```

### Variáveis de ambiente locais
Execute os seguintes comando na pasta do projeto
```bash
cp -a ./env/.env_bk_local ./env/.env
```

### Iniciando
```bash
# Use  o parametro -d para desacoplar o processo do terminal "docker-compose up -d"
dcu lms
```

### Acessando

[https://local.boompeapp.com](https://local.boompeapp.com/)