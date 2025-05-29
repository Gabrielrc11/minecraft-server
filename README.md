# Servidor Minecraft em Docker

Este repositório contém a configuração para executar um servidor Minecraft utilizando Docker e Docker Compose.

## Requisitos

- [Docker](https://docs.docker.com/get-docker/)
- [Docker Compose](https://docs.docker.com/compose/install/)
- Pelo menos 2GB de RAM disponível (configurável)

## Configuração

O servidor está configurado no arquivo `docker-compose.yml` com as seguintes especificações:

- **Versão do Minecraft**: 1.21.5
- **Memória alocada**: 2GB
- **Modo online**: Desativado (permite jogadores com contas não oficiais)
- **Dificuldade**: Difícil
- Mais configurações podem ser adicionadas...

## Instalação e Execução

### 1. Clone este repositório ou baixe os arquivos

```bash
git clone https://github.com/Gabrielrc11/minecraft-server.git
cd minecraft-server
```

### 2. Inicie o servidor

#### 2.1 Subir o container

```bash
docker-compose up -d
```

O parâmetro `-d` inicia o container em modo desanexado (background).

#### 2.2 Para verificar logs do servidor

```bash
docker-compose logs -f minecraft
```

Use Ctrl+C para sair da visualização de logs.

#### 2.3 Parando o Servidor

```bash
docker-compose down
```

## Para disponibilizar servidor na internet

Para disponibilizar seu servidor na internet e jogar com seus amigos, certifique-se do container estar em execução, adicione o port fowarding do seu roteador com o seu IP da maquina e porta do container, após isso compartilhe seu IP Público com seus amigos (Ele será o IP do seu servidor).

## Backup do Mundo

O mundo do Minecraft e todas as configurações são armazenados na pasta `data/`. 
Para fazer backup, basta copiar esta pasta para um local seguro.

## Personalização

### Alterando a Versão do Minecraft

Edite a variável `VERSION` no arquivo `docker-compose.yml`:

```yaml
VERSION: "1.21.5"  # Substitua pela versão desejada
```

### Aumentando a Memória RAM

Edite a variável `MEMORY` no arquivo `docker-compose.yml`:

```yaml
MEMORY: "2G"  # Altere conforme necessário (ex: 4G)
```

### Outras Configurações

Para configurações avançadas, consulte a [documentação oficial da imagem itzg/minecraft-server](https://github.com/itzg/docker-minecraft-server).

## Estrutura de Arquivos

- `docker-compose.yml` - Configuração do Docker Compose
- `data/` - Pasta que contém todos os dados do servidor:
  - `world/` - Dados do mundo
  - `server.properties` - Configurações do servidor
  - `ops.json` - Lista de operadores (admins)
  - `whitelist.json` - Lista de jogadores permitidos (se ativada)

## Comandos Úteis

### Acessar o Console do Servidor

```bash
docker-compose exec minecraft rcon-cli
```

### Adicionar um Operador (Admin)

```bash
docker-compose exec minecraft rcon-cli op NomeDoJogador
```

### Adicionar um Jogador à Whitelist

```bash
docker-compose exec minecraft rcon-cli whitelist add NomeDoJogador
```

### Reiniciar o Servidor

```bash
docker-compose restart minecraft
```

## Solução de Problemas

- **Servidor não inicia**: Verifique os logs com `docker-compose logs minecraft`
- **Problemas de conexão**: Certifique-se de que a porta 25565 está aberta no seu firewall
- **Erros de memória**: Aumente a memória alocada no `docker-compose.yml`

## Licença

Este projeto utiliza a imagem Docker [itzg/minecraft-server](https://github.com/itzg/docker-minecraft-server).
Ao usar este servidor, você concorda com o [EULA da Mojang](https://account.mojang.com/documents/minecraft_eula).
