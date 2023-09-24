A arquitetura do Kubernetes é um sistema complexo e altamente escalável que permite a orquestração de contêineres em ambientes de produção. Ele consiste em vários componentes que trabalham juntos para gerenciar e automatizar a implantação, o escalonamento e a manutenção de aplicativos em contêineres. Existem dois tipos principais de clusters Kubernetes: gerenciados e não gerenciados.

# Arquitetura do Kubernetes

## Master Node (Nó Mestre)

**kube-apiserver:** É o componente central do plano de controle que expõe a API do Kubernetes e atende a todas as solicitações.

**etcd:** É um armazenamento de chave-valor consistente usado para manter o estado do cluster, incluindo configurações e metadados.

**kube-scheduler:** É responsável por agendar pods em nós disponíveis com base em requisitos de recursos e políticas.

**kube-controller-manager:** Inclui vários controladores que regulam o estado do sistema, como replicação, endpoints e nós.

**Cloud Controller Manager:** Fornece integração com a infraestrutura da nuvem (apenas em clusters gerenciados).
Node (Nó):

**Kubelet:** É o agente que roda em cada nó do cluster e garante que os contêineres estejam em execução nos pods.

**Container Runtime:** É o software que executa os contêineres, como Docker ou containerd.

**Kube Proxy:** Mantém as regras de rede no nó, permitindo a comunicação de rede entre os pods.

## Add-ons (Complementos)

Existem vários complementos opcionais, como DNS, dashboard, e monitoramento, que podem ser adicionados ao cluster para funcionalidades adicionais.

## Clusters Kubernetes Gerenciados

Os clusters Kubernetes gerenciados são oferecidos por provedores de nuvem, como Google Kubernetes Engine (GKE), Amazon Elastic Kubernetes Service (EKS), Microsoft Azure Kubernetes Service (AKS) e outros. Nesses clusters, a infraestrutura e a manutenção são tratadas pelo provedor de nuvem, permitindo que os usuários se concentrem apenas em implantar e gerenciar aplicativos.

## Clusters Kubernetes Não Gerenciados

Em contraste, clusters Kubernetes não gerenciados são configurados e mantidos pelos próprios usuários ou suas equipes de operações. Isso envolve a implantação dos componentes do Kubernetes em máquinas virtuais ou servidores físicos em um ambiente de nuvem ou on-premises. Os usuários têm controle total sobre a infraestrutura e são responsáveis pela configuração, escalonamento e manutenção do cluster.

Em resumo, a arquitetura do Kubernetes inclui componentes principais em nós mestres e nós de trabalho que trabalham juntos para orquestrar aplicativos em contêineres. A escolha entre clusters gerenciados e não gerenciados depende dos requisitos específicos e da preferência do usuário, com clusters gerenciados fornecendo uma experiência mais simplificada, enquanto clusters não gerenciados oferecem maior controle e flexibilidade.
