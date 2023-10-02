Caso você queira criar esse mesmo Secret usando o comando kubectl create secret, você pode executar o seguinte comando:

```
kubectl create secret generic giropops-secret --from-literal=username=<SEGREDO> --from-literal=password=giropops
```

Fácil, aqui estamos usando o parâmetro --from-literal para definir os dados do Secret. Outras opções são --from-file e --from-env-file, que você pode usar para definir os dados do Secret a partir de um arquivo ou de variáveis de ambiente.

Se você comparar as strings dos campos username e password do Secret criado usando o comando kubectl create secret com as strings dos campos username e password do Secret criado usando o arquivo YAML, você perceberá que são iguais. Isso acontece porque o comando kubectl create secret codifica os dados em Base64 automaticamente.
