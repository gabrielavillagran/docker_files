# Sao as instrucoes do que nossa aplicacao precisa para rodar sozinha 
# Essa é nossa imagem, antes pegavamos alguma imagem da internet
# Dockerfile é a receita do bolo com o passo a passo, modo de preparo, ingredientes necessários

# Use as imagem oficial do ubuntu como a imagem base
FROM ubuntu:latest

# atualize os pacotes e instale o software
RUN apt-get update && apt-get install -y && rm -rf /var/lib/apt/lists/*

# defina um diretorio de trabalho padrao
WORKDIR /app

# comando padrao a ser executado quando o container for  iniciado, apenas 1 cmd por docker file
ENTRYPOINT [ "bash" ] 

