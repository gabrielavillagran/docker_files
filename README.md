# 🐳 Comandos Docker Básicos

## Criação e Execução de Containers
- **Executar um container**: `docker run <nome-da-imagem>`
  - Executa um container a partir de uma imagem.
- **Executar interativamente**: `docker run -it <nome-da-imagem>`
  - Executa um container em modo interativo (terminal aberto).
- **Executar em background**: `docker run -d <nome-da-imagem>`
  - Executa um container em background.
- **Executar mapeando portas**: `docker run -d -p porta-local:porta-container <nome-da-imagem>`
  - Executa um container mapeando uma porta local para a porta do container.
- **Executar com nome específico**: `docker run --name nome_app <nome-da-imagem>`
  - Executa um container atribuindo um nome específico.
- **Baixar uma imagem**: `docker pull <nome-da-imagem>`
  - Baixa uma imagem do Docker Hub.
- **Construir uma imagem**: `docker build -t nome-da-imagem .`
  - Constrói uma imagem a partir de um Dockerfile no diretório atual.

## Gerenciamento de Containers
- **Listar containers ativos**: `docker ps`
  - Exibe todos os containers em execução.
- **Listar todos os containers**: `docker ps -a`
  - Exibe todos os containers, incluindo os inativos.
- **Parar um container**: `docker stop <id ou nome>`
  - Para a execução de um container.
- **Iniciar um container**: `docker start <id ou nome>`
  - Inicia um container parado.
- **Iniciar interativamente**: `docker start -ai <id ou nome>`
  - Inicia um container parado em modo interativo.

## Logs e Monitoramento
- **Ver logs de um container**: `docker logs <id ou nome>`
  - Exibe os logs de um container.
- **Acompanhar logs em tempo real**: `docker logs -f <id ou nome>`
  - Exibe os logs de um container e continua mostrando novos logs em tempo real.

## Limpeza
- **Remover um container**: `docker rm <id ou nome>`
  - Remove um container parado.

## Ajuda e Documentação
- **Obter ajuda de um comando**: `docker <comando> --help`
  - Exibe informações de ajuda para um comando específico.


<br>
<br>
<br>
<br>

# ✨ Dockerfile para Aplicação Node.js

Este documento descreve o `Dockerfile` para uma aplicação Node.js, explicando cada uma das instruções usadas para construir a imagem do contêiner.


# Dockerfile Explicação

Este Dockerfile configura um ambiente para uma aplicação Node.js seguindo as etapas abaixo:

1. **Base da Imagem**:
   - `FROM node`: Utiliza a imagem oficial do Node.js como base. Você pode especificar uma versão do Node.js, como `node:14` ou `node:16`, para garantir a consistência.

2. **Diretório de Trabalho**:
   - `WORKDIR /src`: Define `/src` como o diretório de trabalho dentro do contêiner. Todos os comandos seguintes serão executados neste diretório.

3. **Copia os Arquivos `package.json`**:
   - `COPY package*.json .`: Copia os arquivos `package.json` e `package-lock.json` (se existir) para o diretório de trabalho no contêiner. Isso permite usar o cache de camadas do Docker se as dependências não mudarem.

4. **Instalação de Dependências**:
   - `RUN npm install`: Executa `npm install` para instalar as dependências do projeto definidas no `package.json`, criando o diretório `node_modules`.

5. **Cópia dos Arquivos do Projeto**:
   - `COPY . .`: Copia todos os arquivos e diretórios do diretório atual no host para o diretório de trabalho dentro do contêiner, exceto o que é definido em `.gitignore`.

6. **Exposição da Porta**:
   - `EXPOSE 3000`: Informa ao Docker que o contêiner escutará na porta 3000. Lembre-se de mapear a porta ao executar o contêiner com `-p 3000:3000`.

7. **Comando de Execução**:
   - `CMD ["node", "app.js"]`: Define o comando padrão para executar a aplicação Node.js, que é iniciar `app.js` com o Node.js.

Cada etapa é essencial para garantir que a aplicação Node.js seja construída e executada corretamente dentro do contêiner Docker.


```dockerfile
FROM node

WORKDIR /src

COPY package*.json .

RUN npm install

COPY . .

EXPOSE 3000

CMD ["node", "app.js"]


# docker_files
