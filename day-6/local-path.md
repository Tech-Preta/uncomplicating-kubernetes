
Nesta configuração, o diretório /opt/local-path-provisioner será usado em todos os nós como o caminho para provisionamento (também conhecido como armazenamento de dados de volume persistente). O provisionador será instalado no namespace local-path-storage por padrão.

```
kubectl apply -f https://raw.githubusercontent.com/rancher/local-path-provisioner/v0.0.24/deploy/local-path-storage.yaml
```

Verifique se a instalação foi bem-sucedida:

```
kubectl -n local-path-storage get pod
```
