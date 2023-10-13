# Use a imagem base do Ubuntu 20.04
FROM ubuntu:20.04

# Atualize os repositórios e instale o Nginx
RUN apt-get update && apt-get install -y nginx

# Remova arquivos temporários e limpe o cache do APT
RUN apt-get clean && rm -rf /var/lib/apt/lists/*

# Exponha a porta 80 para que o Nginx possa receber solicitações
EXPOSE 80

# Inicialize o servidor Nginx em primeiro plano
CMD ["nginx", "-g", "daemon off;"]
