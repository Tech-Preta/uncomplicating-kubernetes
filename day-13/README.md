# Instalação do Cosign e Assinatura de Imagens Docker

Este guia fornece instruções passo a passo sobre como instalar o Cosign e usar essa ferramenta para assinar imagens Docker, garantindo maior segurança e autenticidade.

## Pré-requisitos

- Sistema operacional Linux ou macOS
- Docker instalado e configurado
- Autenticação com docker login
- Imagem publicada no Docker Hub

## Passo 1: Instalando o Cosign

Baixe a versão mais recente do Cosign pré-compilado para seu sistema operacional:

```shell
curl -s -o cosign https://github.com/sigstore/cosign/releases/latest/download/cosign-`uname | tr '[:upper:]' '[:lower:]'` && chmod +x cosign
sudo mv cosign /usr/local/bin/cosign
```

Verifique se o Cosign está instalado corretamente executando:

```shell
cosign version
```

## Passo 2: Gerando sua chave para assinaturas

```shell
cosign generate-key-pair
```

Lembre-se de escolher uma boa senha.

## Passo 3: Assinando nossa imagem

```shell
cosign sign --key cosign.key nataliagranato/nginx:ubuntu
```

Para verificar a assinatura da imagem Docker, use:

```shell
cosign verify --key cosign.pub nataliagranato/nginx:ubuntu
```
