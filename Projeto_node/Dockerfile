FROM node

WORKDIR /src
# pega os arquivos que tem o nome package, sejam json e estejam nessa pasta (.)
COPY package*.json .

RUN npm install

# copia todos os arquivos dessa pasta
COPY . .

# servico usa a porta 3000 cliente:servico
EXPOSE 3000

ENTRYPOINT ["node", "app.js"]