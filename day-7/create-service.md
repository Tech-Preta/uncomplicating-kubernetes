Para criar um Service precisamos utilizar o comando:

```
kubectl expose deployment MEU_DEPLOYMENT --port=80 --type=NodePort
```

## ClusterIP

Para criar um serviço ClusterIP via kubectl, você pode usar o comando kubectl expose conforme mostrado abaixo:

```
kubectl expose deployment meu-deployment --port=80 --target-port=8080
```

## NodePort

Para criar um serviço NodePort via CLI, você pode usar o comando kubectl expose com a opção --type=NodePort. Por exemplo:

```
kubectl expose deployment meu-deployment --type=NodePort --port=80 --target-port=8080
```

## LoadBalancer

Para criar um serviço LoadBalancer via CLI, você pode usar o comando kubectl expose com a opção --type=LoadBalancer.

```
kubectl expose deployment meu-deployment --type=LoadBalancer --port=80 --target-port=8080
```

## ExternalName

Para criar um exemplo de ExternalName usando o kubectl expose:

```
kubectl create service externalname meu-service --external-name meu-db.giropops.com.br
```
