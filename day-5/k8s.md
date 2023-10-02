# Desativando o uso do swap no sistema

Primeiro, vamos desativar a utilização de swap no sistema. Isso é necessário porque o Kubernetes não trabalha bem com swap ativado:

```
sudo swapoff -a
```

# Liberando as portas necessárias

```
sudo apt install ufw -y
sudo ufw allow 6443/tcp
sudo ufw allow 10250:10255/tcp
sudo ufw allow 30000:32767/tcp
sudo ufw allow 2379:2380/tcp
sudo ufw allow 6783/tcp
sudo ufw allow 6783/udp
sudo ufw allow 6784/udp
sudo ufw allow 10248/tcp
sudo ufw enable
sudo ufw reload
```

# Carregando os módulos do kernel

Agora, vamos carregar os módulos do kernel necessários para o funcionamento do Kubernetes:

cat <<EOF | sudo tee /etc/modules-load.d/k8s.conf
overlay
br_netfilter
EOF

```
sudo modprobe overlay

sudo modprobe br_netfilter
```

# Configurando parâmetros do sistema

Em seguida, vamos configurar alguns parâmetros do sistema. Isso garantirá que nosso cluster funcione corretamente:

cat <<EOF | sudo tee /etc/sysctl.d/k8s.conf
net.bridge.bridge-nf-call-iptables  = 1
net.bridge.bridge-nf-call-ip6tables = 1
net.ipv4.ip_forward                 = 1
EOF

```
sudo sysctl --system
```

# Instalando os pacotes do Kubernetes

Hora de instalar os pacotes do Kubernetes! Coisa linda de ai meu Deus! Aqui vamos nós:

```
sudo apt-get update && sudo apt-get install -y apt-transport-https curl

curl -s https://packages.cloud.google.com/apt/doc/apt-key.gpg | sudo apt-key add -

echo "deb https://apt.kubernetes.io/ kubernetes-xenial main" | sudo tee /etc/apt/sources.list.d/kubernetes.list

sudo apt-get update
sudo apt-get install -y kubelet kubeadm kubectl

sudo apt-mark hold kubelet kubeadm kubectl
```

# Instalando o containerd

```
sudo apt-get update && sudo apt-get install -y apt-transport-https ca-certificates curl gnupg lsb-release

curl -fsSL https://download.docker.com/linux/ubuntu/gpg | sudo gpg --dearmor -o /usr/share/keyrings/docker-archive-keyring.gpg

echo "deb [arch=amd64 signed-by=/usr/share/keyrings/docker-archive-keyring.gpg] https://download.docker.com/linux/ubuntu $(lsb_release -cs) stable" | sudo tee /etc/apt/sources.list.d/docker.list > /dev/null

sudo apt-get update && sudo apt-get install -y containerd.io
```

# Configurando o containerd

Agora, vamos configurar o containerd para que ele funcione adequadamente com o nosso cluster:

```
sudo containerd config default | sudo tee /etc/containerd/config.toml

sudo sed -i 's/SystemdCgroup = false/SystemdCgroup = true/g' /etc/containerd/config.toml

sudo systemctl restart containerd

sudo systemctl status containerd
```

# Habilitando o serviço do kubelet

Por fim, vamos habilitar o serviço do kubelet para que ele inicie automaticamente com o sistema:

```
sudo systemctl enable --now kubelet
```

# Inicializando o cluster

```
sudo kubeadm init --pod-network-cidr=10.10.0.0/16 --apiserver-advertise-address=129.80.217.208 --v=5
```

# Instalando o Weave Net

```
kubectl apply -f https://github.com/weaveworks/weave/releases/download/v2.8.1/weave-daemonset-k8s.yaml
```
