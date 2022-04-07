# Kubernetes
iniciado em 10/03/2022

terminado em ANDAMENTO

[certificate]() 
[certificate]() 

Table of contents
- [Kubernetes](#kubernetes)
  - [O que é Kubernetes?](#o-que-é-kubernetes)
    - [Docker](#docker)
    - [imagem docker](#imagem-docker)
      - [alta disponibilidade](#alta-disponibilidade)
      - [escalabilidade](#escalabilidade)
      - [elasticidade](#elasticidade)
      - [Gerenciador de containers](#gerenciador-de-containers)
    - [imagem kubernetes](#imagem-kubernetes)
    - [Docker swarm](#docker-swarm)
  - [Kubernetes: Pods, Services e ConfigMaps](#kubernetes-pods-services-e-configmaps)
    - [Introduçao](#introduçao)
    - [O que é o kubernetes?](#o-que-é-o-kubernetes)
    - [definiçao: Escalabilidade Vertical](#definiçao-escalabilidade-vertical)
    - [definiçao: Escalabilidade Horizontal](#definiçao-escalabilidade-horizontal)
    - [Cluster do kubernetes](#cluster-do-kubernetes)
    - [A Arquitetura do Kubernetes](#a-arquitetura-do-kubernetes)
      - [Resources do Kubernetes](#resources-do-kubernetes)
      - [Maquinas Master](#maquinas-master)
      - [Maquinas Nodes](#maquinas-nodes)
        - [Componente api](#componente-api)
        - [Componente c-m](#componente-c-m)
        - [Componente scheduler](#componente-scheduler)
        - [componente etcd](#componente-etcd)
        - [Componente kubelet](#componente-kubelet)
        - [Componente KubeProxy](#componente-kubeproxy)
      - [Control Plane e Nodes](#control-plane-e-nodes)
    - [kubectl](#kubectl)
    - [o que aprendemos?](#o-que-aprendemos)
    - [inicializando o cluster no windows](#inicializando-o-cluster-no-windows)
      - [kubectl get nodes](#kubectl-get-nodes)
    - [inicializando o cluster no linux](#inicializando-o-cluster-no-linux)
      - [Minikube](#minikube)
        - [minikube start](#minikube-start)
        - [VirtualBox installation](#virtualbox-installation)
    - [inicializando o cluster no GCP (google cloud platform)](#inicializando-o-cluster-no-gcp-google-cloud-platform)
      - [google cloud platform console](#google-cloud-platform-console)
        - [criar um novo projeto no GCP](#criar-um-novo-projeto-no-gcp)
        - [acessar o projeto no GCP](#acessar-o-projeto-no-gcp)
        - [Kubernets engine no GCP](#kubernets-engine-no-gcp)
        - [Criar um cluster no GCP](#criar-um-cluster-no-gcp)
        - [o shell do google](#o-shell-do-google)
    - [o que aprendemos?](#o-que-aprendemos-1)
    - [entendendo o que sao pods](#entendendo-o-que-sao-pods)
      - [o que é um pod?](#o-que-é-um-pod)
      - [pods e IPs](#pods-e-ips)
    - [o que os pods sao capazes de fazer?](#o-que-os-pods-sao-capazes-de-fazer)
      - [falha de um pod](#falha-de-um-pod)
      - [pods sao efemeros](#pods-sao-efemeros)
      - [2 containers no mesmo pod](#2-containers-no-mesmo-pod)
      - [redes nos pods](#redes-nos-pods)
        - [compartilhamento do mesmo ip entre varios containers no mesmo pod](#compartilhamento-do-mesmo-ip-entre-varios-containers-no-mesmo-pod)
    - [o primeiro pod](#o-primeiro-pod)
      - [kubectl run](#kubectl-run)
        - [flag --image](#flag---image)
      - [flag --watch (kubectl get pods --watch)](#flag---watch-kubectl-get-pods---watch)
      - [kubectl describe](#kubectl-describe)
      - [mudar a versao do container no pod](#mudar-a-versao-do-container-no-pod)
      - [kubectl edit](#kubectl-edit)
    - [para saber mais: Onde as imagens sao armazenadas?](#para-saber-mais-onde-as-imagens-sao-armazenadas)
    - [criando pods de maneira declarativa](#criando-pods-de-maneira-declarativa)
      - [arquivo de configuraçao do kubernetes](#arquivo-de-configuraçao-do-kubernetes)
      - [usar o arquivo de config do kubernetes](#usar-o-arquivo-de-config-do-kubernetes)
      - [kubectl apply](#kubectl-apply)
    - [iniciando o projeto](#iniciando-o-projeto)
    - [kubectl delete pod](#kubectl-delete-pod)
    - [kubectl delete -f <arquivo.yaml>](#kubectl-delete--f-arquivoyaml)
      - [kubectl exec](#kubectl-exec)
    - [o que aprendemos?](#o-que-aprendemos-2)
    - [conhecendo services](#conhecendo-services)
      - [Services](#services)
        - [os IP´s das services sao estaticos](#os-ips-das-services-sao-estaticos)
      - [tipos de services: ClusterIP, NodePort e LoadBalancer](#tipos-de-services-clusterip-nodeport-e-loadbalancer)
    - [Criando um ClusterIP](#criando-um-clusterip)
      - [ClusterIP](#clusterip)
      - [containerPort](#containerport)
      - [Labels](#labels)
      - [Selector](#selector)
      - [ports](#ports)
      - [kubectl get service ou kubectl get svc](#kubectl-get-service-ou-kubectl-get-svc)
      - [targetPort](#targetport)
      - [kubectl get pods -o wide](#kubectl-get-pods--o-wide)
    - [Criando um Node port](#criando-um-node-port)
      - [kubectl get nodes -o wide](#kubectl-get-nodes--o-wide)
      - [NodePort](#nodeport)
      - [Linux](#linux)
    - [criando um load balancer](#criando-um-load-balancer)
    - [o que aprendemos?](#o-que-aprendemos-3)
    - [Acessando o portal](#acessando-o-portal)
      - [kubectl delete pods –all](#kubectl-delete-pods-all)
      - [kubectl delete svc – all](#kubectl-delete-svc--all)
    - [subindo o sistema](#subindo-o-sistema)
    - [subindo o banco](#subindo-o-banco)
    - [o que aprendemos?](#o-que-aprendemos-4)
    - [Utilizando variaveis de ambiente](#utilizando-variaveis-de-ambiente)
      - [Environment Variables](#environment-variables)
      - [Acessar o bash do banco de dados](#acessar-o-bash-do-banco-de-dados)
    - [criando um ConfigMap](#criando-um-configmap)
      - [ConfigMap](#configmap)
      - [kubectl get configMap](#kubectl-get-configmap)
      - [kubectl describe configmap](#kubectl-describe-configmap)
    - [aplicando o ConfigMap ao projeto](#aplicando-o-configmap-ao-projeto)
      - [valueFrom](#valuefrom)
      - [usar todas as variaveis do configMap](#usar-todas-as-variaveis-do-configmap)
      - [configMapRef e envFrom](#configmapref-e-envfrom)
    - [para saber mais: NodePort e IP´s](#para-saber-mais-nodeport-e-ips)
    - [o que aprendemos?](#o-que-aprendemos-5)
    - [Conhecendo ReplicaSets](#conhecendo-replicasets)
    - [conhecendo Deployments](#conhecendo-deployments)
      - [a grande vantagem de usar um Deployment](#a-grande-vantagem-de-usar-um-deployment)
      - [kubectl rollout history deployment <deployment_name>](#kubectl-rollout-history-deployment-deployment_name)
      - [flag --record](#flag---record)
      - [kubectl annotate deploy ou kubectl annotate deployment](#kubectl-annotate-deploy-ou-kubectl-annotate-deployment)
      - [kubectl rollout undo deployment --to-revision=2](#kubectl-rollout-undo-deployment---to-revision2)
    - [aplicando Deployments ao projeto](#aplicando-deployments-ao-projeto)
    - [o que aprendemos?](#o-que-aprendemos-6)
    - [Persistindo dados com volumes](#persistindo-dados-com-volumes)
      - [Volumes](#volumes)
        - [hostpath](#hostpath)
      - [criar um volumen no kubernetes](#criar-um-volumen-no-kubernetes)
      - [VolumeMounts](#volumemounts)
      - [2 conteiners dentro de um pod. como selecionar um - flag --container](#2-conteiners-dentro-de-um-pod-como-selecionar-um---flag---container)
    - [volumes no linux](#volumes-no-linux)
      - [criar uma pasta dentro do minikube](#criar-uma-pasta-dentro-do-minikube)
      - [minikube ssh](#minikube-ssh)
      - [DirectoryOrCreate](#directoryorcreate)
    - [Persistencia com PersistentVolumes](#persistencia-com-persistentvolumes)
      - [criando um disco](#criando-um-disco)
      - [Criar um PersistentVolume](#criar-um-persistentvolume)
      - [kubectl get pv](#kubectl-get-pv)
      - [Criar um PersistentVolumeClaim](#criar-um-persistentvolumeclaim)
      - [kubectl get pvc](#kubectl-get-pvc)
    - [Para saber mais: Mais informaçoes sobre PersistentVolumes](#para-saber-mais-mais-informaçoes-sobre-persistentvolumes)
    - [o que aprendemos?](#o-que-aprendemos-7)
    - [Utilizando Storage Classes](#utilizando-storage-classes)
    - [Conhecendo StatefulSets](#conhecendo-statefulsets)
      - [StatefulSet](#statefulset)
      - [Criar um StetefulSet](#criar-um-stetefulset)
    - [utilizando um StatefulSet](#utilizando-um-statefulset)
    - [o que aprendemos?](#o-que-aprendemos-8)
    - [conhecendo probes](#conhecendo-probes)
    - [utilizando Liveness Probes](#utilizando-liveness-probes)
    - [Utilizando Readiness Probes](#utilizando-readiness-probes)
    - [Para Saber Mais: Startup Probes](#para-saber-mais-startup-probes)
    - [o que aprendemos?](#o-que-aprendemos-9)
    - [Escalando pods automaticamente - Horizontal Pod Autoscaler](#escalando-pods-automaticamente---horizontal-pod-autoscaler)
    - [utilizando o HPA no windows](#utilizando-o-hpa-no-windows)
    - [Utilizando o HPA no linux](#utilizando-o-hpa-no-linux)
  

https://www.alura.com.br/artigos/o-que-e-kubernetes
## O que é Kubernetes?
Para entender o Kubernetes e o que ele é, vamos começar falando brevemente de Docker. 

### Docker
O Docker é a ferramenta padrão para deployar/implementar uma aplicação usando containers. 

Em outras palavras, 
```diff
+ o Docker se baseia no formato mais popular para empacotar uma aplicação e é a container engine mais usada.
```

A grande vantagem de um container é encapsular todas as dependências necessárias para rodá-lo, como bibliotecas, o runtime e o código da aplicação. 

Tudo isso em um único pacote chamado de imagem, que pode ser versionado e fácil de distribuir.

### imagem docker

O Docker revolucionou a forma como distribuir e rodar a aplicação. 

Porém, uma vez tendo um container rodando, há ainda outras questões a resolver. 

#### alta disponibilidade
Por exemplo, se um container falha na execução, como garantir que ele sobe novamente de maneira automática (alta disponibilidade)? 

#### escalabilidade
E se precisarmos de 4 containers, como automatizar e garantir que sempre teremos os 4 rodando (escalabilidade)? 

#### elasticidade
E mais, se quisermos algo elástico, como por exemplo ter no mínimo 1 container mas podendo crescer até 5 em execução, como fazer? 

Isso são só algumas questões levantadas, existem vários outras (rede, volumes, monitoramento, atualização etc) que o Docker sozinho não resolve…..

A preocupação ainda cresce se pensarmos em um arquitetura baseada em Microservices. 

Ou seja, a aplicação que estava contida em um único container, agora é dividida em vários outros que precisam interagir entre si de maneira confiável passando por vários hosts. 

E claro, garantindo alta disponibilidade e escalabilidade. 

A complexidade só cresce ...

#### Gerenciador de containers
Reparem aqui a necessidade de ter um "gerenciador de container", alguém que "fica de olho" nos containers em execução, garantindo que o sistema como um todo continua rodando como foi planejado. 

Pensando nisso, será que não existe uma ferramenta que assume essas responsabilidades? 

Será que o Google não tem algo para ajudar? 

Talvez um projeto open-source, bem popular que também funciona nos grandes provedores de nuvem?

Bom, o nome do artigo já deu um pista, mas o que estamos procurando se chama Kubernetes, criado pelo Google com grandes contribuições da Red Hat e hoje é um dos projeto open source mais populares no Github. 

```diff
+ O nome Kubernetes soa um pouco estranho, pois é uma palavra grega e significa "timoneiro" ou "piloto" (o navio de carga pilotado pelo Kubernetes).
```

### imagem kubernetes
O Kubernetes veio com grande experiência da Google e não para de crescer nas funcionalidades e usuários. 

É ele quem gerencia os containers em execução e por isso ele também é chamado de Orquestrador de Containers. 

Através dele podemos definir o estado de um sistema completo, por exemplo baseado em Microservices, seguindo boas práticas de infraestrutura como código, permitindo balanceamento de carga, alta disponibilidade, atualizações em lote e rollbacks e muito muito mais.

Hoje em dia os grandes provedores de nuvem como Azure, AWS, IBM, Red Hat ou Google dão suporte ao Kubernetes. 

Além disso, existe uma implementação local chamada de Minikube que simula um cluster Kubernetes, ideal para testes e estudos. 

O mais legal é que as configurações locais, que definem o estado da aplicação, também rodam no Kubernetes na nuvem. 

Ou seja, podemos testar o orquestrador local usando Minikube e depois publicar o sistema no AWS ou Azure, apenas com poucas alterações.

### Docker swarm
Por fim vale ressaltar que o Kubernetes não é único Orquestrador de Containers no mercado. 

Há uma solução da própria empresa Docker, chamada de Docker Swarm com o mesmo propósito, gerenciar e cuidar os container em execução. 

Qual dos dois orquestradores é melhor ou mais fácil de usar é outra discussão, mas o mercado parece adotar mais o Kubernetes do que o Docker Swarm.

## Kubernetes: Pods, Services e ConfigMaps

### Introduçao
Vamos entender, desde o início, o que é essa ferramenta, para que ela serve e como nós podemos utilizar os recursos que ela nos provê, para que nós possamos tirar o máximo de proveito dessa ferramenta.

E esse curso vai ser dividido em duas partes, onde nós vamos abordar diversos destes recursos que o Kubernetes tem para nós e nós vamos entender o que ele já consegue fazer para nos ajudar do início ao fim desse curso.

Então, nós vamos entender o que é um Pod, um ReplicaSet, um Deployment e um Volume.

E outro aviso é que, como esse curso é voltado a introduzir e apresentar o Kubernetes para vocês, nós não vamos ter ele voltado em nenhuma plataforma específica. 

Então eu vou fazer o máximo para mostrar para vocês como ele funciona no Windows, no Linux e também em alguns Clouds Providers; no caso aqui, o Google Cloud plataform.

Não vai ser com foco nas plataformas, e sim como Kubernetes funcionam; 

para nós entendermos o que essa ferramenta nos dá e como nós podemos utilizar ela em qualquer um desses ambientes.

### O que é o kubernetes?

Então, antes de nós começarmos a colocar a mão na massa com qualquer coisa do tipo com Kubernetes, nós precisamos entender o que é o Kubernetes, algumas questões arquiteturais em linhas gerais de como ele funciona e quais problemas ele resolve.

E isso é bem importante, tanto que nós vamos começar com um exemplo aqui bem clássico. 

Nós temos aqui uma máquina e nós estamos executando alguns containers.

Vamos fazer aqui a ponte com um Docker, que é o que nós temos por enquanto. 

Nós temos alguns containers em execução dentro dessa máquina, e caso nós queiramos executar mais containers dentro dessa máquina para mantermos a nossa aplicação em execução, o que pode acabar acontecendo?

Toda a máquina tem um limite de poder computacional; então caso essa máquina atinja o seu limite, pode ser que ela pare de funcionar, a aplicação responde de maneira mais lenta ou a máquina fique reiniciando incessantemente. Nós temos diversas possibilidades do que pode acontecer com essa máquina.

E para nós resolvermos esse problema temos uma solução bem simples, que é simplesmente comprarmos uma máquina mais potente, com maior poder computacional, para que ela consiga executar os nossos containers sem nenhum problema.

### definiçao: Escalabilidade Vertical
Então nós chamamos isso de adicionar mais poder computacional à uma mesma máquina; adicionando mais processamento, memória, armazenamento para resolvermos aqui o nosso problema de escalabilidade vertical. 

Então nós adquirimos uma máquina mais “parruda” para resolvermos o nosso problema.

E ainda no mesmo problema: 

como nós poderíamos resolver ele de outra forma? 

Nós temos a mesma situação, em que se nós tentarmos adicionar mais containers nessa máquina, ela vai parar de funcionar; nós estamos atingindo o limite computacional dessa máquina.

Para resolvermos isso nós podemos simplesmente adicionar mais máquinas para trabalhar aqui em paralelo com a nossa máquina original, então elas também vão ter capacidade de executar os containers sem nenhum problema e elas vão se comunicar de alguma maneira para falar o que estão fazendo com os containers que estão dentro delas.

### definiçao: Escalabilidade Horizontal
Nesse caso onde nós adicionamos mais máquinas para trabalhar em paralelo em conjunto com as outras, nós chamamos de escalabilidade horizontal. 

Então nós adicionamos mais máquinas para resolver o nosso problema.

Mas por que eu estou falando isso para vocês? Onde é que o Kubernetes entra nessa história?

O Kubernetes entra do seguinte modo: 

eu falei para vocês agora que nós resolvemos o problema na escalabilidade horizontal dividindo o poder computacional das máquinas trabalhando em paralelo.

### Cluster do kubernetes
Então o Kubernetes é capaz de fazer isso, ele gerencia uma ou múltiplas máquinas trabalhando em conjunto, que nós vamos chamar de cluster.

```diff
+ Então, uma ou mais máquinas trabalhando em conjunto, dividindo o seu poder computacional, nós vamos chamar de um cluster. 
```

O Kubernetes é capaz de criar esse cluster e o gerenciar para nós.

É aí que Kubernetes entra na história! 

Então nós conseguimos encontrar um cluster com Kubernetes; seja na AWS, seja no Google Cloud Plataform e na Azure também, aqui com Minikube no final.

Nós vamos utilizar aqui no curso, nós vamos fazer alguns exemplos diversos com o Google Cloud Plataform, nós vamos fazer alguns com Minikube e também com o próprio Docker desktop no Windows. 

Então nós vamos variar bem os cenários para vocês fixarem bem a ideia.

Mas como o Kubernetes vai trabalhar com esse cluster? 

O que ele é capaz de fazer? 

Digamos que, mais uma vez, usando a licença poética de chamar de “container” até então, porque é o que nós sabemos do Docker.

Então, digamos que nós queremos utilizar um container dentro de uma máquina do nosso cluster. 

Nós simplesmente pedimos ao Kubernetes que ponha esse container para executar dentro do nosso cluster e ele vai definir para ele aqui, usando os algoritmos que ele tem ali internamente - que, por exemplo, a nossa primeira máquina é a melhor a executar esse container.

E se eu quiser executar outro como a primeira máquina, já está sendo utilizada ali um pouco do poder computacional dela; pode ser que o Kubernetes defina que a segunda máquina vai ser responsável por executar esse container.

E caso esse container falhe, por exemplo, o Kubernetes tem total capacidade de adicionar um novo container para substituir esse que estava até então ali na nossa máquina e falhou.

E caso essas duas máquinas atinjam o seu limite de poder computacional em algum momento, o Kubernetes também é capaz de criar uma nova máquina dentro do nosso cluster para que nós consigamos também adicionar mais containers à essas máquinas - e isso é claro, uma máquina virtual. Nós não vamos materializar uma máquina física aqui na nossa casa ou no nosso ambiente de trabalho.

Então a questão é essa: 
```diff
+ o Kubernetes é capaz de criar e gerenciar um cluster para que nós consigamos manter a nossa aplicação escalável sempre que nós quisermos adicionar novos containers, sempre que nós quisermos reiniciar a nossa aplicação de maneira automática, caso ela tenha falhado. Então nós chamamos isso de orquestração de containers.
```

Então o Kubernetes é um orquestrador de containers capaz de resolver todos esses problemas que eu listei para vocês.

### A Arquitetura do Kubernetes
Antes de nós colocarmos a "mão na massa", nós vamos entender ainda uma última questão arquitetural e de recursos do Kubernetes. Como assim?

Ele vai muito além de ser um simples orquestrador de containers, ele já tem diversos recursos, como eu acabei de falar para vocês, que nos ajudam a resolver diversos tipos de problemas de maneira bem mais prática, sem nós implementarmos tudo do zero.

#### Resources do Kubernetes
Como assim? Esse resources para se dizer a terminologia correta, já têm soluções ali implementadas para determinadas tipos de caso. 

Então nós temos, por exemplo: pods, ReplicaSets, Deployments, Volumes. 

Nós vamos estudar cada um desses no decorrer do curso e quais problemas eles resolvem.

Então, por exemplo: se eu quero lidar com a questão de persistência de dados eu posso utilizar um recurso já pronto, que é o Persistent Volume. 

Então eu só vou definir como eu quero utilizar o Persistent Volume: se eu quero e devo utilizar e encapsular um container para utilizar no Kubernetes, eu utilizo um pod.

Então já dando um pequeno spoiler para vocês: um pod nada mais é do que um recurso que encapsula um container no Kubernete. Nós nunca vamos utilizar um container propriamente dito diretamente no Kubernete, nós vamos utilizar pods.

Mas nós vamos ter uma aula voltada só para isso e para o Persistent Volume. 

É só para dar uma noção para vocês.

Utilizando esses recursos nós conseguimos construir aplicações bem elaboradas; onde, por exemplo, nós recebemos um tráfego de dados no nosso session, no nosso serviço e ele consegue fazer o balanceamento de cargas entre os pods que nós temos dentro da nossa aplicação.

Esses pods podem estar sendo gerenciados por um ReplicaSet que pode estar sendo gerenciado por um deployment e pode ser escalado. 

Nós podemos aumentar o número de pods, um horizontal pod autoscaler.

Então são coisas bem legais que nós conseguimos fazer de maneira bem prática com Kubernetes, porque estes recursos já nos estão prontos.

Mas como eu falei para vocês, vamos com calma. Nós vamos ver isso no decorrer da parte 1 e da parte 2.

Só que outra coisa que é importante nós sabermos também é que o Kubernetes ,como eu falei para vocês, vai gerenciar um cluster, e as máquinas dentro de um cluster recebem denominações diferentes.

#### Maquinas Master
```diff
+ Elas podem ser master, onde o master é responsável por coordenar e gerenciar todo o nosso cluster 
```

#### Maquinas Nodes
```diff
+ e nós temos os nodes que são responsáveis pela execução do trabalho duro, para executar os nossos pods em capsulas containers, por assim dizer.
```

Mas, se nós formos sumarizar para entendermos de uma maneira mais detalhada, nós já vimos que os masters são responsáveis por gerenciar o cluster, eles vão ser responsáveis também por manter e atualizar o estado desejado.

Então se eu quero que um pod esteja em execução, o master vai ser o responsável por manter esse pod em execução; caso ele caia, ele vai ter um sinal ali responsável por fazer esse pod voltar a execução.

Ele também é responsável por receber os comandos. 

Eu quero criar algum recurso novo no meu cluster; eu vou me comunicar através do master, o qual vai ter todos os componentes necessários para lidar com isso e os nodes vão ser responsáveis por executar as nossas aplicações.

entao:

```
Master:
-> Gerenciar o cluster
-> Manter e atualizar o estado desejado
-> Receber e executar novos comandos

Node:
-> Executar as aplicaçoes
```

Mas se nós ainda formos detalhar um pouco mais, nós conseguimos que os componentes que eu falei para vocês agora possam ser destrinchados. 

##### Componente api
Então, a API, por exemplo, é responsável por receber e executar os novos comandos, ela é uma API REST.

##### Componente c-m
E nós temos o Controller Manager, que é responsável por manter e atualizar o estado desejado; 

##### Componente scheduler
nós temos os scheduler, responsável por definir onde determinado pod, vai ser executado no nosso cluster.

##### componente etcd
E nós temos ETCD, o responsável por armazenar todos os dados vitais do nosso cluster através de um banco de dados chave-valor.

E dentro do nosso Node nós encontramos dois componentes: 

##### Componente kubelet
o Kubelet, que é responsável pela execução dos poddentro dos nodes; 

##### Componente KubeProxy
e o KubeProxy, que é responsável pela comunicação entre os nossos nodes dentro do nosso cluster.

Então, a partir daí nós conseguimos saber o quê? 

#### Control Plane e Nodes
Nós conseguimos nomear essa parte de Control Plane, a composição desses quatro de cima (API, Controller Manager, Scheduler e ETCD) e esses dois componentes (Kubelet e KubeProxy) fazem parte dos Nodes, Control Plane Nodes.

Então, só para vocês terem essa noção, terem o conhecimento e saber do que se trata, caso você entrem em uma conversa sobre isso, para saber e entender como funciona por debaixo dos panos, para não passar batido - isso é bem importante.

Mas para visualizarmos ainda melhor, nós temos esses seis componentes aqui (API, Controller Manager, Scheduler e ETCD) e que nós dividimos de um lado o nosso Control Plane e nós dividimos do outro aqui os nossos nós

```diff
+ Então, nós vamos ter para cada nó que nós tivermos, um par de Kubelet e KubeProxy. A API vai ser responsável por manter a comunicação entre todos esses componentes.
```

Então a API, além de receber as ordens do mundo externo e do que nós queremos fazer com o nosso cluster, ela é responsável por manter a comunicação com Controller Manager, um ETCD, com Scheduler e também os nossos nodes.

Por isso que ela é tão importante, ela é tão importante que nós vamos falar aqui sobre ela mais um pouco. 

Nós vimos que ela é responsável por fazer essa mágica, por conseguir gerenciar os recursos do nosso cluster, nos nossos resources.

Então através dela nós conseguimos criar um pod, editar um ReplicaSet, ler os dados no Deployment, deletar um Volume - tudo isso através da API, 
```diff
- nós nunca vamos nos comunicar diretamente com os outros componentes; vai ser sempre através da API.
```

Mas, como nós nos comunicamos através da API? 

Como nós falamos com a API? 

A nossa máquina não tem poder da vidência e de saber o que é API e como se comunicar com ela, nós precisamos ter uma forma clara de se comunicar com ela através dessa API REST.

### kubectl
Para isso, nós temos uma ferramenta chamada Kubectl, que nos provê as funcionalidades de criar, ler, atualizar e remover os dados do nosso cluster, os componentes do nosso cluster, os nossos recursos.

Então, através do Kubectl nós conseguimos fazer isso de maneira declarativa ou imperativa. 

Nós podemos criar arquivos de definição, que nós vamos ver no decorrer do curso, ou executarmos comandos, que simplesmente vão fazer essa mágica acontecer.

E tudo isso ainda vai ser enviado um request do nosso Kubectl para a nossa API REST, que vai fazer a mágica acontecer dentro do nosso cluster. 

Só que a dúvida que fica agora é: 

como nós instalamos o Kubectl? 

E como nós inicializamos o nosso cluster?

Nós vamos ver que tem diferentes maneiras de nós inicializarmos aqui o nosso cluster, seja no Windows, seja no Linux, ou seja na nuvem. 

### o que aprendemos?
* para que serve o kubernetes
* como o kubernetes funciona
* quais sao os principais componentes da ferramenta
* o que é, e para que serve a API
* o que é, e para que serve o kubectl

### inicializando o cluster no windows
Para nós inicializarmos o nosso cluster no Windows é bem fácil, o próprio Docker Desktop já tem uma ferramenta embutida nele que permite a criação de um cluster kubernetes para nós.

https://www.docker.com/products/docker-desktop/

Então é só apertar em “Download” que ele vai começar a baixar sem nenhum problema. 

E na nossa área de trabalho que foi onde eu baixei, basta clicar no instalador.

Vai ser o processo de instalação padrão do Windows, ele vai pedir permissão para seguir. 

Nós concordamos e ele vai "descompactar aqui", fazer um download rapidamente, na verdade, e vai exibir duas opções: caso ele não exiba, elas são irrelevantes para o nosso curso. 

Então não precisa se preocupar, basta apertar em “Ok” sem se preocupar com mais nada.

E a partir daí ele vai começar a descompactar todos esses pacotes e depois ele vai pedir para você reiniciar a sua máquina. 

Caso ele não peça, eu recomendo que você reinicie mesmo assim para que você não tenha nenhum problema e que o Docker comece a executar corretamente.

Então eu reiniciei a minha máquina, cliquei para nós executarmos o nosso Docker Desktop, ele vai começar a executar e se for a primeira vez que você estiver executando o Docker na sua máquina, ele vai abrir essa tela de tutorial - mas ela não nos é relevante também.

```diff
+ Nós vamos vir diretamente em “Configurações > Kubernetes” e vamos habilitar o Kubernetes ("Enable Kubernetes"). 
```

E a partir daí nós temos a opção de aplicarmos e reiniciarmos para que ele crie esse cluster kubernetes para nós.

Então eu vou aplicar e ele vai reiniciar - no caso, não a nossa máquina, e sim o Docker, o serviço em si. 

Kubernetes em execução. 

Uma dica antes: caso vocês estejam utilizando o Windows, vocês podem vir em “Settings > General” e marcar essa opção para o Docker iniciar sempre que o sistema iniciar também (“Start Docker Desktop When you log in”).

Mas agora com o nosso cluster funcionando nós podemos acessar, por exemplo, o nosso PowerShell. 

A partir daí, nós já temos o Kubectl funcionando!

E nós podemos ver informações do nosso cluster. 

#### kubectl get nodes
Como por exemplo: eu quero retornar os meus nós, então 

```
kubectl get nodes 
```

e ele vai nos retornar esse nó que ele criou. 

Esse cluster com um único nó chamado docker-desktop, já está com status de pronto e com papel de master.

Então nós conseguimos agora, nós conseguimos já, na verdade, criar um cluster de maneira bem fácil no Windows, nós só precisamos instalar o Docker Desktop e habilitarmos o Kubernetes e tudo já está sendo feito. 

Caso não esteja funcionando, caso tenha dado algum erro, sempre certifique se vocês estão com o Docker Desktop rodando.

Então para o Windows é isso, bem fácil!

### inicializando o cluster no linux
Agora nós vamos fazer a instalação do Kubectl e inicializar o nosso cluster no Linux, sem nenhum mistério.

Nós vamos ter um processo um pouco diferente em relação ao como foi no Windows, pois vamos precisar manualmente instalar o Kubectl, e para isso nós poderemos e deveremos seguir a documentação de maneira bem fácil e prática, onde nós só precisamos copiar e colar os comandos no nosso terminal. 

https://kubernetes.io/docs/tasks/tools/install-kubectl-linux/


* primeiro passo
```
  curl -LO "https://dl.k8s.io/release/$(curl -L -s https://dl.k8s.io/release/stable.txt)/bin/linux/amd64/kubectl"
```

Então, copiando.

* segundo passo 

agora é para tornar o Kubectl que nós estamos baixando agora para nós darmos permissão de executável para ele no nosso sistema. 

```
curl -LO "https://dl.k8s.io/$(curl -L -s https://dl.k8s.io/release/stable.txt)/bin/linux/amd64/kubectl.sha256"
```

Então, copiando e colando. 

* terceiro passo

E por fim, nós movemos ele para o nosso path sem nenhum problema, mais uma vez nós colocamos a nossa senha e sem problemas.

```
sudo install -o root -g root -m 0755 kubectl /usr/local/bin/kubectl
```

* quarto passo

Para confirmar se tudo foi instalado sem nenhum problema, nós executamos esse comando. 

```
kubectl version --client
```

E repare que ele executou e nos retornou as informações do Kubectl.

```diff
- OBS: os comandos nao representam as açoes ditas no tutorial. os comandos foram retirados da documentaçao em 21/03/2022
```

Se nós executarmos aquele mesmo comando que nós fizemos no Windows do Kubectl get nodes, o que vai acontecer? 

Repare que ele deu um erro de conexão recusada, porque nós não temos um cluster ainda. 

Sem cluster nós não temos API, logo nós não estamos nos comunicando com ninguém.

#### Minikube
E para nós termos o nosso cluster, a nossa API em si, nós vamos utilizar uma ferramenta chamada Minikube, onde ela já cria um ambiente virtualizado com o cluster pronto para nós.

https://kubernetes.io/pt-br/docs/tutorials/hello-minikube/

E para nós instalarmos ela é bem fácil também, basta nós seguirmos o mesmo passo a passo com os comandos, copiando e colando e depois nós executamos esse comando para criarmos pastas dos binários, caso ela não exista. 

Provavelmente ela já existe no seu sistema, mas só para garantir e todo mundo seguir o mesmo passo a passo.

```diff
- OBS: os comandos a seguir sao relativos à documentaçao em 21/03/2022, nao coincindindo com os do tutorial
```

```
curl -LO https://storage.googleapis.com/minikube/releases/latest/minikube-linux-amd64
sudo install minikube-linux-amd64 /usr/local/bin/minikube
```

Nós esperamos terminar esse download e assim que ele terminar nós colamos sudo mkdir -p /usr/local/bin no terminal e colamos também o comando de instalação sudo install minikube /usr/local/bin/.

Se nós executarmos Minikube, nós veremos que apareceram diversas opções. 

##### minikube start
O mais importante é a opção do minikube start, onde ele vai criar para nós um cluster local do Kubernetes na nossa máquina virtualizada.

E para nós executarmos esse comando do minikube start, nós precisamos informar para ele mais uma coisa: qual é o drive de virtualização que nós vamos utilizar para criar esse cluster?

Para isso, nós utilizamos a flag - -vm-driver. 

##### VirtualBox installation
No caso desse curso, nós vamos utilizar o VirtualBox, onde você vai escolher a sua versão. 

Estou utilizando a versão do Ubuntu 20.04, ele vai baixar aqui o Debian para nós.

Assim que ele terminar o download na sua máquina, basta você abrir um outro terminal para ficar mais fácil, acessar a sua pasta de downloads, por exemplo: cd Downloads/, onde ele foi baixado na minha.

E nós executamos o comando 

```
sudo dpkg –i virtualbox-6.1_6.1.12-139181_Ubuntu_eoan_amd64.deb
```

e passamos para ele esse .deb, que nós queremos utilizar para instalar. 

Então, apertamos a tecla “Enter” e ele vai pedir a nossa senha e vai iniciar todo o processo de instalação. 

Nós não vamos precisar fazer mais nada.

Nós não vamos utilizar o VirtualBox fisicamente. 

Nós não vamos lidar com ele diretamente, nós só vamos utilizar essa ferramenta como o nosso driver de virtualização.

Enquanto ele vai terminando todo esse processo de instalação, nós voltamos para a inicialização, para o start do Minikube. 

E aqui nesse minikube start --vm-driver nós vamos exatamente colocar =virtualbox, onde nós estamos falando que o Minikube, que ele vai utilizar o VirtualBox como driver de virtualização para criar um ambiente virtualizado com o nosso cluster kubernetes dentro. 

```
minikube start --vm-driver=virtualbox
```

E o melhor: o Kubectl já vai conseguir fazer essa comunicação de maneira automática.

Então aqui ele já terminou todo o processo de instalação e aqui agora nós usamos a tecla “Enter” e ele vai fazer o download de todas as imagens necessárias e já vai preparar o nosso ambiente virtualizado com o nosso cluster. 

Repare que ele terminou e no final ele ainda nos mostra que o Kubectl já está até configurado para usar o Minikube.

Então se agora nós executarmos o nosso comando 

```
kubectl get nodes 
```

repare o que vai acontecer: ele nos exibe o nosso nó chamado Minikube com status de Ready e o papel aqui de master, sem nenhum problema.

Mas caso você que está acompanhando essa aula e vai fazer todo o curso no Linux, a única diferença que você vai ter em relação até então ao Windows, é que 

sempre que você iniciar a sua máquina, assim como as pessoas que estão utilizando o Windows vão precisar iniciar o Docker Desktop caso ele não esteja lá para inicializar junto com o sistema.

```diff
+ No Linux, sempre que você iniciar o seu sistema e você for fazer algo relativo ao curso, você vai precisar executar esse comando 
```
```
minikube start --vm-driver=virtualbox 
```

novamente, que ele vai reiniciar a sua máquina virtual e o seu cluster consequentemente, para que você consiga se comunicar efetivamente com o seu cluster, ele vai precisar estar iniciado.

RESUMO:
Os comandos necessários para a instalação e inicialização do cluster no Linux podem ser obtidos abaixo:

Primeiro para o kubectl:

```
sudo apt-get install curl -y

```
```
curl -LO "https://storage.googleapis.com/kubernetes-release/release/$(curl -s https://storage.googleapis.com/kubernetes-release/release/stable.txt)/bin/linux/amd64/kubectl"

```

```
chmod +x ./kubectl

```

```
sudo mv ./kubectl /usr/local/bin/kubectl

```

Agora para o minikube:

```
curl -Lo minikube https://storage.googleapis.com/minikube/releases/v1.12.1/minikube-linux-amd64 \ && chmod +x minikube

```

```
sudo install minikube /usr/local/bin/

```

### inicializando o cluster no GCP (google cloud platform)
Para nós criarmos o nosso cluster no Google Cloud Platform é bem simples, e basta nós termos uma conta no Google. 

Eu já estou logado com a minha, e em seguida nós iremos ao console.

Mas antes de mais nada, eu tenho dois avisos para vocês: 

o primeiro é que nós temos na Alura, caso você tenha interesse em gerenciar Kubernetes usando algum Cloud Provider, nós temos um curso na Alura falando sobre o EKS, sobre o Digital Ocean com Kubernetes e sobre o AKS na Azure.

Então, o foco desse curso não vai ser Google Cloud Platform, vai ser no kubernetes e como elas se comportam nessas diferentes plataformas. 

Vocês vão ver que tudo vai funcionar na exata mesma maneira no Windows, no Linux e no Google Cloud Platform. 

Então, primeiro aviso dado: esse curso não é nessa plataforma.

```diff
- O segundo que é extremamente importante, tenham isso em mente que caso vocês pretendam seguir à risca o que eu vou fazer utilizando o Google Cloud Platform, vocês podem acabar sendo cobrados porque vocês podem estar utilizando alguma coisa de um domínio pago do Google Cloud Platform. 
```

Então, caso você não tenha domínio na plataforma, você corre o risco de ser cobrado pelo que você vai fazer lá.

O propósito desse curso vai ser mostrar algumas coisas do Google Cloud Platform sem dar ênfase nessa plataforma.

#### google cloud platform console
Com os dois recados dados nós podemos seguir, então vamos ao console e a partir daí ele vai me levar para o meu console e eu vou poder criar um projeto.

##### criar um novo projeto no GCP
Então, vou criar um novo projeto. 

“Selecione um projeto > Novo projeto” no canto superior direito, chamado de “aula-gcp” e vou criar. 

É bem simples.

Ele vai criar esse projeto aqui para nós. 

##### acessar o projeto no GCP
Enquanto o projeto está sendo criado, nós podemos vir na nossa página inicial, clicar no ícone do menu lateral para escolher a opção "Página Inicial" e vocês vão notar que já tem a possibilidade de escolhermos o nosso projeto na lista que está terminando de ser criado.

##### Kubernets engine no GCP
É bem rápido. Criou, nós clicamos nele e agora com o projeto devidamente escolhido, nós podemos acessar o campo de busca e vir na parte de "Engine" do Kubernetes para criarmos um cluster utilizando esse projeto.

Então, ele vai ativar a Engine API do Kubernetes. E assim que ele criar, poderemos seguir com a criação do nosso cluster.

##### Criar um cluster no GCP
A Engine está ativa, basta nós criarmos o cluster clicando em "Create cluster" e a partir daí - claro, ele não vai criar automaticamente, ele vai pedir para nós algumas informações sobre esse cluster que nós queremos definir, como por exemplo, o nome dele, a zona.

Então nós podemos definir uma zona qualquer. 

Por exemplo: aqui na América do Sul tem em Osasco em São Paulo. 

Nós temos total liberdade para definirmos essas opções.

Então definir versão do gke que nós queremos utilizar, do Google, entre essas outras coisas, nós podemos definir um primeiro cluster para nós criarmos. 

Então ele tem a opção de vocês criar um cluster menos robusto para caso você acabe sendo cobrado, você seja cobrado menos.

Então fique atento dependendo do que você queira criar, ele desabilita algumas opções dentro também - mas como nós queremos uma coisa mais próxima da realidade, nós vamos simplesmente apertar embaixo em “CRIAR”.

A única mudança que eu fiz aqui foi definir a região para América do Sul. Eu vou apertar aqui em “CRIAR” e ele vai começar, agora sim, efetivamente a criar esse cluster aqui para nós.

Então, mais uma vez ele vai demorar um pouquinho porque o cluster todo vai ser inicializado. 

Estando pronto, o nosso cluster foi criado! Repare o símbolo de check e nós podemos nos conectar a esse cluster usando o próprio shell do Google, no navegador mesmo.

##### o shell do google
Então, ele vai carregar para nós esse shell e vai provisionar tudo para que nós possamos utilizar sem nenhum problema. 

A partir daí, assim que ele terminar essa conexão é bem rápido, ele não vai demorar muito.

Nós só executamos esse comando que já vem pronto, e nós já estamos conectados ao nosso cluster! 

Então se nós executarmos o kubectl que já nos vem configurado, nós podemos ver os nossos nós, por exemplo, aqui do nosso cluster com get nodes.

E por padrão ele criou três nós dentro do nosso cluster. 

Aqui está: 

o gke-cluster-1, cada um com o seu ID no final e todos com status de Ready já criados para nós podermos manipular.

Então nós vamos conseguir fazer exatamente as mesmas coisas no Windows e no Linux aqui também, porque o Kubernetes precisa só do Linux. 

Tendo o Linux ali, ele vai funcionar.

No Windows ele tem ali uma virtualização embutida para funcionar sem nenhum problema. 

Aqui a mesmíssima coisa, nós estamos trabalhando com Linux nas três plataformas.

Então, a partir de agora nós vamos começar a colocar a "mão na massa" e estudar também mais sobre os recursos do Kubernetes.

### o que aprendemos?
* como inicializar um cluster no windows
* como inicializar um cluster no linux
* como fazer a instalaçao manual do kubectl
* como inicializar no google cloud platform

### entendendo o que sao pods
Agora nós vamos entender o que é esse termo tão famoso quando nós ouvimos falar de Kubernetes, que são os pods. 

Nós vamos entender do que se trata, qual a diferença dele para um container, qual a vantagem da utilização de um pod, porque nós devemos utilizar ele e em qual cenário nós devemos utilizar.

Então vamos lá! 

Nós podemos começar fazendo aqui uma analogia com um Docker. 

Nós sabemos que o mundo Docker nós criamos, produzimos, gerenciamos e manipulamos o nosso container; não é verdade?

Então no mundo Docker nós trabalhamos com container. 

E a partir de agora no Kubernetes nós vamos criar, produzir, manipular e gerenciar - não mais os containers diretamente, e sim os nossos pods. 

Então o mundo kubernetes, pods, o mundo Docker e containers.

Então está aí uma diferença já de cara que nós vamos começar trabalhar agora com os pods. 

#### o que é um pod?
Mas o que é um pod? 

Vamos entender agora. 

```diff
+ Um pod, se nós traduzirmos literalmente, ele é uma capsula na verdade, e uma capsula pode conter um ou mais containers dentro dela.
```

Então nós entendemos já a diferença para um pod e entre um pod e um container. 

Nós sabemos que m pod é um conjunto de um ou mais containers, mas o que isso muda na pratica?

A partir de agora então, quando nós tivermos aqui a comunicação da nossa máquina com o kubectl para API, nós não vamos pedir pela criação diretamente de um container, e sim de um pod, que pode conter um ou mais containers dentro dele.

Isso sempre de maneira declarativa ou imperativa. 

#### pods e IPs
Dentro de um pod nós temos liberdade, como eu falei para vocês de termos mais containers, mas sempre que nós criamos um pod ele ganha um endereço IP.

```diff
+ Então o endereço IP não é mais do container, e sim do nosso pod. 
```

Dentro do nosso pod nós temos total liberdade de fazermos um mapeamento de portas para os IPs que são atribuídos a esse pod. 

Então, o que isso quer dizer? 

Vamos entender agora!

No momento em que nós fazemos a requisição aqui, por exemplo, para o IP 10.0.0.1, repare que é o mesmo IP que nós estamos fazendo requisição para o IP do pod na porta 8080. 

Nós estamos nos referindo nesse momento ao nosso container dentro da porta :8080 no nosso pod.

A mesma coisa se nós tivermos outro container na porta 9000. 

Quando nós fizermos a requisição para esta porta neste endereço, nós vamos estar nos referindo a esse container :9000.

O que isso quer dizer? 

Quer dizer que eles estão compartilhando o mesmo endereço IP e nós consequentemente não podemos ter dois containers na mesma porta dentro de um mesmo pod.

### o que os pods sao capazes de fazer?
Seguindo então, o que mais os pods são capazes de fazer? 

Nós vimos que nós temos um container ou mais dentro de um pod. 

#### falha de um pod
Caso esse container falhe, o que vai acontecer?

Nesse momento, esse pod vai parar de funcionar. 

Ele morreu para sempre e o kubernetes tem total liberdade de criar um novo pod para substituir o antigo, mas não necessariamente com o mesmo IP que ele tinha antes, nós não temos controle sobre isso.

Por quê? 

#### pods sao efemeros
Porquê os pods são efêmeros, eles estão ali para serem substituídos a qualquer momento e toda criação de um novo pod é um novo pod efetivamente, não é o mesmo pod antigo que foi renascido.

#### 2 containers no mesmo pod
E caso nós tivéssemos mais de um container dentro do mesmo pod, o que iria acontecer se esse pod falhasse? 

Para ele falhar efetivamente nós teríamos que ter a seguinte condição:

O primeiro container falhou dentro de um pod. 

```diff
+ Caso ainda tenha algum container em funcionamento sem nenhum problema dentro desse mesmo pod, ele ainda está saudável; 
```
```diff
+ mas caso nenhum container mais esteja funcionando dentro desse pod, esse pod foi finalizado e outro vai ser criado no lugar dele.
```

#### redes nos pods
Por fim, vamos entender outra questão aqui de rede do nossos pods. 

Agora, como mostrei para vocês, nós vamos fazer esse mapeamento de portas entre o IP do pod e aqui os nossos containers, porque agora todo IP pertence ao pod, e não aos containers.

```diff
+ Isso quer dizer que no fim das contas, eles vão compartilhar os mesmos namespaces de rede e de processo, de comunicação entre o processo e eles também podem compartilhar volume. 
```

Nós vamos ver isso no decorrer do curso.

Mas qual é a grande vantagem? 

Talvez você já tenha se perguntado isso na sua cabeça. 

Qual é a grande vantagem deles compartilharem o mesmo IP? 

##### compartilhamento do mesmo ip entre varios containers no mesmo pod
```diff
+ A grande vantagem é que agora eles podem fazer essa comunicação diretamente entre eles via localhost, porque eles têm o mesmo IP, não é verdade? 
```

Que é 10.0.0.1 nesse caso.

Então, agora nós temos essa capacidade de fazer uma comunicação de maneira muito mais fácil entre containers de um mesmo pod e isso, é claro, nós também vamos ter total capacidade de comunicar pods entre diferentes IPs. 

Eu tenho um pod com IP 10.0.0.1, ele pode começar com pod de IP 10.0.0.2. Por exemplo: aqui nós temos total liberdade de fazer essa comunicação.

### o primeiro pod
Agora nós vamos criar o nosso primeiro pod. 

Nós estamos utilizando o Docker Desktop aqui no Windows com o nosso cluster Kubernetes, mas caso você esteja utilizando o Linux ou Google Cloud Plataform, ou qualquer outro Cloud Provider que você queira, vai dar o mesmo resultado: nós vamos criar um pod.

E para nós criarmos eu falei para vocês que o Kubernetes, o kubectl, é capaz de fazer operações de criar, ler, atualizar e remover os recursos de dentro do nosso cluster, se comunicando com a API.

#### kubectl run
O comando kubectl run no PowerShell é capaz de criar um pod para nós. 

Os parâmetros que nós vamos informar são bem simples: 

o primeiro vai ser o nome do pod que nós queremos criar.

Então eu vou criar um pod utilizando a imagem do nginx, então eu vou chamar ele de nginx-pod e a partir daí eu posso e devo explicitar qual imagem eu quero utilizar para basear o container que será criado dentro desse pod. 

##### flag --image
Então uso a flag --image e informo com = que eu quero utilizar o nginx, por exemplo na versão latest. 

Então --image=nginx:latest.

```
kubectl run nginx-pod --image=nginx:latest
```

Se eu apertar a tecla “Enter”, olhe o que vai acontecer: ele falou que criou. 

Será que criou? 

Vamos ver aqui com o comando kubectl get pods. 

Está aqui o nosso pod chamado nginx-pod, ainda não está pronto e está com status de criação.

#### flag --watch (kubectl get pods --watch)
Se nós executarmos esse mesmo comando kubectl get pods e utilizarmos a flag --watch, ele vai passar a acompanhar esse comando em tempo real. 

```
kubectl get pods --watch
```

Então assim que tiver uma mudança no status desse comando, ele vai nos atualizar. 

Isso significa que assim que o nosso pod for criado, como ele acabou de ser, ele nos atualiza automaticamente. Olhe que legal!

Então nós podemos apertar as teclas “Ctrl + C” para sairmos desse comando e o nosso pod já está em execução, nós podemos ver outras informações também sobre ele, com o comando kubectl describe. 

#### kubectl describe

E eu quero descrever esse meu pod chamado nginx-pod. Nós apertamos a tecla “Enter” e ele vai exibir diversas informações.

```
kubectl describe pod nginx-pod
```

Inclusive, no final nós conseguimos ver como foi o processo de criação desse pod. 

Primeiro ele atribuiu este pod a um nó chamado Docker Desktop, no caso do Linux vai ser o Minikube e quem fez isso foi o “Scheduler”. 

Olhe que legal! Como é importante nós sabermos essa questão arquitetural do Kubernetes!

A partir daí ele começou a fazer o download da imagem. 

Baixou ela com sucesso, criou o container e iniciou o pod. 

Então repare: o pod só foi iniciado depois da criação do container que vai compor esse pod.

Nós podemos também ter outras informações, como por exemplo: o IP dele, esses labels e essas etiquetas que nós vamos entender do que que se tratam, pois elas são bem importantes e poderosas. 

Nós vamos entender bastante sobre elas no decorrer do curso, além de o nome dele e informações bem básicas sobre o nosso pod.

#### mudar a versao do container no pod
Se, digamos, eu estou usando a versão nginx:latest, digamos que eu queira mudar a versão do nginx que estou utilizando nesse pod. 

Eu quero atualizar esse pod já existente.

#### kubectl edit 
Eu tenho o comando kubectl edit e eu posso editar o quê? 

Um pod e qual é o pod que eu quero editar? 

Esse chamado nginx-pod, e ele vai abrir esse bloco de notas na nossa frente com diversas informações bem complexas.

```
kubectl edit pod nginx-pod
```

Mas o que importa para nós? 

Nós vamos aceitar isso por enquanto, porque nós estamos trabalhando de maneira bem ingênua. 

Nós queremos atualizar a imagem do nosso pod, que se nós analisarmos bem, está logo embaixo com o nosso image. 

Nós não queremos utilizar a versão latest, nós queremos utilizar a versão 1.0.

Nós salvamos o arquivo, fechamos e ele vai falar que o nosso pod foi editado. 

Se nós vermos aqui de novo o nosso comando kubectl get pods, olha o que vai acontecer: ele está agora com status de 0/1, de Ready, e deu erro de imagem para baixar.

```
ErrImagePull
```

O que isso quer dizer? 

Vamos descobrir o que isso quer dizer utilizando aqui o nosso comando kubectl describe pod e vamos passar aqui o nosso nginx-pod.

Se nós vermos aqui em baixo sem nenhum problema, olhe o que aconteceu - ele começou a tentar baixar essa imagem da versão 1.0 do nginx e não conseguiu. 

Por quê? 

Porque essa imagem não existe, então ele caiu meio que em um loop, no fim das contas de ficar tentando baixar essa imagem e não conseguir.

Por isso que se nós viermos aqui agora de novo, no status, nós estamos com esse ImagePullBackOff, porque ele não conseguiu fazer o download dessa imagem para a criação do nosso pod.

E foi um pouco complexo porque nós fizemos isso de maneira ingênua, nós criamos esse pod de maneira imperativa e nós tentamos editar ele também de maneira imperativa. 

Nós fizemos essa edição, na verdade, de maneira imperativa.

Só que, qual é o problema da maneira imperativa? 

Nós acabamos não tendo meio que o acompanhamento de como tudo está acontecendo dentro do nosso cluster, nós não temos nada muito bem declarado e definido.

Nós precisamos ter um histórico de quais comandos nós realizamos para saber qual é o nosso estado atual.

Para evitarmos esse tipo de problema e deixarmos tudo muito mais claro e organizado no nosso cluster, nós vamos passar a trabalhar com maneira declarativa, onde na proximo topico nós vamos criar um arquivo declarativo - um arquivo de definição para definir como é o pod que nós queremos criar.

### para saber mais: Onde as imagens sao armazenadas?
Executamos o nosso primeiro Pod. 

Porém, como o Kubernetes armazena as imagens baixadas dentro do cluster?

A resposta é simples: quando definimos que um Pod será executado, o scheduler definirá em qual Node isso acontecerá. 

O resultado então é que as imagens quando baixadas de repositórios como o Docker Hub, serão armazenadas localmente em cada Node, não sendo compartilhada por padrão entre todos os membros do cluster.

### criando pods de maneira declarativa
Agora nós vamos criar o nosso primeiro pod de maneira declarativa. 

O que isso quer dizer? 

Quer dizer que agora nós vamos precisar trabalhar com algum editor de texto. 

Eu, no caso, vou utilizar o Visual Studio Code para nós podermos fazer todo o nosso processo de criação de arquivos.

Então eu criei uma pasta e vou abrir ela, chamada “kubernetes-alura”, e dentro dela vai ser onde nós vamos fazer todo o nosso processo de criação de arquivos.

Então dentro dessa pastinha nós vamos criar os nossos arquivos de definição.

Mas como isso funciona? 

#### arquivo de configuraçao do kubernetes
É bem simples na verdade, basta nós criarmos um novo arquivo dentro dessa pasta e nomear ele. 

Então eu vou chamar ele de “primeiro-pod” e ele precisa ter uma extensão específica para que o kubectl consiga enviar ele e a API consiga interpretar. Então, ou ele pode ser um .json, ou ele pode ser um .yaml também.

O mais comum e fácil de se trabalhar é o .ayml, então vai ser ele que nós vamos utilizar daqui para o final do curso.

Então dentro desses arquivos nós precisamos começar a escrever e a informar algumas coisas, como por exemplo: 

qual é a versão da API que nós queremos utilizar.

“Como assim versão da API, Daniel?” 

Se nós viermos na documentação, nós vamos entender que na verdade a API era uma única aplicação centralizada que foi dividida em diversas partes. 

Embaixo nós temos uma delas, por exemplo: a versão alfa, a versão beta e a versão estável.

Onde a alfa tem coisas que podem ainda estar contendo bug; 

embaixo nós temos a beta que já pode ser considerada segura, mas ainda não é bom utilizar definitivamente; 

e a versão estável que é um “v” seguido de um número inteiro, onde é a versão estável efetivamente para uso.

E ela possui também diversos grupos para nós utilizarmos. Como nós queremos criar um pod, o pod está dentro da versão estável da API, logo está na versão “v” seguida de algum número - nesse caso ele está na versão “v1”.

Logo depois nós precisamos informar o que nós queremos criar. 

Nós queremos criar um pod, então o tipo do que nós queremos criar, dos recursos que nós queremos criar, é um pod.

Logo depois nós definimos quais são os metadados desse pod. 

Como, por exemplo: 

nós vamos definir qual nome nós vamos dar para ele, no caso dentro de metadados nós vamos definir essas informações.

Como nós queremos fazer isso dentro de metadata, eu vou dar usar a tecla “Tab” e vou escrever que o nome que eu quero dar para esse pod vai ser o nosso primeiro-pod-declarativo e fechar. 

Não tem mais nada para colocar no meu metadado.

E agora, quais são as especificações que eu quero dar para esse pod. 

Eu quero que ele contenha um container, um ou mais containers. 

Aqui no caso que tenho o nome de, no caso, nginx-container, que eu posso dar qualquer nome a esse container. 

É irrelevante para o nosso caso. 

Logo depois eu posso definir qual imagem eu quero utilizar para esse container.

Então nós queremos utilizar mais uma vez a versão do nginx na versão latest.

Repare que eu coloquei um tracinho. 

Por quê? 

Eu posso ter diversos desses pares para definir exatamente essa questão, eu posso ter múltiplos containers dentro de um pod. 

Então esse tracinho é para marcar o início de uma nova declaração dentro do nosso container, mas nós só queremos um container dentro desse pod. 

Então ele está feito.

E agora, como nós utilizamos esse arquivo de definição? É bem fácil! 

#### usar o arquivo de config do kubernetes
Basta nós acessarmos essa mesma pasta que eu criei, no caso “kubernetes-alura”. 

E pedir para o kubectl fazer o quê? 

Não para ele criar um pod da maneira como nós fizemos antes, mas para ele aplicar o nosso arquivo de definição chamado de primeiro-pod (config-1.yaml).

#### kubectl apply
```
kubectl apply -f .\primeiro-pod.yaml
```

E olhe que legal, ele fala que o nosso primeiro-pod agora foi criado. 

Se nós dermos o comando kubectl get pods - está ele, o nosso primeiro pod declarativo, 1/1 rodando.

E olhe que legal - agora nós só precisamos utilizar o nosso arquivo de definição e o comando foi para entregar esse arquivo para a API fazer e tomar a ação necessária!

Então nós não precisamos mais nos preocupar com qual comando nós vamos utilizar, e sim em entregar um arquivo de definição para o Kubernetes fazer o que nós queremos.

Então nós vamos ficar aplicando esses arquivos de definição, declarativos para criar os nossos recursos. Olhe que legal!

E com isso fica bem mais fácil nós manusearmos os nossos recursos. 

Por quê? 

Porque digamos que agora eu quero utilizar de novo a versão 1.0 que não existe do nginx. 

Basta eu vir no meu arquivo de definição, trocar para a versão 1.0 e aplicar esse arquivo novamente, o mesmo comando, a mesma ideia.

Ele vai nos informar que o pod não foi criado, e sim configurado; porque ele já existe e uma ação foi realizada sobre ele. 

Se nós formos olhar exatamente a mesma coisa, ele não conseguiu baixar a imagem.

Se nós continuarmos repetindo isso, em algum momento ele vai cair nesse ImagePullBackOff.

E agora nós editamos. 

Conseguimos editar ele de uma maneira bem mais prática em relação àquele arquivo gigante que nós tínhamos, que também era um .yaml, mas era bem mais complexo de se entender.

Agora nós temos um arquivo mais simples, isso significa que se eu voltar e tentar colocar uma outra versão - por exemplo, a stable do nosso nginx, que é uma versão que existe; se eu voltar e aplicar de novo o nosso arquivo de definição, olhe que legal!

Vamos executar o kubectl get pods e vamos observar o que vai acontecer. 

Ele vai continuar com esse status de erro, mas ainda ele não se configurou, ele ainda não atualizou ali efetivamente. 

E agora sim ele baixou e está utilizando a nova imagem.

Se nós apertarmos as teclas “Control + C” e descrever esse nosso pod que nós fizemos o nosso primeiro pod declarativo.

```
kubectl describe pod primeiro-pod-declarativo
```

A atribuição do scheduler como antes, a criação; o erro do ImagePullBackOff, que ele continuou tentando utilizar da versão 1.0; depois a nova tentativa de baixar a versão estável e a criação. Tudo feito sem nenhum problema, olhe que legal!

E isso tudo só com um comando, então nós centralizamos diversas dessas ações através desse único comando kubectl apply, ou seja, o kubectl foi responsável por fazer a comunicação com a API. 

Nós aplicamos um arquivo, esse -f de file - na verdade chamado primeiro-pod.yaml - e a mágica foi feita sem nenhum mistério, nós só definimos o que nós queríamos e isso foi criado dentro do nosso cluster.

Então a partir de agora, o que nós estamos conseguindo fazer? 

Nós estamos conseguindo criar, gerenciar e manipular recursos através de um único comando de uma maneira que é bem mais usada em produção e tendo um registro de como está o nosso estado atual.

Basta nós consultarmos um arquivo e vermos como nós queremos que o nosso recurso esteja, e ele vai estar conforme o arquivo de declaração de definição.

### iniciando o projeto
Agora nós vamos começar a colocar a mão na massa em um projeto mais bem elaborado, para nós conseguirmos, como eu falei, sedimentar os conceitos que nós viemos aprendendo.

Então, de início nós temos aqueles dois pods da aula passada funcionando ainda. Nós temos duas maneiras de fazer esses pods pararem de funcionar.

Esse que foi criado de maneira imperativa, nós só temos essa possibilidade de executarmos o comando Kubectl delete pod e passamos o nome do pod que nós queremos deletar.

### kubectl delete pod
```
kubectl delete pod nginx-pod
```

Então a partir desse momento que nós executarmos o comando 

```
kubectl get pods 
```

de novo, que está terminando de deletar, nós vamos ver que esse nginx-pod foi removido; 

nós não temos esse pod em execução, só o nosso primeiro-pod-declarativo, que foi criado de maneira declarativa.

A outra maneira que nós temos de eliminarmos um pod que foi criado também de maneira declarativa, que no caso é o nosso pod, é da seguinte maneira: 

### kubectl delete -f <arquivo.yaml>
nós podemos utilizar o 

```
kubectl delete –f 
```

para passar um arquivo. 

Qual é o pod que nós queremos criar? 

O pod que está utilizando o arquivo de definição baseado no .\primeiro-pod.yaml.

Então, ele vai bater esse nome: primeiro-pod-declarativo e vai remover esse pod. Nós apertamos a tecla “Enter” e ele também vai ser deletado.

Então nós temos essa maneira de removermos imperativamente, mas também nós podemos remover ele em cima do nosso arquivo de definição.

Mas vamos criar o nosso projeto! Nós vamos trabalhar em cima de um portal de notícias, só que seguindo todas as boas práticas do Kubernetes e como nós podemos utilizar os recursos ao nosso favor.

Então, como nós vamos criar de início um pod para esse portal de notícias, que é uma imagem Docker que já existe, nós vamos criar esse pod.

Vamos chamar ele de “portal-noticias.yaml”.

E dentro dele nós temos aquelas informações que nós já vimos, da versão da API. Como é um pod que está na versão V1 e o tipo que nós queremos criar, nós já sabemos que é um pod.

Os metadados daqui que nós vamos definir, nós vimos que o nome que nós vamos definir é também arbitrário. Nós podemos colocar name: portal-noticias, sem nenhum problema. Nós podemos dar o nome que nós quisermos, mas é sempre bom sermos semântico.

E as especificações desse name: portal-noticias, quais são as informações do container que vai compor esse pod para nós? Ele vai ter um nome que nós temos total liberdade para definirmos. Como, por exemplo: portal-noticias-container. Nós podemos dar o nome que nós quisermos para esse campo desse nosso container.

E a imagem que nós vamos utilizar é uma imagem que já existe e está nesse repositório da Alura – image: aluracursos/portal-noticias:1 (na versão 1). 

portal-noticias.yaml
```
apiVersion: v1
kind: Pod
metadata: 
  name: portal-noticias
spec:
  containers:
    - name: portal-noticias-container
      image: aluracursos/portal-noticias:1
```

Nós salvamos esse arquivo e partindo daí basta nós repetirmos o nosso comando e aplicarmos o nosso arquivo de definição, passando a flag -f .\portal-noticias.yaml e ele vai criar. 

```
kubectl apply -f .\portal-noticias.yaml
```

Se agora nós escrevermos o nosso kubectl get pods --watch, ele vai começar a acompanhar esse status de criação.

Criado, rodando sem nenhum problema. Como nós acessamos agora essa aplicação dentro desse pod que nós acabamos de criar? Nós podemos de início verificarmos qual é o IP dele com o comando kubectl describe pod portal-noticias. Ele vai nos exibir todo o status de que tudo está rodando sem nenhum problema. Se nós vemos o nosso IPem cima, ele é 10.1.0.9.

Então vamos copiar. Nós podemos abrir o nosso navegador. Vamos abrir ele sem nenhum problema, vamos abrir e vamos tentar executar esse IP.

O que vai acontecer? 

Pelo tempo que está demorando nós já conseguimos ter uma breve noção de que alguma coisa está errada. 

Então ele vai continuar tentando acessar e enquanto ele tenta acessar nós vamos tentar acessar ele de uma outra maneira.

Vamos volta o para o nosso terminal. 

Eu vou digitar clear e nós temos uma maneira de verificar se tudo dentro do nosso pod está funcionando da maneira que nós esperamos.

Nós conseguimos executar comandos dentro do nosso pod. Assim como no Docker, nós temos aquele comando docker exec. 

#### kubectl exec
Aqui no Kubernetes, nós temos o comando kubectl exec e também de maneira interativa.

E qual é o comando? 

Qual é o pod que nós queremos executar de maneira interativa? 

Exatamente o nosso portal-noticias. 

E qual comando nós queremos executar dentro dele? 

Nós queremos executar o comando do bash, que é o terminal ali, no caso.

Mas para nós fazermos isso, nós precisamos colocar -- e o comando que nós queremos executar. Então nós apertamos a tecla “Enter” - e nós estamos no container, nós estamos no terminal dentro do container do nosso pod.

```
kubectl exec -it <nome_do_pod> --bash

kubectl exec -it portal-noticias --bash
```

E nós conseguimos executar comandos. 

Como, por exemplo, um curl, para enviarmos uma requisição. 

```
curl localhost
```

Eu quero enviar uma requisição para o meu localhost, ou seja, para o endereço dentro do meu pod, dentro do meu container.

Se eu apertar a tecla “Enter”, repare que ele exibiu todo o conteúdo da página web que eu esperava. 

Mas se nós voltarmos no nosso navegador, ele não conseguiu acessar essa página, ele demorou muito a responder; nós não conseguimos acessar.

Mas por que nós não conseguimos acessar? 

Se nós voltarmos mais uma vez no nosso comando - vamos sair do nosso pod, do nosso container, apertando as teclas “Control + D”, vamos descrever ele mais uma vez, kubectl describe pod, e vamos exibir as informações do nosso portal de notícias.

```diff
+ Esse IP que ele está exibindo (10.1.0.9) é o IP desse pod, realmente - mas esse pod, esse IP especificamente, é para acesso só dentro do cluster. 
```

Então as outras aplicações dentro do cluster vão conseguir se comunicar com esse pod através desse IP.

E mais, nós não fizemos nenhum tipo de mapeamento para exibirmos o nosso container dentro do nosso pod porque, como nós vimos, o IP é do pod, e não do container.

Como ele sabe que a partir desse IP ele deve acessar o nosso container dentro do pod? 

Nós precisamos fazer um mapeamento para isso - e mais, nós precisamos fazer a liberação para que esse IP seja acessível no mundo externo ao cluster.


### o que aprendemos?
* o que é e para que serve um pod
* como utilizar o kubectl para criar um pod
* como criar um pod de maneira imperativa
* as desvantagens de criar recursos de maneira imperativa
* as vantagens de criar recursos de maneira declarativa
* como funcionam as diferentes versoes da API

### conhecendo services
Falei para vocês que nós conseguimos fazer a comunicação entre diferentes pods dentro do nosso cluster. 

Então, por exemplo: se nós temos esse pod de IP 10.0.0.1, nós conseguimos normalmente nos comunicar com outro pod de IP 10.0.0.2 dentro do nosso cluster.

Mas essa comunicação está sendo bem simples, entre dois pods dentro do nosso próprio cluster. 

Se nós tivéssemos um cenário um pouco mais bem elaborado, onde nós teríamos um pod responsável pelas aplicações de login com esse IP terminado em .1, um de busca com .2, um de pagamentos com .3, um de carrinho com .4 e todos esses pods se comunicariam através dos seus respectivos IPs.

Mas vamos supor que esse pod do carrinho parasse de funcionar, ou seja, ele vai precisar ser substituído. 

Então criamos um novo pod para o carrinho. 

```diff
- Só que nós não temos a garantia de que esse pod vai ter exatamente o mesmo IP do anterior.
```

Porque se nós viermos no nosso terminal, o que nós conseguiríamos fazer? 

Nós temos mais uma vez. 

Deixe-me ver esse para vocês do nosso kubectl get pods. 

Nós temos o nosso “portal-noticias” que se nós, ao invés de descrevermos ele, utilizarmos esse comando get pod –o para formatarmos o nosso output de maneira “wide”, nós teríamos que o IP dele de 10.1.0.9.

Sistema interligado de "Login" com pod 10.0.01, "Busca" com pod 10.0.0.2, "Carrinho" com pod 10.0.04 e "Pagamentos" com 10.0.0.3. Fora do sistema, está outro ícone de "Carrinho" com pod 10.0.0.5

Se nós deletarmos esse nosso pod com o comando kubectl delete –f e passarmos o nosso arquivo de definição para ele - que é o nosso .\portal-notícias.yaml - ou até mesmo, nós deletarmos com o comando kubectl delete pod portal-noticias - que é o nome do nosso pod; 

ele vai ser removido. 

Nenhum mistério até aí.

Mas se nós criarmos ele de novo... 

Vamos executar o comando kubectl apply –f e passar o nosso .\portal-noticias.yaml.

Se nós escrevermos um get pod -o wide de novo, repare, o IP veio diferente. 

Nós não temos controle sobre isso. 

Então se nós voltarmos para a nossa apresentação, nós estamos caindo exatamente nesse mesmo problema.

Como esses pods , que se comunicavam com esse pod , vão saber que eles devem se comunicar com esse pod novo? 

Como eles sabem o IP do pod novo? 

Essa é a pergunta que nós queremos responder agora.

#### Services
E para isso nós temos um recurso maravilhoso dentro do Kubernetes, chamado service, ou SVC . 

Eles são capazes de nos fazer essas coisas. 

Eles são uma abstração que expõem as aplicações executadas em um ou mais pods e nós permitirmos a comunicação entre diferentes aplicações de diferentes pods e com isso eles provêm IPs fixos.

eles sao:
* abstraçoes para expor aplicaçoes executando em um ou mais pods
* proveem IP´s fixos para comunicaçao
* proveem um DNS para um ou mais pods
* sao capazes de fazer balanceamento de carga

Então, o IP que nós vamos utilizar para comunicarmos diferentes pods não vai ser o IP do próprio pod, e sim o IP do nosso serviço. 

Os serviços sempre vão possuir um IP fixo, que nunca vai mudar. 

Além disso, um DNS que nós podemos utilizar para nos comunicar entre um ou mais pods.

E inclusive, eles são capazes também de fazer o balanceamento de carga. 

Então, como assim? 

O que isso muda na prática? 

Se nós voltarmos para aquele exemplo anterior, entre a comunicação do nosso pod de IP terminado em 1 e o terminado em 2, a questão é que nós não vamos nos comunicar com esse pod.2 diretamente.

##### os IP´s das services sao estaticos
O nosso pod vai fazer comunicação com o serviço que tem esse DNS ou esse IP que nunca vão mudar, eles são estáveis; então nós temos a garantia que por mais que o IP desse pod mude, ele vai continuar sendo o mesmo, sempre sendo comunicado por causa do nosso serviço.

Então nós precisamos entender que os serviços têm esses três tipos. 

#### tipos de services: ClusterIP, NodePort e LoadBalancer
Entre o ClusterIP, o NodePort e o LoadBalancer, cada um com uma finalidade específica.

### Criando um ClusterIP
O primeiro tipo de serviço que nós vamos abordar dentro do Kubernetes é o ClusterIP.

E qual é o propósito dele? 

Para que ele serve? 

#### ClusterIP
```diff
+ Ele serve para nada mais, nada menos, que fazer a comunicação entre diferentes pods dentro de um mesmo cluster.
```

Então, nesse cenário que nós estamos visualizando, todo e qualquer pod, esse de final .2, .4 e .3 eles vão conseguir fazer a comunicação para este pod de final .1 a partir desse serviço, utilizando o IP e o DNS, ou o DNS no caso desse serviço.

E vale ressaltar que o serviço não é uma via de mão dupla, não é porque este pod tem um serviço que ele vai conseguir se comunicar com os outros que não têm também, porque eles não têm o serviço atrelado a eles. Então unilateralmente falando, todos os outros vão se comunicar a este pod de maneira estável, mas ele só porque é um serviço não vai se comunicar aos outros se eles também não tiverem.

Tendo isso em mente, se nós tentarmos acessar esse pod a partir de fora do cluster, o que vai acontecer? 

```diff
- Utilizando esse serviço, claro, ClusterIP, nós não vamos conseguir, porque a comunicação, como eu falei, é apenas interna do cluster utilizando um ClusterIP.
``` 

Então vamos começar na prática! 

Nós vamos criar de início dois pods para fazermos o nosso experimento com o ClusterIP. 

O que nós vamos fazer imediatamente? 

Nós vamos primeiro criar um arquivo de definição para esse nosso primeiro pod, o nosso “pod-1.yaml”.

E vamos definir todo ele, a versão da API; nós vamos definir o tipo, que é um pod; no metadata nós vamos definir o nome dele, nós vamos chamar ele de pod-1 assim como o nome do arquivo. Isso não é obrigatório, só frisando.

E nas especificações nós vamos colocar as informações do container que vai compor esse pod, que vai ter um nome também não relevante para nós nesse cenário, mas é sempre bom nós definirmos semanticamente. 

Vou colocar ele como container-pod-1 e a imagem que ele vai utilizar ainda vai ser do nginx:latest.

Dito isso, nós vamos dar um pequeno parêntese. 

Caso você esteja olhando para esse arquivo como desenvolvedor, se você não soubesse, olhando na documentação do nginx no Docker Hub, que ele é executado na porta 80 por padrão, como você poderia saber que este container definido dentro desse pod está escutando na porta 80?

#### containerPort
A boa prática em questão de documentação seria nós definirmos através desse campo ports e colocarmos dentro a instrução também: containerPort, indicando que este container definido dentro deste pod está ouvindo na porta 80.

Então quando o pod for criado e tiver um IP atribuído a ele, se nós tentarmos fazer essa requisição na porta 80, nós vamos cair no nosso nginx.

pod-1.yaml
```
apiVersion: v1
kind: Pod
metadata:
  name: pod-1
spec:
  containers:
    - name: container-pod-1
      image: nginx:latest
      ports:
        - containerPort: 80
```

Tendo isso já pronto, nós podemos criar o nosso segundo pod. 

Então a mesma ideia vai ser aplicada. 

Eu vou copiar e vou criar um novo arquivo chamado “pod-2.yaml”, vou colar e vou trocar para pod-2, para manter o mesmo nome padronizado no container também.

E ele também está exposto na porta 80. 

Por quê? 

Não vai dar problema isso? 

Porque os dois são pods diferentes e cada um tem o seu respectivo IP, então não vai ter nenhum conflito em relação a isso.

pod-2.yaml
```
apiVersion: v1
kind: Pod
metadata:
  name: pod-2
spec:
  containers:
    - name: container-pod-2
      image: nginx:latest
      ports:
        - containerPort: 80
```

Vou salvar os dois arquivos e agora nós vamos criar esses dois pods, com o comando kubectl apply -f .\pod-1.yaml e logo depois também o nosso pod-2.

E agora o que nós temos, se nós voltarmos na nossa apresentação? 

Nós temos o nosso “Cluster”, o nosso portal de notícias em execução, o nosso “pod-1” e o nosso “pod-2” também.

Só que, falta o que ? 

Nós termos o nosso serviço. 

Nesse cenário que nós estamos testando o nosso cluster pela primeira vez a ideia vai ser que esse serviço pod-2 seja voltado apenas ao pod-2.

Então nós queremos criar uma maneira estável de comunicarmos com o nosso segundo pod, então vamos criar esse serviço para nós entendermos como isso funciona.

Assim como nós temos o recurso do pod dentro do Kubernetes, nós temos o recurso de service, de serviço. 

Como nós queremos criar esse recurso, nada mais válido do que nós criarmos um arquivo de definição. 

Então vamos criar o nosso “svc-pod-2.yaml”, o nome do arquivo.

E dentro dele nós vamos continuar utilizando a versão 1 da API, nada vai mudar até então. Quando mudar, eu vou destacar isso para vocês e o tipo que nós queremos criar.

É um pod? 

Não é mais um pod, é um serviço. 

E nós vamos definir no metadata dele o quê? 

Também um nome, então nós podemos chamar ele de svc-pod-2 e também uma especificação.

E dentro dessa especificação nós também não vamos definir containers, porque ele não é mais um pod. 

Nós vamos definir o tipo. 

Qual é o tipo do serviço que nós estamos criando? 

É um ClusterIP.

E agora, o que nós temos? 

Se nós salvássemos isso agora, tecnicamente, na teoria nós já temos o nosso serviço. 

Só que, o que acontece? 

Quando o nosso pod-1 ou o nosso portal de notícias quiserem se comunicar com o nosso pod-2, ele precisa encaminhar essas requisições que ele receber para o nosso pod-2.

Só que, como ele sabe que ele deve se comunicar com o pod-2? 

Como ele sabe que, isso se refere a isso ?

Caso você esteja pensando, não é pelo nome, o nome é completamente irrelevante nesse caso. 

Nós precisamos ter uma maneira sólida e estável de fazermos essa atribuição. 

#### Labels
Esse serviço está selecionando este recurso, e para isso nós temos as labels - lembra que eu falei delas para vocês? 

Nós vamos usar elas agora!

Então nós podemos e devemos, nesse cenário, etiquetar o nosso recurso - por exemplo: o nosso pod-2 - e informarmos que este serviço seleciona apenas os recursos que possui essa label.

E como isso funciona no nosso arquivo declarativo? 

Basta nós virmos e definirmos dentro do nosso metadata as labels que nós queremos utilizar, através de uma chave. 

Nesse caso, app, que nós estamos chamando e um valor que nós definimos como segundo-pod.

```
labels:
  app: segundo-pod
```

E nós também temos a liberdade de utilizarmos quantas e quaisquer label nós quisermos, então qualquer chave com qualquer valor nós podemos definir sem nenhum problema. 

Nós podemos colocar diversas coisas.

Mas nesse caso o importante é mantermos sempre a semântica, a informação do que realmente está sendo feito .

#### Selector
E agora com a nossa label criada (app), a nossa chave com este valor segundo-pod, nós precisamos informar para este serviço que ele vai selecionar todos os recursos que tiverem esta chave app com o valor segundo pod. 

```
selector:
  app: segundo-pod
```

Então a partir desse momento ele já sabe que quando ele estiver recebendo alguma requisição, ele deve encaminhar para o nosso segundo pod, o nosso pod-2.

Só que outra pergunta: agora, como ele sabe que ele deve despachar a requisição que ele receber para a porta 80 do nosso pod? 

Porque como nós vimos, o que está sendo exposto dentro desse pod é a porta 80 (containerPort), mas não tem nada claro para esse nosso serviço que ele deve, assim que receber uma requisição, encaminhar ela para a porta 80.

#### ports
É claro então que nós precisamos definir também configurações de porta dentro - e isso é bem fácil: basta nós definirmos do nosso port, definirmos a instrução port e informarmos qual é a porta que nós queremos ouvir e qual é a porta que nós queremos despachar.

Isso significa o quê? 

Que nós já sabemos em qual porta nós estamos soltando a nossa requisição. 

Mas em que porta o nosso serviço está ouvindo? 

Porque ele vai ter um IP, mas ele vai ter também uma porta para receber essas requisições. 

Então nós precisamos, e devemos, nesse cenário também definirmos uma porta onde esse serviço vai escutar.

Mas olhe que legal: se nós definirmos a nossa porta - e nós temos a liberdade de definirmos a porta de entrada igual a porta de saída – então, o que nós estamos fazendo? 

Nós estamos falando que o nosso serviço vai receber as requisições na porta 80 e vai despachar para a porta 80 também.

 De quem? 
 
 De qualquer recurso que tiver a label app segundo pod.

```
selector:
  app: segundo-pod
ports:
  - port: 80
```

Vamos entender isso na prática. 

svc-pod-2.yaml
```
apiVersion: v1
kind: Service
metadata:
  name: svc-pod-2
spec:
  type: ClusterIP
  selector: 
    app: segundo-pod
  ports:
    - port: 80
```

Agora nós vamos criar esse recurso efetivamente, vamos atualizar primeiro o nosso pod-2, porque nós definimos essa label para ele, ou seja, agora ele foi configurado.

Se nós viermos em 

```
kubectl describe pod pod-2
```

, olhe só, em cima - ele tem as nossas labels, : 

```
labels: app-segundo-pod
```


E se nós agora criarmos o nosso serviço também com 

```
kubectl apply -f .\svc-pod-2.yaml 
```

- ele foi criado.

Assim como nós temos o comando 

```
kubectl get pods
```

#### kubectl get service ou kubectl get svc
, nós temos o comando kubectl get service ou get svc, os dois funcionam.

```
kubectl get service

kubectl get svc
```

E ele vai nos mostrar esse nosso serviço. 

Esse primeiro kubernetes já vem por padrão criado com o nosso cluster. 

Esse svc-pod-2 é do tipo ClusterIP, ele tem um IP que foi definido ali no momento da criação dele, ele não tem nenhum IP externo e a porta que ele ouve é a porta 80 e vai ser a porta também que ele vai despachar.

Então, como isso vai funcionar agora? 

Como nós nos comunicamos com o nosso pod-2? 

Vamos fazer o seguinte: eu vou digitar um 

```
kubectl get pods
```
, nós temos o nosso pod-1 e o nosso portal de notícias. 

Vamos fazer o seguinte: eu vou digitar um 

```
kubectl exec -it pod-1 -- bash
```

O que eu quero fazer agora é enviar uma requisição. 

Vou fazer um curl para nós pegarmos essa página que nós queremos adquirir. 

Para onde? 

Para que o nosso endereço IP do nosso ClusterIP, que é 10.106.130.115. 

Onde? 

Na porta 80.

```
curl 10.106.130.115:80
```

E olhe só que legal: está o nosso retorno do nginx. 

Se nós tentarmos fazer a mesmíssima coisa a partir do nosso portal de notícias, o que vai acontecer? 

Vamos lá: curl 10.106.130.115:80. 

A mesma coisa, que legal!

E agora o ponto é o seguinte: eu vou sair de dentro também do nosso pod, do nosso container, vou limpar a nossa tela e vou fazer o seguinte. 

Eu vou digitar kubectl delete –f e vou deletar o nosso pod-2.

Mas o serviço vai continuar em execução no nosso cluster IP. 

Não é à toa que se eu executar agora um kubectl get svc, ele vai continuar ouvindo na porta 80.

Se eu tentar mais uma vez executar esse curl que eu acabei de fazer para a porta 80 deste serviço, ele vai continuar ouvindo, mas ele não vai ter lugar nenhum para despachar porque não tem ninguém ouvindo na porta 80. 

Então, isso significa que se em algum momento nós criarmos qualquer outro pod. 

Por exemplo: o nosso pod-2 de novo com essa label que ele vai ser selecionado pelo serviço, independentemente do IP dele ser diferente, que nós vimos que vai ser, o comando vai continuar funcionando; porque agora o nosso serviço tem um IP estável, DNS estável para fazer essa comunicação.

Se nós tentarmos, inclusive, também fazer a comunicação via DNS, também vai funcionar. 

Então, um último comentário também para ficar bem direto e bem passado o que eu quero passar para vocês é que dentro da configuração de porta nós temos a liberdade de definirmos que a porta em que nós vamos ouvir é diferente da porta que nós queremos despachar.

Como assim? 

nós vamos continuar despachando na porta 80, mas ao invés do nosso serviço ouvir na porta 80, ele pode ouvir em qualquer outra porta. 

Então basta nós definirmos, por exemplo, a porta 9000. 

Nós temos essa liberdade.

E ao invés do nosso pod ouvir na porta 9000, nós sabemos que ele está ouvindo na porta 80. 

#### targetPort
Então como a porta que o nosso serviço ouve é diferente da porta que nós queremos ouvir no nosso pod, nós devemos definir também então um outro campo chamado TargetPort - que nesse caso é o 80. 

Qual é a porta que nós queremos despachar o nosso serviço? 

A porta 80.

```
ports:
  - port: 9000 #porta de escuta do service
    targetPod: 80 # porta do pod
```

svc-pod-2.yaml
```
apiVersion: v1
kind: Service
metadata:
  name: svc-pod-2
spec:
  type: ClusterIP
  selector: 
    app: segundo-pod
  ports:
    - port: 9000
      targetPort: 80
```

Então se nós salvarmos e executarmos, nós vamos configurar o nosso serviço novamente. 

Olhe o que que vai acontecer, vamos lá! 

Ele foi devidamente configurado. 

Se nós escrevemos 

```
kubectl get svc
```
, repare que agora ele não ouve mais na porta 80, ele ouve na porta 9000.

Mas o IP é exatamente o mesmo, a diferença é que agora quando nós fizermos alguma requisição, por exemplo, a partir do nosso portal de notícias para esse pod-2, nós não vamos mais enviar requisição para a porta 80; nós vamos enviar ela para a porta 9000 e tudo vai continuar funcionando.

Então, o que acontece? 

Quando nós temos o nosso pods - eu vou botar o - wide para nós vermos o nosso IP - 


#### kubectl get pods -o wide
```
kubectl get pods -o wide
```

o nosso pod-2 tem este IP que ouve na porta 80, que é onde está a nossa aplicação do nginx.

Nós temos o nosso pod no IP 10.1.0.67 ouvindo na porta 80, nós conseguimos nos comunicar a esta aplicação usando este endereço. 

Mas qual é o problema dela? 

O problema é que ela não é estável.

Então nós temos total liberdade para fazermos isso, só que se nós tentarmos também nos comunicar agora a partir do IP do nosso serviço, que é 10.106.130.115, o que vai acontecer? 

Nós precisamos fazer essa comunicação a partir da porta como nós definimos agora, 9000 e ele vai fazer o bound, ele vai fazer esse bind para nós, para o nosso 10.1.0.67 na porta 80.

Então nós também temos a possiblidade de variarmos essa porta, como nós fizemos e da maneira como nós quisermos, contanto que ele esteja livre para este IP e ele vá fazer esse redirecionamento para a nossa TargetPort definida do nosso container, dentro do nosso pod.

### Criando um Node port
Tendo entendido o que são ClusterIP, fica muito mais fácil nós entendermos do que que se trata um NodePort. 
```diff
+ Eles nada mais são do que um tipo de serviço que permitem a comunicação com o mundo externo.
```

Então agora nós conseguimos fazer uma requisição, enviar uma requisição de uma na que não está dentro do nosso cluster para o nosso cluster, para algum pod dentro dele.

Então significa que agora nós conseguimos acessar, por exemplo, a partir do navegador alguma aplicação que está dentro do nosso cluster, utilizando o nosso NodePort.

E ele vai além disso, 
```diff
+ ele também funciona dentro do próprio cluster como um ClusterIP. 
```

Então se você quer ter algum pod que além de ser acessado dentro do cluster, também deve ser acessado de maneira externa, você pode utilizar o NodePort, porque ele também vai funcionar como ClusterIP.

Isso significa que, por exemplo, este pod, que tem a label version 2.0, consegue ser acessado tanto por esse pod de dentro do cluster a partir desse serviço, quanto das mnas fora do nosso cluster, também a partir desse serviço.

Então agora nós vamos conseguir fazer toda a criação do nosso NodePort. 

Nós vamos deixar posteriormente tudo bem elaborado com o projeto. 

Como eu falei para vocês, nós vamos alcançar o estado onde nós conseguimos gerenciar múltiplos pods com o mesmo serviço, tudo a partir das nossas labels e com o balanceamento de carga automático. 

Mas vamos com calma, vamos primeiro criar o nosso NodePort na primeira vez.

Qual é a ideia ? 

Nós já temos o nosso cluster do jeito que ele está agora, nós temos o nosso pod-1, o nosso pod-2, o nosso portal-noticias e um serviço que faz essa requisição esse tratamento de requisição para enviar para o nosso pod-2 - tudo isso feito através das nossas labels que nós criamos.

A ideia agora vai ser bem parecida, só que nós vamos querer criar um serviço para o nosso pod-1, onde ele vai expor o nosso pod-1 para o mundo externo. 

Então, agora nós precisamos, mais uma vez, voltar ao nosso Visual Studio Code. 

Nós já temos o nosso pod-1 e o nosso pod-2, o nosso portal-noticias também e o ClusterIP criado anteriormente já rodando.

A ideia agora vai ser nós criarmos o nosso service chamado NodePort desse tipo. 

A ideia é bem parecida, vamos chamar então de name: svc-pod-1 porque esse serviço vai ser voltado para o nosso pod-1.

E nós vamos definir a versão da API também como V1. 

Nada de novo, o tipo ainda é um serviço, um service, então escrevemos Service .

Na metadata vamos dar um nome para ele, vamos seguir a mesma ideia que nós colocamos no anterior que vai ser svc-pod-2. nós vamos colocar também svc-pod-1.

Nas especificações, olhe só como é bem parecido: o tipo, ao invés de ser ClusterIP, vai ser um NodePort.

```
type: NodePort
```

E dentro nós também vamos ter aquelas configurações de porta. 

Vamos definir, qual é a porta que, como eu falei para vocês, esse serviço, o nosso NodePort também vai funcionar como ClusterIP.

Então, de maneira similar ao nosso serviço 2, nós também vamos definir um port dentro. 

Qual é a porta em que o nosso serviço vai ouvir dentro do cluster? 

Nós queremos, por exemplo, que seja na porta 8080. 

Nós temos total liberdade para isso.

Vamos colocar só port: 80. 

Lembra que eu falei para vocês que se nós definirmos só a port, implicitamente ele vai nos definir também o TargetPort sendo igual ao port? 

Então nós não precisamos explicitar o TargetPort se nós explicitarmos só o port, ele assume que os dois são iguais se nós definirmos só o primeiro.

svc-pod-1.yaml
```
apiVersion: v1
kind: Service
metadata:
  name: svc-pod-1
spec:
  type: NodePort
  ports:
    - port: 80
      #targetPort: 80
```

Então, agora nós já definimos o nosso port. 

Se nós tentarmos executar para valer, ele vai funcionar a princípio. 

Vamos ver, eu vou salvar, vou no nosso Powershell vou digitar 

```
kubectl apply -f .\svc-pod-1.yaml
```

Se nós apertarmos a tecla “Enter”, ele vai ser criado. 

Mas ainda faltam alguns pequenos detalhes. 

Como, por exemplo: nós temos o nosso serviço do tipo NodePort, eu vou separar a tela mais uma vez, vou dar um split.

E nós precisamos, assim como nós fizemos anteriormente, fazer o bind desse serviço com este pod? 

Então, vamos colocar as labels, no caso, vamos seguir a mesma ideia de, por exemplo: app e vamos chamar ele de primeiro-pod para seguirmos o mesmo padrão que nós viemos fazendo.

entao o pod-1.yaml fica assim:
```
apiVersion: v1
kind: Pod
metadata:
  name: pod-1
  labels:
    app: primeiro-pod
spec:
  containers:
    - name: container-pod-1
      image: nginx:latest
      ports:
        - containerPort: 80
```

E nós vamos adicionar fora de port alinhado, o seletor. Então: selector: e vamos chamar o nosso app: primeiro-pod.

entao o svc-pod-1.yaml fica assim:
```
apiVersion: v1
kind: Service
metadata:
  name: svc-pod-1
spec:
  type: NodePort
  ports:
    - port: 80
      #targetPort: 80
  selector:
    app: primeiro-pod
```

Então agora, como isso vai funcionar ? 

Se nós voltarmos e configurarmos os dois da maneira correta... 

Configuramos o nosso serviço e agora nós configuramos também o nosso pod. 

Devidamente configurado!

E se nós tentarmos, como eu falei para vocês, fazer o acesso a partir de dentro do cluster, nós vamos conseguir. 

Então, vamos lá!

Vamos digitar 

kubectl get svc

Está o nosso svc-pod-1, ele tem esse IP (10.104.108.232) e olhe só como ele nos mostra que ele faz o bind da porta 80 para a porta 30363. 

```
80:30363/TCP
```

O que isso quer dizer? 

Nós vamos entender, com calma.

Primeiro nós vamos fazer o mesmo teste que nós fizemos com o ClusterIP. 

Vamos acessar ele a partir do nosso portal de notícias. 

Então, 

```
kubectl exec –it -- bash
```

Se nós colocarmos, fazer um curl novamente para 10.104.108.232, que é o nosso IP na porta 80, o que vai acontecer? 

Mágica! 

Tudo continua funcionando sem nenhum problema!

Mas como nós fazemos para acessar agora esse NodePort a partir do mundo externo, a partir do nosso navegador? 

Então vou abrir uma nova aba. 

Vamos lá, o que vai acontecer ?

Se nós tentarmos acessar esse serviço... Vamos colocar o IP dele, vamos pegar 10.104.108.232 e vamos colocar ele na porta 80. 

```
10.104.108.232:80
```
O que vai acontecer pessoal? 

Ele está carregando e mais uma vez aparentemente está demorando demais e não vai conseguir.

Por quê? 

Porque olhe só a peculiaridade. 

Vou digitar get svc de novo, para nós destacarmos melhor.

Nós temos o nosso IP para esse svc-pod-1, mas repare na coluna que ele está! ClusterIP.

O que isso quer dizer? Quer dizer que esse IP é para comunicação dentro do cluster. 

Então qual é o IP que eu devo utilizar para fazer a comunicação a partir de fora do cluster? 

Eu tenho que fazer isso a partir do IP do meu nó, porque é um NodePort.

#### kubectl get nodes -o wide
Então se eu vier e fizer 

```
kubectl get nodes -o wide 
```

para ele botar o IP, olhe só - o nosso external IP no caso do Windows é none e o nosso IP interno é 192.168.65.3.

No caso do Windows, agora é um momento em que nós vamos ter uma pequena diferença entre o pessoal que está no Windows e no Linux, porque no caso do Docker Desktop no Windows ele faz um bind automaticamente do Docker Desktop para o nosso LocalHost, então o IP desse nó no Windows vai ser LocalHost.

Então se nós viermos no nosso navegador e colocarmos 

```
localhost:80
```

, nós vamos a princípio acessar, só que não é isso que nós queremos. 

Isso é o Windows que tem alguma coisa rodando na porta 80 para nós. 

O que nós queremos acessar é a página do nginx.

Mas eu botei, não botei pessoal!? 

A porta 80? 

Por que eu não estou conseguindo acessar? 

Por que isso não funciona? 

Porque, na verdade, se nós formos um pouco mais "malandros", nós vamos observar que a porta 80 é a de uso interno do cluster, mas ele faz o bind para a porta 30363 - que é aquela porta louca que nós vimos.

Então se nós copiarmos esse número, pegarmos esse 30363 e colocarmos LocalHost nessa porta – mágica! 

```
localhost:30363
```

Nós conseguimos agora a nossa aplicação através do nosso serviço de maneira externa.

```diff
- Mas tem uma peculiaridade: esse número é arbitrário, ele vai variar de 30000 até 32000 e alguma coisa, é um intervalo, é 32767. 
```

#### NodePort
Mas nós temos a liberdade para nós definirmos o NodePort que nós queremos utilizar.

Então vamos fazer o seguinte: nós podemos voltar no nosso serviço que nós acabamos de definir e definirmos também uma instrução, um outro campo chamado NodePort, onde nós podemos definir qualquer valor no intervalo de 30000 até 32767.

svc-pod-1.yaml
```
apiVersion: v1
kind: Service
metadata:
  name: svc-pod-1
spec:
  type: NodePort
  ports:
    - port: 80
      #targetPort: 80
      nodePort: 30000
  selector:
    app: primeiro-pod
```

Nesse caso vou colocar, por exemplo, o próprio 30000, vou apertar as teclas "Ctrl + S". 

No momento em que eu aplicar a minha mudança a esse serviço, olhe o que vai acontecer.

Ele foi configurado! Se nós digitarmos 

get svc de novo, olhe só, LocalHost 30000. 

Então se nós viermos e executarmos na porta 30000, repare que tudo continua funcionando.

Agora pessoal, repare que tudo, da maneira como nós esperávamos e que nós vamos fazer agora. 

#### Linux
Eu vou entrar no Linux para o pessoal que também está no Linux entender como tudo funciona sem nenhum problema.

Pessoal, agora nós estamos no Linux, com as exatas mesmas configurações, o pod-1, o pod-2, o portal-notícias, os nossos dois serviços que nós criamos. 

Nada de novo, os mesmos arquivos.

E a diferença para acessarmos é que se nós viermos no nosso navegador e executarmos localhost:30000, ele não vai conseguir acessar - porque como eu falei para vocês, 
```diff
- no Linux nós estamos utilizando o Minikube com o Virtual Box e ele não faz o bind automático para o nosso LocalHost.
```

Para nós conseguirmos acessar, nós vamos executar o comando 

```
kubectl get nodes -o wide 
```

e ele vai nos retornar, nessas informações todas, o internal IP.

E vai ser ele. no caso, o meu é 192.168.99.106; no caso de vocês provavelmente vai ser diferente. 

Então eu vou copiar esse IP e agora no meu navegador vou fazer o acesso através dele na porta 30000. 

Olhe só que legal, tudo funcionando normalmente!

Então LocalHost não vai funcionar, nós vamos usar o nosso internal IP no Linux. 

Enquanto no Windows, todo o acesso vai ser via LocalHost porque ele vai bind direto. 

A única diferença vai ser essa, o comportamento do resto todo é exatamente o mesmo.

### criando um load balancer
Entender o que é um LoadBalancer depois que nós já entendemos do que se trata um NodePort e um ClusterIP é bem fácil - principalmente porque o 

```diff
+ LoadBalancer nada mais é do que um ClusterIP que permite a comunicação entre uma uma do mundo externo e os nosso pods. 
```

```diff
+ Só que ele automaticamente se integra ao LoadBalancer do nosso cloud provider.
```

Então quando nós criamos um LoadBalancer ele vai utilizar automaticamente, sem nenhum esforço manual, o cloud provider da AWS ou do Google Cloud Platform ou da Azure, e assim por diante.

Então, vamos! Eu vou pegar o nosso pod-1 que nós viemos trabalhando e vou criar esse mesmo pod no nosso cluster do Google Cloud Platform.

Vou colocar o arquivo, vou criar ele com as mesmas definições que eu acabei de copiar ali, vou colar, vou digitar um apply, 

kubectl apply –f e passar o nosso pod-1.yaml. 

Ele foi criado sem nenhum problema, nós digitamos um 

kubectl get pods

, ele foi criado e agora nós precisamos criar o nosso LoadBalancer.

Então eu vou criar no Visual Studio Code para nós conseguirmos visualizar melhor. 

Nós vamos fazer o seguinte: vamos criar o nosso svc-pod-1-loadbalancer.yaml e dentro dele nós vamos definir mais uma vez a versão da nossa API como V1. 

O que nós queremos criar continua sendo um service e em metadata vamos chamar ele também pelo name: svc-pod-1-loadbalancer.

nas especificações nós vamos definir o tipo que vai ser o nosso type: LoadBalancer, agora sem nenhum problema. 

em ports: nós vamos definir a nossa porta de entrada, onde nós podemos ir definindo. 

Nós queremos que dentro do cluster.

Como ele é um NodePort, ele também é um ClusterIP, ele ouça na porta 80 e despacha também para a porta 80, dentro do cluster. 

E que também o nosso nodePort : 30000, por exemplo. 

Nós podemos fazer essa definição.

Por fim, falta apenas nós selecionarmos qual é o nosso pod. 

Nesse caso vamos definir a label com a chave app e o valor primeiro pod.

svc-pod-1-loadbalancer.yaml
```
apiVersion: v1
kind: Service
metadata:
  name: svc-pod-1-loadbalancer
spec:
  type: LoadBalancer
  ports: 
    - port: 80
      nodePort: 30000
  selector:
    app: primeiro-pod
```

Tudo perfeito! 

Basta agora nós copiarmos essas mesma definição, vir no nosso Google Cloud Platform e criar esse arquivo que vai ser o nosso “lb.yaml”. 

Nós colamos sem nenhum mistério: 

```
kubectl apply -f lb.yaml 
```

e ele vai criar para nós sem nenhum problema.

Se nós viermos agora dentro do nosso cluster na atividade na parte visual dele, nós conseguimos vir em “Serviços e entradas” e olhe só que legal: está - o nosso serviço que nós acabamos de criar! E mostra que tem 1 de 1 pod sendo gerenciado por ele no nosso “cluster-1”.

Ele está terminando de criar os endpoints para acesso. 

Se nós continuarmos atualizando, vai ser bem rapidinho, nós vamos conseguir acessar esse nosso pod a partir do próprio navegador.

Então se vocês estivessem assistindo agora em tempo real, vocês também conseguiriam ao mesmo tempo que eu fazer o acesso a esse pod, porque nesse exato momento ele está sendo publicado e sendo possivelmente acessado com o LoadBalancer do Google Cloud Platform - já tudo integrado sem nenhum problema, sem nenhuma configuração adicional na gestão de balanceamento de carga que acabou de ficar pronto.

Basta nós clicarmos no link que foi gerado o do IP. 

Ele está alertando sobre o redirecionamento e está o nosso nginx, que é o nosso pod-1 sem nenhum problema na web. 

Então agora que nós já nos familiarizamos com os três tipos de serviço, ClusterIP, NodePort e LoadBalancer, nós vamos colocar eles na prática em uma aula em que nós vamos trabalhar com eles em cima do nosso projeto, do portal de notícias e nós vamos sedimentar o conteúdo que nós aprendemos agora nessas últimas aulas.


### o que aprendemos?
* o que sao e para que servem os services
* como garantir estabilidade de IP e DNS
* como criar um service
* labels sao responsaveis por definir a relaçao service x pod
* um clusterIP funciona apenas dentro do cluster
* um NodePort expoe pods para dentro e fora do cluster
* um loadbalacer tambem é um NodePorte ClusterIP
* um loadbalacer é capaz de automaticamente utilizar um balanceador de carga de um cloud provider

### Acessando o portal
Como eu falei para vocês, agora nós vamos colocar a mão na massa com prática em cima do que nós já vimos sobre serviços e pods.

O primeiro passo que nós vamos fazer é colocar o nosso “portal-noticias” com o NodePort para que nós consigamos acessar ele de fora do nosso cluster.

#### kubectl delete pods –all 
Então, primeiramente, por questão de organização, eu vou tirar todos esses pods que nós já temos em execução com o comando 

```
kubectl delete pods –all 
```

e vou fazer a mesma coisa para os serviços; para nós ficarmos com todo o nosso projeto limpinho, nós não vamos precisar desses pods que nós usamos para entender os conceitos de serviço agora.

#### kubectl delete svc – all
Vou fazer a mesma coisa com os serviços 

```
kubectl delete svc – all
```

Removidos. 

no Visual Studio Code eu vou deixar apenas o pod, o arquivo do pod do nosso “portal-noticias. Pronto, removido! Agora só o nosso “portal-noticias” e a partir daqui nós vamos definir um serviço para fazermos a exposição desse nosso *pod.

E como nós vamos fazer isso agora? 

Nós precisamos primeiramente definir um serviço para ele, mas nós vimos que para definir um serviço para um pod nós precisamos definir uma label para ele.

Então eu vou definir uma label chamada app: portal-noticias, que nada impede de nós termos uma chave com um valor igual ao name. 

E também, aquela questão de documentação, eu vou definir em ports: - containerPort: 80.

E agora nós podemos finalmente criar o nosso serviço - que eu vou chamar de o arquivo de “svc-portal-notícias.yaml”. Sem nenhum mistério!

svc-portap-noticias.yaml
```
apiVersion: v1
kind: Pod
metadata: 
  name: portal-noticias
  labels:
    app: portal-noticias
spec:
  containers:
    - name: portal-noticias-container
      image: aluracursos/portal-noticias:1
      ports:
        - containerPort: 80
```

A API version que nós vamos colocar vai ser V1. 

O kind nós já vimos que vai ser um Service e a partir daí nós definimos um metadata:, que eu vou dar um name para ele - que vai ser svc-portal-noticias. 

Nas especificações do tipo dele nós vamos colocar como type: NodePort, porque nós queremos acessar de fora do cluster.

Em ports:, o que nós vamos definir? 

Que dentro do cluster nós queremos que quando ele ouça algo na porta 80 e encaminhe para a porta 80 do pod que está sendo gerenciado por ele.

Então nós podemos definir de maneira implícita só o port uma vez, não precisamos definir também nosso TargetPort; porque se eu escrever só o port, ele já assume que nós estamos definindo igualmente.

Então vou deixar comentado só para vocês entenderem isso e frisarem essa ideia e agora nós conseguimos definir o nosso NodePort, que eu vou colocar na porta 30000 - porque nós temos essa restrição entre 30000 e 32767, 32767. 

Eu vou manter na 30000.

E por fim, nós precisamos que também colocar o nosso seletor. 

Então eu quero selecionar o recurso que tenha a chave app e o valor de portal-noticias. 

Tudo correndo bem, podemos agora limpar o nossoPowerShell e executar um 

kubectl apply -f .\portal-noticias.yaml 

e 

kubectl apply -f .\svc-portal-noticias.yaml.

svc-portal-noticias.yaml
```
apiVersion: v1
kind: Service
metadata: 
  name: svc-portal-noticias
spec:
  type: NodePort
  ports:
    - port: 80
      #targetPort: 80
      nodePort: 30000
  selector: 
    app: portal-noticias
```

Tudo correndo bem, ele vai estar em execução e agora nós podemos abrir uma nova aba do nosso navegador. 

Eu vou abrir para nós fazermos o acesso ao nosso 

localhost:30000.

E olhe só a mágica! 

Agora nós conseguimos acessar a nossa aplicação a partir do mundo externo. 

Nós não estamos mais dentro do nosso cluster e vale lembrar que, caso você esteja fazendo isso dentro do Linux, você vai precisar fazer o mapeamento com o seu IP do Minikube. 

Então sem mistérios vocês vão precisar utilizar aquele internal IP para fazerem o acesso sem nenhum problema.

Então basicamente é isso que vocês têm que fazer; utilizar um INTERNAL-IP para fazer a comunicação não LocalHost.

### subindo o sistema
O que nós temos até então é o nosso portal de notícias sendo gerenciado por esse serviço do tipo NodePort, que permite o acesso do mundo externo ao nosso pod dentro do nosso cluster.

Mas o que nós queremos? 

Como nós falamos, criar um serviço e um pod responsáveis no caso pelo sistema de notícias onde nós vamos cadastrar. 

Esse sistema também vai prover para o nosso portal essas notícias para que nós possamos exibir.

Então, como nós queremos acesso do mundo externo ao nosso pod do sistema de notícias e também ao mundo interno do nosso cluster, para que o nosso portal consiga consumir essas notícias, nós precisamos criar um NodePort e um pod no caso - obviamente com a imagem do nosso sistema. 

Então vamos fazer isso.

Eu vou abrir o nosso Visual Studio Code mais uma vez e nós vamos criar o nosso 'sistema-noticias.yaml”, o arquivo de declaração dele.

Vamos achar “apiVersion: v1”, o tipo que nós queremos criar é um kind: Pod e no metadata: dele vamos chamar de name: sistema-noticias. 

Sem nenhum problema, nenhuma mudança.

E como mais uma vez, ele também vai ser gerenciado por outro serviço, uma label com app: sistemas-noticias.

Nas especificações vamos definir as configurações do container, onde o name: dele vai ser sistema-noticias-container. 

na image:, ao invés de nós utilizarmos a nossa clássica aluraCursos/portal-noticias, nós vamos usar o aluracursos/sistema-notícias; 

a imagem que contém todas as informações do nosso sistema, toda implementação para nós podermos executar.

Vamos botar o nosso ports: com o “- containerPorts:80”, que nós estamos deixando claro que a nossa aplicação da aluraCursos/sistema-noticias é executada na porta 80. 

Como nós temos dois pods diferentes, cada um vai ter o seu respectivo IP, não vai ter nenhum conflito de porta.

sistema-noticias.yaml
```
apiVersion: v1
kind: Pod
metadata: 
  name: sistema-noticias
  labels:
    app: sistema-noticias
spec:
  containers:
    - name: sistema-noticias-container
      image: aluracursos/sistema-noticias:1
      ports: 
        - containerPort: 80
```

E por fim, precisamos agora criar o nosso serviço para esse sistema, então: “svc-sistema-noticias.yaml” e vamos lá! 

Digitamos apiVersion: v1. 

Nós queremos expor ele para o mundo externo então: kind: Service, com um metadata:, um name: svc-sistema-noticias, com as especificações. 

O tipo dele nós vimos que vai ser um type: NodePort.

Em ports: nós vamos fazer o mapeamento de como nós queremos que ele ouça na parte 80 este serviço e despache também para a porta 80.

Mais uma vez, nós não precisamos fazer essa declaração do TargetPort se nós queremos que a entrada seja igual a saída. 

Por fim, o NodePort: - como nós não podemos, nós estamos acessando o nosso cluster de maneira externa, nós precisamos ter uma maneira única de garantir o que nós estamos acessando.

Então como nós já estamos utilizando a porta 30000, nós não podemos utilizá-la de novo, então vamos utilizar a porta 30001.

Finalizando, basta nós usarmos o nosso “select” e definirmos que nós queremos gerenciar o app que tem as informações com a label sistema-noticias. 

svc-sistemas-noticias.yaml
```
apiVersion: v1
kind: Service
metadata:
  name: svc-sistema-noticias
spec:
  type: NodePort
  ports:
    - port: 80
      nodePort: 30001
  selector: 
    app: sistema-noticias
```

Copiando, salvando e nós já conseguimos aplicar. Então, vamos lá!

```
kubectl apply -f .\sistema-noticias,yaml 

```
e 

```
kubectl apply -f “.\svc-sistema-noticias.yaml

```
 e o 
 
```
 kubectl get pods

``` 
 , estão os dois, já em execução.

Se nós voltarmos no nosso navegador e abrirmos agora o nosso localhost:30001... está o nosso sistema de notícias!

Ele vai ser responsável por todo cadastro de notícias dentro do nosso sistema e nós vamos cadastrar todas essas notícias a partir daqui, mas nós devemos ter em algum lugar para guardar essas noticias, inclusive, por isso está reclamando em cima para nós guardarmos a informação dessas notícias - e isso vai ser exatamente um banco de dados.

Então nós precisamos também subir um banco que vai ser responsável por guardar as informações da nossa notícias, e esse banco vai se comunicar o nosso sistema.

### subindo o banco
Agora vai ser o seguinte: nós precisamos, como nós vimos, de alguma maneira criar um banco de dados para que nós possamos nos comunicar com o nosso sistema e guardar as notícias. 

Precisamos ter uma forma de armazenar as nossas notícias.

Então se nós viermos na nossa apresentação, nada mais válido do que nós criarmos um pod e um serviço, para que nós possamos nos comunicar com ele.

E para isso, como nós queremos comunicação apenas dentro do cluster. 

Nós não queremos que o nosso banco seja acessível para o mundo externo, nós podemos criar um ClusterIP para ele. 

Nada de misterioso.

Então vamos colocar a mão na massa, vamos criar o nosso “db-notícias.yaml”, vamos definir a nossa apIVersion: v1, o kind: Pod e no metadata: vamos colocar um name: db-noticias. 

Como ele vai ser gerenciado por um serviço, precisamos de uma label que vai ser app: db-noticias.

Nas especificações nós vamos botar sobre o nosso container, que vai ter um nome de db-noticias-container. 

Ele vai utilizar a imagem da aluracursos/mysql-db:1. 

Não vai ser nenhuma das outras imagens, vai ser uma imagem já prontinha com o nosso banco para nós podermos utilizar.

E o nosso “ports:”? 

O que nós vamos definir no nosso containerPort:? 

Nós vamos falar para ele, e para todo mundo que vê esse arquivo, que o container dessa aplicação do MySQL por padrão é executado na 3306. 

Pod, a princípio, bem definido.

db-noticias.yaml
```
apiVersion: v1
kind: Pod
metadata: 
  name: db-noticias
  labels:
    app: db-noticias
spec:
  containers:
    - name: db-noticias-container
      image: aluracursos/mysql-db:1
      ports:
        - containerPort: 3306
```

Vamos definir o nosso serviço, como “svc-db-noticias.yaml” e vamos digitar apIVersion: v1, kind: Service e em metadata: vai ser “name:” - e definimos o que?

O nosso svc-db-noticias e em spec: definimos o tipo - que não vai ser o NodePort, e sim um ClusterIP.

Em ports: nós vamos definir que nós queremos que as requisições dentro do cluster cheguem neste IP do nosso serviço na porta 3306 e saiam também na 3306. 

Por fim, basta nós selecionarmos o que nós vamos gerenciar, então: app: db-noticias. 

Nós salvamos.

svc-db-noticias.yaml
```
apiVersion: v1
kind: Service
metadata:
  name: svc-db-noticias
spec:
  type: ClusterIP
  ports:
    - port: 3306
  selector:
    app: db-noticias
```

Nós vamos no nosso banco de dados, no nosso PowerShell e digitamos 

kubectl apply –f e passamos o nosso .\db-noticias.yaml. 

Ele foi criado e 

kubectl apply –f, nosso sistema também “.\svc-db-noticias.yaml” devidamente criado.

Se nós viermos e vermos o serviço, está sem nenhum problema em execução no nosso clusterIP. 

Se nós viermos agora no nosso 

kubectl get pods

, o que nós vamos ver? 

Que tem um erro no pod do db!

Por quê? 

Vamos descobrir, vamos executar kubectl describe pods e passar o nosso db-noticias. 

Ele baixou, atribuiu com sucesso ao nó, baixou a imagem - no caso nós tínhamos encontrado - criou o container e inicializou o nosso container.

Só que, o que aconteceu? 

Ele ficou reiniciando indefinidamente. 

Por quê? 

Vamos descobrir. 

Vamos olhar na documentação também do MySQL no Docker Hub. 

Se nós viermos olhando com bastante paciência, nós descobrimos que essa parte de variáveis de ambientes precisa ser definida, porque nós precisamos informar diversas informações fim das contas.

Como, por exemplo: qual é a senha do banco que nós estamos criando, qual é o nome do banco, qual é a senha de root, dentre outras coisas. 

Nós precisamos explicitar essas informações.

Só que no nosso Visual Studio Code nós não estamos fazendo isso, então a pergunta que fica é: como nós podemos utilizar variáveis de ambiente com o Kubernetes para definirmos as informações do nosso container?

### o que aprendemos?
* como escolher o melhor tipo de service para cada situaçao
* como comunicar diversos pods atraves de um service
* devemos definir informaçoes necessarias para inicializaçoes de pods

### Utilizando variaveis de ambiente
Então,como nós conseguimos fazer o nosso banco funcionar agora? 

Porque ele é baseado na imagem do MySQL e então nós precisamos definir para este container algumas informações.

E se nós viermos olhar dentro da página do MySQL no Docker Hub, nós vamos encontrar que nós precisamos obrigatoriamente definir essa variável chamada MYSQL_ROOT_PASSWORD, onde ela vai ser a nossa senha de root.

Nós também temos opcionalmente a possibilidade de definir qual vai ser o nosso banco, a nossa senha sem ser de root. 

Se o nosso banco permite senha vazia, ou não - mas também é opcional - qual vai ser. 

Todas essas informações que nós vamos utilizar na inicialização do nosso banco.

Então nós precisamos ter alguma maneira de que no nosso arquivo de definição, para colocarmos essas informações para o nosso container dentro do nosso pod.

E como nós fazemos isso? Todas essas informações para um container nós estamos definindo dessa maneira: o nome, a imagem, as portas que nós estamos documentando que estão expostas.

#### Environment Variables
Então nada mais válido do que embaixo nós também definirmos as env (Environment variables), que nós vamos definir - e é bem fácil, é bem simples, sem muito mistério. 

Nós conseguimos agora colocar o - name: para essa variável, que no caso nós vamos definir primeiro a ”MYSQL_ROOT_PASSWORDS”, que é obrigatório; e um valor para ela, que no caso do nosso banco vai ser value: “q1w2e3r4”.

db-noticias.yaml
```
apiVersion: v1
kind: Pod
metadata: 
  name: db-noticias
  labels:
    app: db-noticias
spec:
  containers:
    - name: db-noticias-container
      image: aluracursos/mysql-db:1
      ports:
        - containerPort: 3306
      env:
        - name: "MYSQL_ROOT_PASSWORD"
          value: "q1w2e3r4"
```

E nós precisamos no nosso caso específico, não é obrigatório para subir uma imagem do MySQL, mas nós vamos fazer também a definição do MYSQL_PASSWORD e do MYSQL_DATABASE.

E como nós podemos definir múltiplas variáveis de ambientes? Será que nós precisamos repetir tudo isso d? Na verdade, não; basta dentro ainda de env:, nós alinharmos outro - name:, que vai entender com esse travessão que nós estamos começando uma nova definição, de uma nova variável e nós colocamos o nome dela que vai ser name: “MYSQL_DATABASE” e o seu respectivo valor que vai ser value: “empresa”, o nome do banco que nós vamos trabalhar.

E por fim, a última variável que nós vamos definir vai ser também o nosso MySQL_Password. Vamos colocar ele : - name: “MYSQL_PASSWORD” e o nosso valor vai ser o mesmo do nosso root(value: “q1w2e3r4”).

db-noticias.yaml
```
apiVersion: v1
kind: Pod
metadata: 
  name: db-noticias
  labels:
    app: db-noticias
spec:
  containers:
    - name: db-noticias-container
      image: aluracursos/mysql-db:1
      ports:
        - containerPort: 3306
      env:
        - name: "MYSQL_ROOT_PASSWORD"
          value: "q1w2e3r4"
        - name: "MYSQL_DATABASE"
          value: "empresa"
        - name: "MYSQL_PASSWORD"
          value: "q1w2e3r4"
```

Com isso feito, basta nós voltarmos no nosso PowerShell e deletarmos esse pod atual do nosso db-noticias. 

A partir daí nós vamos reiniciar e recriar este pod manualmente.

Para isso, é só nós utilizarmos o comando que nós viemos trabalhando desde sempre, que é o kubectl apply, e passarmos o nosso arquivo de definição do banco. 

Ele vai ser criado e se nós digitarmos um kubectl get pods, olhe que legal: ele está com status de “running”.

Mas como nós podemos verificar agora se está tudo funcionando direito? 

#### Acessar o bash do banco de dados
Vamos executar esse pod em modo interativo do nosso db-noticias e acessar o banco diretamente dentro dele. 

Para isso, nós acessamos ele com bash e executamos o nosso “mysql -u root –p, colocamos a nossa senha q1w2e3r4 e o banco está rodando. 

```
kubectl exec -it db-noticias -- bash

mysql -u root -p
```

Se nós digitarmos um 

```
show database;
```

temos já o nosso banco “empresa”!

E se nós usarmos esse banco, nós também conseguimos ver todas as configurações de tabela. 

```
use empresa;
```

Já está o show tables. 

```
show tables;
```

Nós conseguimos selecionar o usuário para nós conseguirmos fazer o nosso login, sem nenhum problema.

```
select * from usuario;
```

E só para deixar claro: todas essas configurações de tabelas e de banco já vieram configuradas nessa imagem (mysql-db) para nós não precisarmos nos preocupar com popular o banco.

a questão é só o acesso. 

Então nós fizemos a definição de tudo o que nós queremos utilizar para inicializar o container do nosso banco. 

E agora, o que nós precisamos fazer? 

Se nós voltarmos no nosso login da Alura e apertarmos a tecla “F5”, ainda não está funcionando. 

Mas por que, se o banco já está rodando?

Vamos voltar para o nosso PowerShell e digitar um kubectl get pods. 

Simplesmente porque o nosso sistema de notícias não é vidente para saber onde está o banco, qual o endereço dele e quais são as informações que ele deve usar para acessar o banco.

Então se nós dermos uma olhada mais detalhada também dentro desse sistema de notícias, o que nós veremos? 

Nós veremos que nós temos um arquivo chamado bancodedados.php.

Dando uma olhada dentro desses arquivos nós percebemos que nós precisamos também definir outras variáveis de ambiente para esse pod.

Como: qual é o host do banco (HOST_DB), qual é o usuário(USER_DB), qual é a senha (PASS_DB) e qual é o nome do banco (DATABASE_DB) que nós queremos utilizar. 

Então essas informações nós também vamos precisar utilizar uma variável. 

Nesse caso, quatro variáveis de ambiente para fazer o acesso deste nosso pod do sistema ao banco.

Só que, se nós voltarmos no nosso arquivo, o que nós temos? 

Observando de maneira um pouco mais crítica, nós temos as configurações do nosso pod, toda a definição dele. 

Mas nós também temos a definição de ambiente, de variáveis de ambiente e de configuração.

Então se nós formos um pouco mais detalhistas, nós vamos ver que nós estamos misturando arquivos de configuração, trechos de configuração com o nosso conteúdo de imagem.

Nós estamos deixando tudo muito acoplado. 

Seria interessante se nós separássemos isso para mantermos as responsabilidades - onde todo esse trecho vai ser responsável pela definição do pod e da imagem que vai ser utilizada para ele.

E nas envs nós poderíamos separar isso de alguma maneira para que seja só as partes de configuração para deixar este pod o máximo de portável possível. 

Nós não estamos atrelando ele à nenhuma configuração específica.

### criando um ConfigMap
Então, como nós podemos extrair essas informações de configuração para fora do nosso arquivo de definição do nosso banco de dados? 

Como nós podemos tornar o nosso pod nesse sentido de ser mais portável, para nós não acoplarmos as configurações com a definição do nosso pod?

Como eu falei para vocês, o kubernetes vai muito além de ser um simples orquestrador de containers e ele já nos provê diversas soluções nativas para diversos problemas. 

Para esse caso não seria diferente.

#### ConfigMap
Nós temos a solução chamada ConfigMap, onde ele vai ser responsável por 
```diff
+ armazenar essas configurações que nós precisamos utilizar dentro de determinados pods, determinados recursos. 
```

Nós podemos guardar dentro deles para não acoplarmos o nosso recurso com informações de configuração, por isso um ConfigMap.

E ele vai muito além, nós vamos extrair todo esse trecho que nós definimos no nosso banco de dados para dentro de um ConfigMap. 

Nós vamos aprender como criar ele também.

Mas ele também vai muito além disso, porque ele permite a reutilização e o desacoplamento.

Então, a partir de determinado momento nós conseguimos reutilizar configurações definidas dentro de ConfigMaps em diferentes pods. 

Nós podemos ter pods utilizando diferentes ConfigMaps.

Então isso nos dá um poder de desacoplamento muito grande e de reutilização também. 

Mas como é que nós criamos um ConfigMap? 

É bem fácil! 

Vocês viram como nós criamos um pod e um serviço até então, mas criar um ConfigMap é tão fácil quanto.

Vamos voltar no nosso Visual Studio Code e vamos criar um novo arquivo chamado “db-configmap.yaml” e dentro dele nós vamos definir uma apIVersion: v1 e o kind: ConfigMap.

No metadata: nós vamos definir um name: db-configmap e nós vamos definir também agora o data:, o conteúdo dele. 

Não temos um spec como nós tínhamos tradicionalmente com os nossos outros recursos.

dentro nós vamos fazer agora a definição de chave e valor, como nós já vínhamos fazendo antes. 

Então, vamos só recortar isso e colocar. 

Vamos fazer a seguinte mudança: nós não vamos definir um env, não vamos definir um name também. 

O que nós vamos fazer vai ser definir, nesse caso, chaves e valores.

Então nós vamos definir um MySQLRoot Password, onde value: “q1w2e3r4”. 

Colocamos isso sem nenhum problema e podemos até colocar fora das nossas aspas e vai ser a mesmíssima ideia para os outros campos que nós já temos. 

Vai ter um name: “MySQL_DATABASE” e colocamos também um valor para ele, que vai ser value: “empresa”.

Repare em como nós estamos fazendo. 

Nós estamos definindo todos os nossos campos, todas as nossas chaves e os valores que nós queremos para este ConfigMap. 

A partir desse momento, quando nós criarmos ele nós vamos conseguir reutilizar tudo sem nenhum problema.

Então definimos o nosso MySQL_ROOT_PASSWORD, o nosso MySQL_DATABASE e o nosso MySQL_PASSWORD, e salvamos o arquivo. 

db-configmap.yaml
```
apiVersion: v1
kind: ConfigMap
metadata:
  name: db-configmap
data:
  MYSQL_ROOT_PASSWORD: q1w2e3r4
  MYSQL_DATABASE: empresa
  MYSQL_PASSWORD: q1w2e3r4
```


Vamos salvar também a operação que nós fizemos no nosso db-noticias.

db-noticias.yaml
```
apiVersion: v1
kind: Service
metadata:
  name: svc-db-noticias
spec:
  type: ClusterIP
  ports:
    - port: 3306
  selector:
    app: db-noticias
```

E agora, se nós viermos no nosso PowerShell... 

Basta nós executarmos um 

kubectl apply –f e passar o nosso .\db-configmap.yaml e foi criado. 

Simples assim!

#### kubectl get configMap
Se nós dermos um 

```
kubectl get configmap
```
, temos o nosso db-configmap criado há 8 segundos. 

#### kubectl describe configmap
Nós podemos também descrever ele com o comando 

```
kubectl describe configmap db-configmap
```

E nós vamos ter todas as informações que nós queremos, o nosso MySQL_DATABASE, o nosso MySQL_PASSWORD e ele sempre fazendo ; a chave e o valor, a chave e o valor; a chave e o valor; a chave e o valor.

Olhe que simples e fácil! 

### aplicando o ConfigMap ao projeto
Nós já temos o nosso ConfigMap em execução, mas nós precisamos agora de uma maneira de importarmos esses valores (MYSQL_ROOT_PASSWORD: q1w2e3r4; MYSQL_DATABASE: empresa; MYSQL_PASSWORD: q1w2e3r4) para dentro do container do nosso pod.

E a declaração vai ser bem parecida de como nós já tínhamos antes. 

Nós temos o nosso env: - e qual é a variável que nós queremos criar? 

Uma variável chamada MySQL_ROOT_PASSWORD, mas agora nós não vamos simplesmente definir um value para ela, nós vamos definir de onde ela vem.

#### valueFrom
Então vai ser valueFrom: e nós vamos informar a origem dela - que vem de um configMap”, que tem uma referência a uma chave, então configMapKeyRef. 

O nome desse configMapKeyRef é db-configmap e a chave que nós queremos colocar dentro dessa nossa variável é exatamente essa, de MYSQL_ROOT_PASSWORD.

Então, MYSQL_ROOT_PASSWORD, nós estamos fazendo o acesso daqui (db_noticias.yaml) (db-configmap.yaml)e estamos armazenando (MYSQL_ROOT_PASSWORD), certo?

db-noticias.yaml
```
apiVersion: v1
kind: Pod
metadata: 
  name: db-noticias
  labels:
    app: db-noticias
spec:
  containers:
    - name: db-noticias-container
      image: aluracursos/mysql-db:1
      ports:
        - containerPort: 3306
      env:
        - name: MYSQL_ROOT_PASSWORD
          valueFrom:
            configMapKeyRef:
              name: db-configmap
              key: MYSQL_ROOT_PASSWORD
```

E se nós quiséssemos fazer isso para MySQL_DATABASE e para MySQL_PASSWORD também, nós teremos que repetir toda essa declaração mais duas vezes. 

Então nosso arquivo, por mais que ficasse portável, ele ficaria bem grande também.

#### usar todas as variaveis do configMap
Como nesse caso nós queremos fazer declaração de todas as variáveis que estão dentro do nosso configMap, nós podemos fazer uma declaração mais simples e ao invés de importar uma a uma, nós podemos importar todo o nosso configMap de uma única vez.

Como? 

Nós podemos fazer a referência ao invés de variável à variável, nós podemos fazer referência direto ao configMap. 

#### configMapRef e envFrom
Então,configMapRef e qual é o nome desse configMap? 

É db-configmap! Salvamos ele .

db-noticias.yaml
```
apiVersion: v1
kind: Pod
metadata: 
  name: db-noticias
  labels:
    app: db-noticias
spec:
  containers:
    - name: db-noticias-container
      image: aluracursos/mysql-db:1
      ports:
        - containerPort: 3306
      envFrom:
        - configMapRef: db-configmap
```

E agora nós já temos ele em execução, então nós vamos fazer ele parar para ele usar o configMap efetivamente, 

kubectl delete pod db-noticias. 

E nós vamos aplicar novamente com essa nova declaração que nós estamos fazendo ao nosso configMap.

Então, kubectl apply -f .\db-noticias.yaml, se nós digitarmos um kubectl get pods e agora, ele está em execução.

Mais uma vez, confirmando: kubectl exec –it no nosso db-noticias – bash e temos o nosso mysql -u root –p; a nossa senha q1w2e3r4 e no show databases está o nosso banco empresa.

Só que... O que nós precisamos agora? 

Se nós voltarmos no nosso navegador, no nosso sistema, e apertarmos a tecla “F5”, nós precisamos ainda fazer a referência a esse banco - que era o que nós já estávamos planejando.

Se nós acessarmos o nosso sistema com comando também 

kubectl exec –it no nosso sistema-noticias, 

nós conseguimos ver o que ? 

Se ele estava nos arquivos nós temos esse arquivo chamado “bancodedados.php”.

Mas nós olhando esse arquivo nós conseguimos ver que precisamos declarar essas quatro variáveis, para que ele consiga localizar o banco.

Qual é o host, o endereço desse banco, qual é o usuário dele, a senha e o nome do banco que nós queremos utilizar - para nós fazermos isso é bem simples

Então, o que nós vamos fazer agora? 

Nós vamos simplesmente criar um novo configMap, só que dessa vez para o nosso sistema.

Então vamos ter agora o nosso sistema-configmap.yaml. 

Dentro dele, a versão da API vai continuar sendo a v1, o kind: ConfigMap, no nosso metadata: vamos definir um name: sistema-configmap.

E por fim, no nosso data: nós vamos definir essas quatro variáveis. 

O nosso “HOST-DB” vai ter um valor e como nós queremos fazer a comunicação do nosso serviço, do nosso pod de sistema com o serviço do nosso banco de dados.



O que nós precisamos? 

Eu vou abrir uma nova aba do PowerShell e digitar kubectl get svc. 

Nós precisamos fazer a referência ou ao nosso DNS, que é o nosso nome do nosso serviço para nós acessarmos o nosso pod do banco, ou ao IP também.

Ambos estão ouvindo na porta 3306, então vamos fazer isso. 

Vamos colocar que o nosso “HOST_DB”, nada mais é do que o nosso próprio DNS. 

Vamos utilizar ele para mostrar que funciona também. 

Vamos copiar e vamos colocar ele na porta 3306.

Vamos definir o nosso USER_DB, que é “root”, o nosso Pass_Db que é q1w2e3r4 e por fim o nosso DATABASE_DB, que é o empresa.

sistema-configmap.yaml
```
apiVersion: v1
kind: ConfigMap
metadata:
  name: sistema-configmap
data:
  HOST_DB: svc-db-noticias:3306
  USER_DB: root
  PASS_DB: q1w2e3r4
  DATABASE_DB: empresa
```

Basta nós voltarmos agora. 

Vamos sair de dentro desse container, desse pod, vamos digitar 

kubectl apply –f no nosso .\sistema-configmap.yaml

. E ele foi criado.


E agora nós precisamos no nosso sistema de notícias fazer a mesma coisa que nós fizemos antes, importar este configMap para uso, ou seja, envFrom: configmapRef e o nome dele, que é o nosso sistema-configmap.

sistema-noticias.yaml
```
apiVersion: v1
kind: Pod
metadata: 
  name: sistema-noticias
  labels:
    app: sistema-noticias
spec:
  containers:
    - name: sistema-noticias-container
      image: aluracursos/sistema-noticias:1
      ports: 
        - containerPort: 80
      envFrom:
        - configMapRef:
          name: sistema-configmap
```

Vamos precisar agora deletar e recriar ele: 

delete pod sistema-notícias 

e vamos aplicar novamente 

kubectl apply -f .\sistema-noticias.yaml. 

Foi criado.

E se nós voltarmos agora e apertarmos a tecla “F5”, o erro some. 

Então agora nós já conseguimos fazer o login, que nós vimos no banco que é “admin” e “admin”. 

Podemos vir, digitarmos e estaremos autenticados. 

Podemos cadastrar as notícias.

Então, podemos vir em “Nova Notícia” e colocarmos uma notícia com alguma informação qualquer e colocarmos também uma foto, onde podemos colocar uma foto qualquer da Alura. Vamos salvar.

Repare que ele salvou e agora no nosso portal nós queremos que esse portal se comunique com esse sistema para fazer a exibição dessa notícia para nós. 

Se nós queremos fazer essa comunicação voltando na nossa apresentação, nós queremos também fazer essa comunicação via variável de ambiente.

Se nós viermos no nosso PowerShell e entrarmos em modo interativo dentro do nosso portal-noticias, o que nós vamos ver? 

Vai ser algo bem parecido com o nosso sistema, nós temos um arquivo chamado de “configuracao”, nesse arquivo nós precisamos definir qual é o IP do nosso sistema (IP_SISTEMA). 

Bem simples e prático.

Então vamos voltar no nosso Visual Studio Code e vamos criar o nosso também “portal-configmap.yaml” e dentro dele vamos definir também todas as mesmas coisas que nós já viemos fazendo com os configMaps.

Então, configMap, vamos definir um metadata: para ele, que vai ser um name: portal-configmap. Vamos definir a data:, que vai ser IP_SISTEMA:.

E nesse momento, o que vai acontecer?

Quem está utilizando o Windows assim como eu, vai colocar o IP do nosso sistema.

E o nosso sistema está sendo executado em qual porta? 

```
localhost:30001
```
, onde nós definimos o nosso NodePort.

Então quem está utilizando Windows vai colocar 
“http://localhost”

Atentem-se ao “http://”, ele é necessário. 

Na porta 30001, caso você esteja utilizando o Linux é aquela velha história: você vai precisar colocar o seu INTERNAL_IP. 

Então, caso seja 192.168.99.106, você vai colocar também 192.168.99.106, mas como eu estou no Windows vou deixar o localhost.

portal-configmap.yaml
```
apiVersion: v1
kind: ConfigMap
metadata: 
  name: portal-configmap
data:
  IP_SISTEMA: http://192.168.99.106:30001 #IP e porta do node
```

E agora nós vamos fazer o que? 

Nós vamos simplesmente aplicar este arquivo também ao nosso cluster, 

kubectl apply -f .\portal-configmap.yaml 

e vamos utilizar esse configMap dentro do nosso portal de notícias.

Com o nosso envFrom e vamos colocar mais uma vez o nosso configMapKeyRef, onde o nome do configMap que nós queremos fazer referência é o nosso portal-configmap.

portal-noticias.yaml
```
apiVersion: v1
kind: Pod
metadata: 
  name: portal-noticias
  labels:
    app: portal-noticias
spec:
  containers:
    - name: portal-noticias-container
      image: aluracursos/portal-noticias:1
      ports:
        - containerPort: 80
      envFrom:
        - configMapRef:
            name: portal-configmap
```

Vamos agora voltar, sair do nosso container dentro do nosso pod e recriar esse pod no nosso portal de notícias e vamos reaplicar com essa devida mudança.

Então vai ser o nosso 

kubectl apply –f em cima do nosso novo arquivo. 

Então, 

kubectl apply -f .\portal-noticias.yaml.

eu só esqueci de colocar o espaço, ele ficou com um espaço a mais, estão espere aí! portal-configmap e não é configMapKeyRef, é ConfigMapKeyRef só, porque agora nós estamos fazendo a referência só ao configMap, e não a uma chave dele.

E vamos aplicar. 

Se nós voltarmos agora no nosso navegador, vamos colocar, apertar a tecla “F5” - e olhe só, está a nossa notícia com uma imagem e a nossa informação que nós definimos.

Comunicamos os três pods via serviço, utilizando as melhores práticas, um NodePort para os dois que precisam ser NodePort e um ClusterIP, para o que é o ClusterIP.

E também, se nós voltarmos na nossa aplicação, para visualizarmos tudo o que foi feito, nós também utilizamos as variáveis de ambiente para mantermos essa comunicação agnóstica. Ali nós vamos definir onde eles estão.

### para saber mais: NodePort e IP´s

No último vídeo, definimos como variável de ambiente o endereço do sistema de notícias para o nosso portal de notícias conseguir acessá-lo. Fizemos isso utilizando o IP do node seguido da porta exposta pelo nosso NodePort, nesse caso localhost:30001.

Caso tivéssemos múltiplos nodes em nosso cluster, tudo funcionaria da mesma maneira, pois as portas mapeadas pelo NodePort são compartilhadas entre os IP's de todos os nodes.

Mais informações podem ser adquiridas em https://kubernetes.io/docs/concepts/services-networking/service/#nodeport.

### o que aprendemos?
* como definir variaveis de ambiente atraves do campo env
* como desacoplar configuraçoes e definiçoes com um configMap
* como criar e definir um ConfigMap
* como importar variaveis de ambiente com um ConfigMap
* como importar todo um ConfigMap com o campo envFrom

### Conhecendo ReplicaSets
Uma das primeiras coisas que falamos no início do nosso curso, foi que quando criamos um Pod, o Kubernetes tem total capacidade de definir onde ele vai ser executado, através daquele componente chamado scheduler.

Mas, também, vimos que caso este Pod falhe, o Kubernetes tem total capacidade de criar um novo Pod e substituir o antigo, que parou de funcionar. Com as mesmas características, mas, sendo um novo Pod e não o mesmo.

```diff
+ Isso porque os Pods são efêmeros, então, eles devem estar prontos para serem substituídos por questão de falha ou de atualização, sem causar grande impacto na nossa aplicação, como um todo.
```

Mas, como o Kubernetes vai conseguir fazer isso? 

Para isso, temos recursos, como nós já vimos. 

E esses dois recursos vão nos ajudar a resolver este tipo de problema: os ReplicaSets e os Deployments.

Nós vamos começar falando sobre os ReplicaSets e depois vamos falar sobre os Deployments.

Para entendermos o que é um ReplicaSet é bem fácil. 

Vamos visualizar este Pod. 

Nós acabamos de ver que, caso ele falhe, pare de ser executado, seja interrompido, ele morreu para sempre. Ele nunca mais vai voltar, não existe nenhuma maneira de fazer ele voltar.

E a pergunta que queremos responder é como conseguimos criar outro para assumir o lugar dele, de maneira automática.

Como assim? 

Vamos visualizar. Temos os nossos três Pods do banco de dado de notícias, do portal de notícias e do sistema de notícias. 

Caso, nós pararmos o nosso Pod do portal de notícias, sem nenhum mistério, simulando uma interrupção, o que vai acontecer?

A nossa aplicação do portal não está mais disponível porque acabamos de interromper ela, mas, vamos visualizar só para ter a garantia.

Ou seja, quando nosso Pod foi interrompido, por algum motivo, o que aconteceu? 

Aconteceu que ele não voltou por nenhuma razão. 

E nós queremos contornar esse tipo de situação, que em caso de falha ele volte.

Então, voltando à nossa apresentação, nós temos uma estrutura que resolve isso para nós, que são os ReplicaSets.

```diff
+ Então, vimos que um Pod é uma estrutura que encapsula um ou mais containers e um ReplicaSet nada mais é que uma estrutura que encapsula, pode encapsular, na verdade, um ou mais Pods.
```

Repara nas duas coisas que acabei de falar. 

Ela tem a capacidade de encapsular um ou mais Pods, ou seja, nós não temos a obrigatoriedade de criar um Pod com um ReplicaSet. 

Não é a toa que nós viemos fazendo isso, até agora, no curso. 

E que ele também pode gerenciar um ou mais Pods, ao mesmo tempo.

Logo, se, um desses Pods falhar, e ele nunca mais vai voltar, mas o ReplicaSet vai conseguir criar um novo para nós. 

E isso também vai funcionar para diversos Pods gerenciados por um mesmo ReplicaSet.

Então, o que vai acontecer? 

Caso algum desses Pods falhe, Nós vamos ter um número de Pods desejados diferentes do número de Pods prontos. 

Logo, o próprio ReplicaSet vai criar um Pod novo para substituir esse que parou de funcionar.

E por que nós podemos ter diversas réplicas? 

Um deles é que enquanto este Pod está voltando a ser executado, para que consigamos acessar nossa aplicação, nós temos outras três formas de acessar esta mesma aplicação, porque nós possuímos cópias dela em execução, então, enquanto essa aqui não volta, nós temos outras três para receber as requisições do nosso usuário.

E, também, caso nós estejamos recebendo muitas requisições, nós conseguimos dividir através de um Service que vai fazer o balanceamento de carga, as requisições para esses Pods de maneira bem igual.

Então, vamos colocar a mão na massa. 

Vamos criar o nosso primeiro ReplicaSet. 

É bem fácil. 

Nós vamos criar um novo arquivo, clicando no botão "New File" no canto superior esquerdo da tela, chamado portal-noticias-replicaset.yaml. 

E, dentro desse arquivo, a primeira grande diferença que nós vamos ver é que a versão da api não vai ser só v1, vai ser um grupo específico da v1 que é a 

apps/v1

, que podemos até conferir na própria documentação do Kubernetes.

Então, sobre ReplicaSets, nós conseguimos ver que apiVersion: apps/v1. 

O tipo que nós queremos criar é um ReplicaSet e ele também possui um metadata, então, qual vai ser o nome desse ReplicaSet? 

Vai ser portal-noticias-replicaset.

E uma especificação para ele, o que vai conter neste ReplicaSet. 

É nesse momento, em que talvez você esteja pensando, basta copiar o trecho das especificações do nosso portal-noticias e colar ele aqui no ReplicaSet e está tudo feito.

Não é bem assim. 

Nós vamos ter algumas peculiaridades, então, eu já vou comentar isso para termos como base o que nós vamos utilizar e vamos fazer o seguinte: nós precisamos de início, definir um template.

Qual vai ser o conteúdo, qual vai ser o modelo deste ReplicaSet, qual vai ser o padrão dele? 

Então, nós vamos definir o que no portal-noticias-replicaset? 

As informações do nosso Pod.

Então, o nosso Pod possui o que? 

Ele possui um metadata e esse metadata tem um name, como já está especificado mais abaixo do trecho copiado. 

Vou, até, descomentar este trecho e copiar.

Nós temos o metada que contém um name, um label que é app: portal-noticias, então, já definimos o metadata dos Pods, ou do Pod, no singular, que vai ser gerenciado por este ReplicaSet.

Esse metadata (name: portal-noticias) é do Pod de dentro do ReplicaSet e este metadata (name: portal-noticias-replicaset) é do nosso ReplicaSet. 

O trecho copiado anteriormente já pode ser apagado, inclusive.

E, agora, precisamos definir o que? 

Quais são as especificações do nosso Pod. 

Então, basta pegarmos o mesmo trecho do arquivo portal-noticias.yaml e colocar alinhado com o nosso metadata.

Nós temos todas as informações do nosso Pod, que vai ser gerenciado pelo nosso ReplicaSet. 

Então, dentro de template nós vamos definir todas as informações do nosso Pod.

Agora falta o que? 

Falta definirmos, alinhado com template, o número de réplicas que queremos para nossa aplicação, então, como falei para vocês nós podemos ter um ou mais Pods sendo gerenciados por um ReplicaSet.

Nós podemos definir, por padrão, se nós não informarmos esse número vai ser 1, mas, podemos colocar 1, 2, 3, 4 e podemos colocar o quanto quisermos neste cenário. 

Então, eu vou colocar que nós queremos três réplicas, para caso alguma delas falhe, nós ainda vamos ter duas de backup para receber as requisições do nosso usuário.

E, por fim, falta definirmos mais uma coisa que parece ser um pouco redundante, que acaba sendo, visualmente falando. 

Que por mais que todas essas informações estejam definidas dentro das especificações deste ReplicaSet (metadata: name: portal-noticias-replicaset), o Kubernetes não sabe que este ReplicaSet deve gerenciar este template, que definimos anteriormente.

Nós precisamos fazer o seguinte, informar que o nosso ReplicaSet, assim como um serviço, vai selecionar os recursos que tenham um matchLabels que encaixem, que batam o valor das labels com app: portal-noticias, então, esse matchLabels tem que ser igual, idêntico ao labels.

Senão, não vai funcionar. 

No momento que tentarmos aplicar esse arquivo de definição, ele não vai funcionar. Então, os matchLabels e labels, repara, sempre serão iguais.

```
apiVersion: apps/v1
kind: ReplicaSet
metadata:
  name: portal-noticias-replicaset
spec:
  template: 
    metadata:
      name: portal-noticias
      labels: 
        app: portal-noticias
    spec:
      containers:
        - name: portal-noticias-container
          image: aluracursos/portal-noticias:1
          ports: 
            - containerPort: 80
          envFrom:
            - configMapRef:
              name: portal-configmap
  replicas: 3
  selector: 
    matchLabels:
      app: portal-noticias
```

Se salvarmos ele e viermos no nosso Powershell e executar o nosso 

kubectl apply -f .\portal-noticias-replicaset.yaml

, o que vai acontecer? Ele foi criado.

E se nós usarmos o comando 

kubectl get pods

, nós temos três Pods, como nós definimos no nosso número de réplicas, para o nosso portal de notícias. 

E cada um desses Pods segue a mesma receita.

Não é à toa que todos começam o nome com portal-noticias-replicaset traço um identificador único. 

E todos eles vão estar expondo na porta 80, como já definimos.

Todos vão utilizar as mesmas variáveis do nosso portal do configmap sem nenhuma mudança. 

os três são iguais, só os identificadores que são diferentes.

Não é à toa que se viermos no nosso navegador e tentar acessar o nosso portal temos tudo funcionando.

Se tentarmos cadastrar uma nova notícia no nosso sistema, vamos colocar 'uma notícia' dentro da aba "Título" e vamos colocar 'uma informação' dentro da aba "Notícia". 

Podemos colocar uma nova imagem da Alura, por exemplo e salvar e tudo continua funcionando.

Vão ter duas notícias com a mesma imagem, mas, o conteúdo que definimos é diferente. 

Tudo continua funcionando sem nenhum problema.

Se tentarmos forçar a parada de um desses Pods com o comando 

kubectl delete pod 

e colocar um deles para ser removido, o que vai acontecer? 

Vamos colocar no comando o Pod portal-noticias-replicaset-dkppr, vamos remover e vamos confirmar se, realmente, temos dois ou três Pods em execução.

kubectl get pods, repara que agora temos um novo Pod no lugar daquele, com identificador diferente, porém, com o mesmo comportamento, sem nenhum mistério.

Se nós executarmos um outro comando que é o 

kubectl get rs 

ou 

kubectl get replicasets 

o que vai acontecer: 

Ele vai nos mostrar que o número desejado de Pods, atualmente, por este ReplicaSet é três, que nós definimos no nosso número de réplicas, e que o nosso atual de prontos, que nós temos, também é três. 

Então, tudo vai correr sem nenhum problema.

Para vocês verem mais um cenário eu vou abrir outro Powershell e nós vamos fazer o seguinte. 

Eu vou dividir a tela entre os dois e vou limpar a tela e na da esquerda eu vou comandar 

kubectl get replicaset --watch 

e do outro lado eu vou comandar 

kubectl get pods 

e vou dar um 

kubectl delete pod 

em qualquer um dos três Pods que está sendo gerenciado pelo nosso ReplicaSet.

Vou colocar este Pod no comando 

kubectl delete pod

e vou parar. 

O que aconteceu... por um momento tivemos dois, porque um foi removido, foi interrompido, depois nós tivemos três, mas, ele ainda não estava pronto, e, por fim, nós ficamos no nosso estado desejado, sem nenhum mistério.

E ele foi criado um novo, como já vimos. 

Se utilizarmos o comando 

kubectl get pod 

ele vai ter criado um novo, em relação ao anterior, que nesse caso é o portal-noticias-replicaset-mzskh.

```diff
+ Então, utilizando ReplicaSets nós conseguimos definir que a nossa aplicação deve estar sempre disponível para o usuário, o Kubernetes tem que manter ela sempre disponível em caso de falhas ou interrupções.
```

E também, definir o número de réplicas para o nosso usuário conseguir acessar, caso uma dê problema e ainda não tenha voltado. 

Ou dividir, fazer todo o balanceamento de carga.

Então, por mais que agora, só para finalizarmos, o nosso Pod esteja dentro de um ReplicaSet, o nosso serviço continua funcionando sem nenhuma mudança porque ele seleciona por qualquer um que tenha a chave app com valor portal-noticias.

E ele continua tendo isso porque nós definimos no labels do arquivo portal-noticias-replicaset.yaml, então, não muda ele estar dentro de um ReplicaSet. 

Vai tudo funcionar da mesma maneira.

Agora, o nosso serviço, o que ele faz? 

Para a gente finalizar, vamos voltar na nossa apresentação e ver um trecho que explicita o que está acontecendo agora.

Nós temos, a grosso modo, um serviço balanceando, o nosso acesso a três diferentes Pods, que são iguais. 

Que, nesse caso, estamos utilizando a nossa aplicação localmente com um nodeport para fazer esse acesso.

O nosso serviço, agora, faz todo esse balanceamento sem nenhum mistério, para três Pods gerenciados por um ReplicaSet.

### conhecendo Deployments
Nós acabamos de ver sobre os ReplicaSets, que permitem a criação de Pods de maneira automática, em caso de falha, todo esse controle do estado desejado e do estado atual. 

E nós vamos falar agora sobre o segundo recurso que permite a mesma coisa, que são os Deployments.

Mas, o que muda na prática? 

Nós vimos que um ReplicaSet nada mais é do que esse conjunto de réplicas que permite a criação, de maneira automática, em caso de falhas de um Pod, dentro de um cluster gerenciado por um ReplicaSet.

```diff
+ Mas, um Deployment nada mais é do que uma camada acima de um ReplicaSet. 
```

Então, quando nós definimos um Deployment, nós estamos, automaticamente, definindo um ReplicaSet, sem nenhum mistério.

Mas, o que muda? 

Quando criamos um Deployment, nós criamos um ReplicaSet, mas, o que vem de novo com isso? 

O que ganhamos de adicional? 

Vamos verificar, vamos criar o nosso primeiro Deployment para entendermos.

Para isso, vamos criar um arquivo que vai ser o nosso nginx-deployment.yaml e a definição dele vai ser idêntica a de um ReplicaSet. 

A versão apiVersion também vai ser apps/v1; 

vamos colocar o nosso kind, que vai ser um Deployment.

No nosso metadata vamos definir um name pra ele, que vamos chamar também de nginx-deployment.

Vamos colocar nossas especificações espec, que nós vimos que vai definir, inicialmente, o número de réplicas. 

Podemos colocar três, novamente, para exemplificar e vamos colocar as informações do nosso template, que vai ter um metadata, que serão as informações dos nossos Pods.

Vamos colocar um name: nginx-pod e as labels vamos colocar a chave app com um valor, também, de nginx-pod.

Nas especificações spec do nosso Pod vamos colocar as informações dos containers, que teremos um name: nginx-container e uma image que vamos colocar nginx-stable.

Por fim, só que é boa prática vamos colocar o nosso ports: containerPort: 80. E agora só falta o nosso seletor, que vai ter o nosso matchLabels, que tem que ser igual ao nosso labels do nosso metadata, então, app: nginx-pod. 

Nada de novo, a mesma declaração de um ReplicaSet, só trocamos em cima para Deployment.

```
apiVersion: apps/v1
kind: Deployment
metadata:
  name: nginx-deployment
spec:
  replicas: 3
  template:
    metadata:
      name: nginx-pod
      labels:
        app: nginx-pod
    spec:
      containers:
        - name: nginx-container
          image: nginx:stable
          ports:
            - containerPort: 80
  selector:
    matchLabels:
      app: nginx-pod
```

Se viermos na tela do Windows PowerShell e executar o comando 

kubectl apply –fe .\nginx-deployment.yaml

, ele foi criado. 

Se executarmos o comando 

kubectl getpods

, temos agora três Pods em execução, por causa deste Deployment.

Se dermos um 

kubectl get rs

, temos dois ReplicaSets. 

O nosso portal-noticias-replicaset e o nosso recém criado nginx-deployment-6bf9fcdcc7, mas, ele tem um ReplicaSet, porque, como vimos, temos uma super camada, um super conjunto, que é o Deployment e dentro de um Deployment nós criamos, automaticamente, um ReplicaSet que vai gerenciar os Pods.

E se formos um pouco mais além, temos o kubectl get deployments e temos o nosso Deployment criado, o nosso nginx-deployment, que tem os três Pods em execução, sem nenhum problema.

O que vai mudar na prática agora? 

#### a grande vantagem de usar um Deployment
A grande vantagem do uso de Deployments é que, assim como temos um git, por exemplo, para o nosso controle de versionamento de código, 
```diff
+ nós temos os Deployments em Kubernetes, que permitem o nosso controle de versionamento das nossas imagens e Pods.
```

O que muda agora? 

Conseguimos utilizar comandos extras para validar e verificar todo o nosso fluxo.

Então, por exemplo, podemos executar o comando 

#### kubectl rollout history deployment <deployment_name>

```
kubectl rollout history deployment nginx-deployment 
```

e ele nos mostra que temos uma revisão, a que estamos atualmente, um estado atual, e não temos nenhuma causa de mudança, porque ela é nossa primeira, não definimos nada para ela.

Mas, e se eu quiser mudar aquela versão stable para, por exemplo, a versão latest? 

O que pode acontecer? 

Eu posso, simplesmente, agora, executar o comando 

#### flag --record

kubectl apply-f nginx-deployment.yaml --record 

e o que vai acontecer? 

Ele vai configurar, vai alterar para nós, se eu der um 

kubectl get pod

, repara, recém-criados e cada um deles vai estar utilizando a versão latest.

Mas, se eu executar, de novo, o comando rollout history deployment xginx-deployment, o que vai acontecer? 

Ele tem, agora, a segunda revisão, a que estamos atualmente. 

E podemos alterar este CHANGE-CAUSE para ficar mais claro o que fizemos.

Ele está com esse comando kubectl.exe apply –filename=.\nginx-deployment.yaml –record=true, o que ele executou, mas, eu quero deixar mais claro o que foi feito.

#### kubectl annotate deploy ou kubectl annotate deployment

Então, para isso, nós temos o comando 

kubectl annotate deploy 

ou 

kubectl annotate deployment

, como você preferir, o nome do nosso Deployment que é nginx-deployment e aqui nós colocamos qual vai ser a nossa CHANGE-CAUSE, qual vai ser a nossa mudança?

Então, nós vamos definir através desse kubernetes.io/change-cause=”Definindo a imagem com versão latest, por exemplo, e ele vai anotar para nós.

kubectl annotate deployment <deploy_name> kubernetes.io/change-cause="<version change cause>"

```
kubectl annotate deployment nginx-deployment kubernetes.io/change-cause="Definindo a imagem com versao latest"
```

Se executarmos, novamente, o comando 

kubectl rollout history deployment xginx-deployment 

o que vai acontecer é que teremos a nossa primeira revisão, que foi a de criação, e a nossa segunda, que foi Definindo a imagem com versão latest.

E podemos ir além. 

Se eu quiser alterar mais uma vez, por exemplo, para a versão 1 do nginx o que vai acontecer? 

Vamos usar o comando 

kubectl apply –f .\nginx.deployment.yaml 

com nosso arquivo de definição com flag --record e o que vai acontecer?

Temos mais uma causa de mudança, mais uma revisão com o mesmo comando. 

Ele grava por padrão comando que foi executado para essa alteração.

E podemos, mais uma vez, alterar para ficar mais claro. 

Repetindo o mesmo comando de antes, do nosso annotate, ele vai alterar para nossa revisão atual, que é a três, que nós estamos, então 

kubectl annotate deployment nginx-deployment

, com nosso CHANGE-CAUSE sendo Definindo a imagem com versão 1.

se dermos agora um 

kubectl get pod

temos tudo em execução, sem nenhum mistério e se dermos um 

kubectl rollout history

mais uma vez, temos aqui todo nosso controle de versionamento. 

Tudo sendo feito, exatamente, da maneira que esperávamos.

Pra validarmos se tudo está da maneira que esperamos, vamos ao comando 

kubectl describe pod 

e eu vou descrever qualquer um dos nossos Pods do nginx-deployment, vou colar ele xginx-deployment-5c6d6c6479-9qfnd e podemos ver que nas nossas configurações de imagens, o que está acontecendo: ele está utilizando a versão 1, que foi o que definimos.

#### kubectl rollout undo deployment --to-revision=2

Mas, e se eu quiser voltar para alguma versão específica, fazer um rollback, alguma alteração no que já tenho, invés de eu ter que alterar manualmente no meu arquivo de definição, por exemplo.

O que eu consigo fazer aqui é, simplesmente, mais uma vez executando o comando de history, digamos que eu queira voltar para versão latest, eu consigo executar o comando 

kubectl rollout undo deployment 

e passando ou não do nosso Deployment que é nginx-deployment, eu consigo voltar para alguma revisão específica.

```
kubectl rollout undo deployment --to-revision=2
```

Então --to-revision=2 eu consigo voltar para versão dois e ele vai fazer tudo isso, magicamente, se eu usar o comando 

kubectl get pod

todos estão sendo criados e estão encerrando os anteriores e criando os novos, como, por exemplo, esse nginx-deployment-6c88c4c95c-b7k8g e se eu usar o comando 

kubectl describe pod

, este Pod utilizando a versão latest.

Então, quando utilizamos nossos Deployments, o que conseguimos fazer? 

```diff
+ Conseguimos, simplesmente, ter uma camada extra acima de um ReplicaSet, que consegue gerenciar as imagens, todo o versionamento do que estamos definindo, controle de atualização em cima das nossas imagens e Pods.
```

Então, no fim das contas, a boa prática, o mais comum que vocês irão ver quando vocês forem criar Pods é criar eles através de Deployments, que eles já vão permitir todo esse controle de versionamento e também os benefícios de um ReplicaSet.

Nada impede de criarmos manualmente, como viemos fazendo com Pods e ReplicaSets, mas, o mais comum, a boa prática, é fazer a criação através de Deployments, por conta desses benefícios de controle de versionamento e de estabilidade, disponibilidade da nossa aplicação.

### aplicando Deployments ao projeto
Já temos dois serviços que fazem o acesso ao nosso portal, nós vamos transformar ele num Deployment, nós temos um ReplicaSet, atualmente.

E vamos transformar o nosso simples Pod do sistema e do nosso banco de dados em Deployment pra termos, além da questão do reinício automático, em caso de falhas, também teremos a nossa questão do controle de versionamento, para tudo ficar sem nenhum problema, tudo padronizado, utilizando os melhores recursos possíveis para o nosso momento.

Então, bem fácil. 

Vamos colocar a mão na massa. 

O primeiro que iremos trabalhar em cima vai ser o nosso portal de notícias.

O primeiro passo vai ser remover o nosso Deployment do nginx, que foi só para exemplificar, então, 

kubectl delete ou podemos deletar pelo Deployment, eu vou fazer primeiro assim.

```
kubectl delete deployment nginx-deployment
```

Quero deletar o nosso nginx-deployment, ele vai deletar. 

Se usarmos o 

kubectl get pod

, vemos que ele está terminando cada um deles.

E, também, podemos deletar via arquivo, então usando o comando 

kubectl delete -f eu quero deletar o nosso portal-noticias-replicaset.yaml. Vai deletar da mesma maneira.

```
kubectl delete -f .\portal-noticias-replicaset.yaml
```

tudo sendo removido para ficarmos somente com nosso banco de dados e nosso sistema sem nenhum problema. 

Vou deixar um --watch no comando kubectl get pods para ficarmos acompanhando. 

Agora, a ideia vai ser criarmos nosso Deployment pro nosso portal. 

Já temos toda a estrutura do nosso ReplicaSet, então, basta virmos aqui, pegarmos o conteúdo todo do arquivo portal-noticias-replicaset.yaml.

Vamos criar um arquivo novo chamado portal-noticias-deployment.yaml, 

vamos apagar o do nosso ReplicaSet, 

eu copiei todo o conteúdo e vou colar dentro do nosso Deployment.

Vimos que a declaração toda é idêntica, aqui em cima só vou trocar para Deployment e vou colocar para o name dentro do metadata o -deployment. 

```
apiVersion: apps/v1
kind: Deployment
metadata:
  name: portal-noticias-deployment
spec:
  template:
    metadata:
      name: portal-noticias
      labels:
        app: portal-noticias
      spec:
        containers:
          - name: portal-noticias-container
            image: aluracursos/portal-noticias:1
            ports:
              - containerPort: 80
            envFrom:
              configMapRef:
                name: portal-configmap
  replicas: 3
  selector:
    matchLabels:
        app: portal-noticias
```

Nada de novo, tudo vai ser igual. 

Então, se viermos no comando 

kubectl apply -f e definir o nosso portal-noticias-deployment ele foi devidamente criado.

Então, usando o comando 

kubectl get pod

 no terminal e estão os três em execução.

Se eu usar 

kubectl rollout history

e colocar o nosso Deployment do nosso portal-noticias-deployment o que vai acontecer? 

Estaremos na nossa revisão 1, sem mudanças.

Vamos deixar aqui bem claro, então, vamos praticar um comando 

kubectl annotate deployment o nosso portal-noticias-deployment e vamos colocar o nosso kubernets.io/change-cause e definir para Criando portal de notícias na versão 1, pra praticarmos os comandos.

Se viermos na revisão, o nosso CHANGE-CAUSE todo definido, sem nenhum problema.

Agora, vamos fazer o seguinte. 

Temos o nosso 

kubectl get pod

e vamos fazer a mesma coisa para nosso sistema-noticias e para o nosso banco de dados db-noticias. 

Reparem que se viermos, mais uma vez, no nosso navegador, tudo está funcionando normalmente ao utilizar nosso Deployment, então, vamos fazer a mudança noticias-deployment.

E, por fim, o que nós vamos fazer? Vamos definir nossa especificação, que já vimos que vamos definir o número de réplicas para um, porque só queremos uma réplica do nosso sistema de notícias em execução. Vamos deixar nossa apresentação e nós criamos só uma réplica do nosso sistema de notícias e temos que definir, agora, o nosso template.

Porque vimos que se colarmos não dá certo e nós temos que definir as informações que nos são necessárias, porque vamos definir o nosso metadata que tem um name, vamos alinhar ele no metadata e temos também as nossas especificações espec alinhados com o mesmo.

Por fim, precisamos definir o nosso seletor com o nosso matchLabels e vamos colocar app: sistema-noticias, mais uma vez, frisando, igual ao labels.

```
apiVersion: apps/v1
kind: Deployment
metadata:
  name: sistema-noticias-deployment
spec:
  template:
    metadata:
      name: sistema-noticias
      labels:
        app: sistema-noticias
      spec:
        containers:
          - name: sistema-noticias-container
            image: aluracursos/sistema-noticias:1
            ports:
              - containerPort: 80
            envFrom:
              configMapRef:
                name: sistema-configmap
  replicas: 1
  selector:
    matchLabels:
        app: sistema-noticias
```

Salvamos e se viermos no PowerShell e usar o comando 

kubectl delete pod sistema-noticias

, vamos fazer o que de início: 

vamos deletar o Pod atual do nosso sistema de notícias e vamos recriar ele utilizando um Deployment, um comando 

kubectl apply -f 

e vamos passar o nosso arquivo.

Então, ele está terminando de deletar. kubectl apply -f e vamos colocar o nosso sistema-noticias-deployment, criado sem nenhum problema. 

kubeclt get pods, temos agora o nosso portal de notícias, o nosso sistema de notícias, falta agora fazermos o nosso banco de dados.

Eu vou criar o nosso db-noticias-deployment.yaml na lista de arquivos, pra praticarmos, mais uma vez, e vamos colocar a mesma coisa. 

Vamos copiar o conteúdo do arquivo db-noticias.yaml e dentro dele caber no nosso Deployment.

Vamos definir ´apiVersion: apps/v1´. O nosso kind é Deployment, nosso metadata, o name dele vai ser db-noticias-deployment.

E nas nossas especificações, repare que vou mostrar que não precisamos definir as réplicas, porque por padrão ele já vai definir como 1, então, vamos definir o nosso template e dentro do nosso template definimos tudo que já vimos, o nosso metadata dentro do template e as nossas especificações, também, dentro do nosso template

Por fim, só o nosso seletor que falta, então, selector, vamos colocar no nosso matchLabels e vamos colocar o nosso app: db-noticias. Salvamos e vamos, mais uma vez, dar um kubectl delete pod no nosso db-noticias. Ele vai ser deletado e vamos recriar ele, também, utilizando nosso Deployment.

```
apiVersion: apps/v1
kind: Deployment
metadata:
  name: db-noticias-deployment
spec:
  template:
    metadata:
      name: db-noticias
      labels:
        app: db-noticias
      spec:
        containers:
          - name: db-noticias-container
            image: aluracursos/mysql-db:1
            ports:
              - containerPort: 3306
            envFrom:
              configMapRef:
                name: db-configmap
  replicas: 1
  selector:
    matchLabels:
        app: db-noticias
```

Então, 

kubeclt apply –f db-noticias-deployment

, foi devidamente criado. 

Se dermos um kubectl get pods

, tudo devidamente funcionando.

Só para finalizar, assim como fizemos com o portal, 

kubectl annotate 

e vamos definir o nosso Deploy e vamos chamar qual deles queremos definir. 

Temos três, que é o nosso portal-noticias-deployment, db-noticias-deployment e o nosso sistema-noticias-deployment.

Então, vamos definir o nosso sistema-noticias-deployment, porque a nossa CHANGE-CAUSE, assim como fizemos com o nosso portal-noticias, então, kubernetes.io/change-cause e vamos colocar: Subindo o sistema na versão 1, só para tudo ficar padronizado.

Pronto, está aqui. 

Se dermos nosso comando kubectl rollout history deployment portal-noticias-deployment, mas, se trocarmos, invés de portal-noticias para sistema-noticias e está aqui subindo o sistema na versão 1.

Vamos finalizar fazendo a mesma coisa para o nosso banco, então, kubectl annotate deployment sistema-noticias-deployment kubernetes.io/change-cause=”Subindo o banco na versão 1” e não queremos alterar o nosso sistema-noticias-deployment e sim nosso db-noticias-deployment.

Então, colocamos db-noticias-deployment e ele vai anotar também. Se exibirmos o nosso db-noticias-deployment tudo está funcionando sem nenhum problema. 

E agora, temos todo esse controle, se caso alguma de nossas aplicações parem de funcionar, tudo vai voltar da maneira que estava.

Então, o que pode acontecer? Vamos voltar para o nosso portal e vamos entender o que aconteceu. 

Vou dar um "F5" e cadê as nossas notícias que tínhamos registrado aqui? 

Se eu vier no painel e fizer o login, cadê as notícias que eu cadastrei? É essa pergunta que temos agora para responder.

Então, sumiu tudo que fizemos porque os Pods por serem efêmeros eles não tem nenhum dado armazenado neles, porque eles estão prontos para serem armazenados, criados e destruídos.

Então, já temos a primeira pergunta: 

aonde foi parar as nossas notícias? 

Como podemos persistir os dados em caso de falhas? 

Precisamos ter alguma maneira de, caso um container dentro de um Pod reinicie ou o Pod todo reinicie, precisamos ter o acesso às informações que já estavam lá.

### o que aprendemos?
* a manter pods em execuçao com ReplicaSets e Deployments atraves de arquivos declarativos
* a fazer o controle de versionamento de Deployments com o kubectl
* como utilizar os comandos kubectl rollout para ver e alterar as versoes de Deployments
* que ReplicaSets sao criados automaticamente dentro de um Deployment
* que Pods normalmente sao criados atraves de deployments e nao individualmente

### Persistindo dados com volumes
Nós estamos enfrentando um problema de persistência de dados, porque, o que acabou de acontecer? 

Nós pegamos alguns arquivos das nossas notícias, colocamos dentro do nosso Pod, dentro do container desse Pod e quando este Pod é encerrado, todos os arquivos dele são perdidos.

Isso porque eles, ao serem executados nativamente, não tem nenhuma maneira, até então, de nós utilizarmos e persistir os dados de algum modo.

Porque nós sabemos que eles são efêmeros, eles devem estar prontos para serem trocados a qualquer momento e isso implica numa situação um pouco mais delicada.

Então, nós precisamos ver o que? 

Nós precisamos começar a estudar as questões da persistência de dados, primeiro no âmbito dos containers dentro de um Pod para que nós consigamos partir para conhecimentos mais aprofundados, que seria a persistência de dados no próprio Pod.

Então, o que acontece aqui? 

Nós já vimos lá do Docker que nós conseguimos compartilhar dados, arquivos de maneira geral entre containers.

O que acaba acontecendo? 

Nós precisamos de início, como eu acabei de falar para vocês, ter alguma maneira também do Kubernetes de compartilhar dados entre containers.

Mas, entre containers de um mesmo Pod. 

Nós precisamos estudar isso para entender a base e depois partir para o avançado.

E para isso nós temos os nossos recursos que são os Volumes, os PersistentVolumes, os PersistentVolumeClaim e os Storage Classes.

Nós vamos começar falando sobre os Volumes. 

#### Volumes
E qual é a peculiaridade deles? 

Bom, voltando ao nosso problema inicial, mais básico, nós temos um container ou alguns containers dentro de um Pod e queremos compartilhar um arquivo entre eles.

Se nós queremos compartilhar arquivos entre containers no Docker, nós fazemos o que? 

Nós criamos Volumes. 

No Kubernetes nós fazemos a mesma coisa, só que a peculiaridade dele é que o ciclo de vida é independente dos containers do Pod, mas é dependente do Pod.

```diff
+ Volumes possuem ciclos de vida independentes dos containers, porem, sao dependentes dos pods
```

Então, isso quer dizer que se nós vincularmos, colocar algum arquivo dentro desse Volume, dentro dos containers compartilhando esse Volume e algum desses containers dentro do Pod falhe, mas, o Pod ainda esteja em execução, esse Pod ainda existe.

E caso nós consigamos fazer o reinício manual desse container ou mantenha ele ainda em estado parado, mas tenha outros containers em execução, os arquivos ainda estão persistidos, por mais que este container tenha falhado.

Porque frisando, o ciclo de vida desse Volume é independente do container e sim dependente do Pod. 

```diff
- Isso quer dizer que se esse segundo container aqui falhar, ou seja, todos os containers desse Pod estão falhando, o Pod vai falhar, logo, o volume vai ser removido, porque o ciclo de vida dele é dependente do Pod.
```

Mas, o que vai acontecer com o arquivo? 

Bom, depende, se nós olharmos aqui na documentação oficial do Kubernetes, o que acontece? 

Nós conseguimos ver toda a questão dos Volumes e que os containers são efêmeros assim como os Pods e tudo mais.

E ele conta uma breve história sobre estes tipos de recursos, bem básico que é o básico que eu contei para vocês.

E mais aqui embaixo ele tem os tipos de Volumes, então, ele fala que o Kubernetes suporte diversos tipos, por exemplo, o awsElasticBlockStore, azureDisc, azureFile, vários.

##### hostpath
O que nós vamos usar para exemplificar a nossa utilização de Volumes é o hostPath, que é que nem o que vocês fizeram lá no curso de Docker.

```diff
+ Então, nós fazemos o bind de um diretório do nosso host para um diretório de dentro do nosso container do nosso Pod, nesse caso do Kubernetes.
```

E como que ele funciona? 

Se nós clicarmos no link do “hostPath” e ver, é exatamente dessa mesma maneira, o hostPath monta um caminho ou arquivo do nosso host e monta ele dentro do nosso Pod, dentro dos containers desse Pod.

E enquanto o Pod ficar vivo, esse Volume vai existir, e como é que nós fazemos a criação desse hostPath? 

É bem simples, como que nós criamos um volume básico no Kubernetes?

#### criar um volumen no kubernetes
Então, nós precisamos criar um arquivo de definição para ele. 

Vou criar um arquivo chamado pod-volume.yaml e dentro dele nós vamos definir um Pod mesmo para ser mais prática, mais simples a definição, funcionaria da mesma maneira para um ReplicaSet ou para um Deployment.

Vamos colocar aqui o kind que é um Pod e no metadata vamos definir um name para ele que vai ser o nosso pod-volume.

Nas especificações vamos colocar aqui as informações do container que nesse caso nós vamos fazer o que? 

Nós vamos ter o mesmo cenário da nossa apresentação. 

Vou encerrar a tela e colocar a animação da apresentação novamente para nós termos a ideia inicial.

Nós almejamos criar dois containers dentro de um Pod e um Volume para fazer o compartilhamento entre esses dois containers, é esse o nosso objetivo para entender a utilização de Volumes.

Então, vamos lá, como nós declaramos dois containers dentro de um Pod? 

É bem simples, basta seguir o que nós já viemos fazendo, nós definimos um nome para ele, vamos chamar ele de nginx-container, uma imagem, vou utilizar a versão nginx-latest.

E agora, repara que o nome containers já está até no plural, basta nós fazermos outra definição de nome e imagem. 

Esse traço no início da especificação name (- name) indica uma nova posição, como se fosse um array, uma nova posição nesse array para nós adicionarmos um novo campo.

Então, nós estamos adicionando aqui um novo campo, um novo container, por exemplo, vamos utilizar uma outra especificação bem famosa, por exemplo, o Jenkins. 

Vamos colocar o jenkins-container e utilizar a versão não latest, vamos utilizar uma versão mais leve, por exemplo, a alpine, irrelevante isso, mas só para nós definirmos aqui.

E agora, falta nós definirmos o nosso Volume, mas, como eu falei para vocês os Volumes tem ciclo de vida atrelado ao Pod, a especificação do Pod e não aos containers, então, faz todo sentido nós alinharmos com os containers a definição dos Volumes desse Pod.

Que é bem simples, basta nós definirmos um nome para ele, como por exemplo, primeiro-volume e definir qual é o tipo, o que nós queremos fazer? 

Nós queremos criar um hostPath e agora nós precisamos definir qual é o caminho dele no nosso host.

O caminho vai ser para /c/Users/Daniel/Desktop/primeiro-volume. 

Eu criei essa pasta na minha área de trabalho e ela vai ser o nosso Volume para nós.

E agora, a questão é bem simples, basta nós também falarmos que o tipo desse Volume é um diretório, sem nenhum mistério.

Só que falta algumas coisas ainda, como por exemplo, nós precisamos informar agora que cada um desses dois containers que nós definimos dentro do nosso Pod, vai montar esse Volume chamado primeiro-volume em algum lugar deles.

#### VolumeMounts
Então, dentro da definição de cada um desses containers, nós precisamos colocar aqui esse volumeMounts e dentro dele basta definir qual é o caminho dentro do nosso container. 

Pode ser, por exemplo, volume-dentro-do-container, sem nenhum mistério.

E qual é o Volume que nós queremos montar? 

É o primeiro volume, então, o nome do Volume que nós queremos montar é primeiro-volume, sem nenhum mistério.

E como nós queremos fazer isso para o nosso segundo container basta nós virmos no volumeMounts colar e tudo feito, sem nenhum mistério.

Por fim, basta vocês fazerem o seguinte, o pessoal que está no Windows comigo vai ter que fazer essa declaração como eu fiz para o caminho, não vai ser c:// vai ser no formato do Unix /C/Users/ o seu usuário/pasta que você quiser compartilhar.

Eu, no caso, coloquei essa aqui, /C/User/Daniel/Desktop/primeiro-volume. 

Aqui no Windows ainda vocês vão precisar fazer o seguinte.

Aqui vocês, dentro do Docker, das configurações do Docker que você podem abrir com settings, basta vocês fazerem o que? 

```diff
+ Vocês precisam desativar, caso esteja ativa essa opção de utilizar o WSL 2, vai precisar reiniciar o Docker, sem nenhum problema.
```

```diff
+ E depois em resources, basta vocês virem em “File Sharing” e marcar aqui no botão mais “+”, escolher, por exemplo, que nem eu fiz. 
+ A pasta C/Users/Daniel/Desktop/primeiro-volume, selecionar pasta e agora essa pasta vai estar compartilhável com o Docker. 
```

Sem nenhum mistério, tudo feito.

```
apiVersion: v1
kind: Pod
metadata:
  name: pod-volume
spec:
  containers:
    - name: nginx-container
      image: latest
      volumeMounts:
        - mountPath: /volume-dentro-do-container
          name: primeiro-volume
    - name: jenkins-container
      image: jenkins:alpine
      volumeMounts:
        - mountPath: /volume-dentro-do-container
          name: primeiro-volume
  volumes:
    - name: primeiro-volume
      hostPath:
        path: /c/users/daniel/desktop/primeiro-volume
        type: Directory
```

Com isso feito, basta nós virmos no PowerShell e aplicar esse arquivo, então kubectl apply -f pod volume.yaml.

E agora, ele foi criado sem nenhum mistério, se nós dermos um kubectl get pod agora, repara que nós temos aqui o nosso Pod com 2/2 em execução, sem nenhum problema.

Nós temos dois containers em execução e dois estão prontos já e basta nós virmos aqui e fazer o seguinte teste, eu quero executar um comando em modo interativo no meu Pod Volume, mas agora como eu tenho dois containers dentro desse Pod eu preciso explicitar se eu quero fazer isso no meu primeiro ou no meu segundo.

#### 2 conteiners dentro de um pod. como selecionar um - flag --container
E como é que eu faço isso? Só passando o nome. Então --container nginx-container, eu quero fazer o que? Eu quero executar o --bash, sem nenhum mistério.

```
kubectl exec -it <pod_name> --container <container_name> -- bash

kubectl exec -it pod-volume --container nginx-container -- bash
```

Se eu usar um ls, eu tenho o meu volume-dentro-do-container assim como eu defini no mouthPath dentro de VolumeMounts. 

E ele está mapeado para a minha área de trabalho nessa pasta primeiro-volume.

Se eu acessar essa pasta, então cd/volume-dentro-do-container, eu posso, por exemplo, criar um arquivo, um arquivo.txt. 

Isso significa que agora se eu vier na minha área de trabalho eu tenho o primeiro-volume e aqui está o arquivo que eu acabei de criar as 17:31.

Isso também significa que se eu vier aqui agora, sair desse meu container e acessar o meu jenkins-container com a mesma maneira, basta eu colocar o nome dele. O que vai acontecer? 

Eu também vou ter aqui o meu volume-dentro-do-container e posso, se eu vier aqui comandar um cd volume-dentro-do-container e acessar esse meu Volume se eu der um ls, aqui está o meu arquivo.txt.

Inclusive, eu posso criar outro arquivo, por exemplo, outroarquivo.txt e se eu vier mais uma vez na minha área de trabalho, eu tenho agora esses dois arquivos criados. 

Isso significa que esse Volume vai existir, se nós sairmos daqui, enquanto este meu Pod existir.

Como assim? Vamos executar o comando 

kubectl describe pod pod–volume, se nós dermos uma olhada aqui em cima, olha só a definição dele aqui do Volume, esse cara ele só vai existir essa definição só vai existir enquanto este Pod existir. 

Ele está vinculado diretamente ao nosso Pod.

Mas, como os arquivos já estão persistidos no nosso host, no caso aqui do hostPath, por mais que o Volume deixe de existir em algum momento, os arquivos vão continuar nessa pasta, o que vai ser encerrado é o vínculo.

Então, se eu remover agora este meu pod-volume, volume atrelado a este Pod, se nós voltarmos na nossa apresentação, como os dois containers que estavam em execução foram removidos, foram parados, o Pod também parou.

Logo, o Volume também foi removido, mas nesse caso, o arquivo, como nós fizemos esse mapeamento para a nossa área de trabalho aqui para um lugar persistente no nosso disco, os arquivos vão continuar aqui.

O que não continua é o Volume em si, se nós fizermos essa mesma declaração de novo, ele vai criar outro Volume para nós, mas que vai seguir a mesma ideia. E como os arquivos já vão existir, vai estar tudo ali sem nenhum problema.

### volumes no linux
```diff
- Atenção! A imagem do Jenkins no Docker Hub foi alterada! Agora para executá-la, você deve utilizar a imagem jenkins/jenkins:alpine e não a jenkins:alpine!
```

Eu estou no Linux agora para nós entendermos qual vai ser a diferença do Windows para o Linux nesse cenário do nosso terminal.

Nós temos já, se eu executar o kubectl get pods tudo da mesma maneira, só falta nós colocarmos o nosso primeiro Volume lá com o pod-volume.yaml para ser executado e nós fazermos o nosso teste.

Então, eu vou abrir o arquivo com o pod-volume.yaml e nós temos a mesma definição que eu fiz no Windows, mas, qual vai ser a diferença? 

É que no Windows nós temos o diretório c:// que nós definimos já no formato do Unix.

O que nós precisamos fazer aqui agora? 

Nós precisamos, a princípio, trocar para algum diretório que nós tenhamos no Linux, por exemplo, para /home/primeiro-volume e assim como nós fizemos no Windows, eu preciso aqui no Linux criar essa pasta.

A princípio, se eu vier no terminal agora e executar o comando kubectl apply -f pod-volume o que vai acontecer? 

Ele falou que foi criado, mas, se nós viermos e dermos um comando kubectl get pods ele está em criação.

O ponto é, vamos dar uma olhada para ver uma coisa mais específica na descrição da criação desse Pod, 

kubectl describe pod pod-volume. 

O que está acontecendo aqui? 

Ele deu um erro aqui embaixo, ele deu um warning e um problema de montagem.

O que aconteceu? 

Ele tentou fazer toda essa configuração para o nosso primeiro volume, mas ele falou que não encontrou com o hostPath, com /Home/primeiro-volume, ele falou que esse arquivo não é um diretório.

Mas, por que se ele está aqui, eu estou acessando ele agora? 

Porque, como eu falei para vocês, nesse cenário aqui do Linux nós estamos utilizando uma máquina virtual para criar e utilizar o nosso cluster que é o Minikube.

#### criar uma pasta dentro do minikube
Então, a grande questão é que nós precisamos criar dentro dessa máquina virtual, dentro do sistema operacional dessa máquina essa pasta chamada primeiro-volume dentro de home.

E como é que nós acessamos essa máquina virtual? 

#### minikube ssh

Com o comando 

```
minikube ssh
```

, e agora nós estamos dentro do Minikube.

Então, podemos acessar agora cd/home. 

Se nós dermos um ls, nós não temos a pasta primeiro-volume aqui, só a pasta docker, então, 

sudo mkdir 

e vamos criar a pasta primeiro-volume, vamos dar um "Enter".

```
sudo mkdir primeiro-volume
```

E agora, se nós sairmos com o "Control + D" de dentro do Minikube, vamos fazer o seguinte, vamos dar um 

kubectl delete –f 

no nosso pod-volume, e vamos recriar utilizando o mesmo arquivo.

Porque agora nós criamos a pasta e vamos ver o que vai acontecer.

Que ele vai deletar, sem nenhum mistério, e agora nós recriamos com o pod-volume.yaml.

Vamos dar um 

kubectl describe pod 

em cima desse pod-volume e a princípio ele inicializou tudo sem nenhum problema.

E nós conseguimos, inclusive, agora dar o nosso 

kubectl get pods 

e está aqui em execução os dois. Os dois containers dentro desse Pod, no caso.

#### DirectoryOrCreate
Mas será que eu preciso sempre acessar e criar manualmente, seja lá qual for o meu host, para criar o meu diretório?

Na verdade não, o que eu poderia ter feito aqui é o seguinte, vamos voltar, vou deletar mais uma vez o nosso pod-volume para nós entendermos o que vai acontecer agora.

Então, ele foi deletado e agora nós vamos fazer isso aqui, vamos acessar mais uma vez esse arquivo do nosso pod-volume e vamos fazer o seguinte experimento, eu vou colocar no path ao invés de primeiro-volume, eu vou chamar de segundo-volume.

E para manter aqui a coerência, eu vou trocar também para segundo, logo, vou ter que trocar aqui também dentro da definição dos meus containers.

E agora o que vai acontecer? Essa pasta não existe, mas, eu posso falar para o Kubernetes fazer o seguinte, se esse diretório não existir eu posso utilizar a criação, então DirectoryOrCreate, caso esse diretório não exista, ele vai ser criado automaticamente.

```
apiVersion: v1
kind: Pod
metadata:
  name: pod-volume
spec:
  containers:
    - name: nginx-container
      image: latest
      volumeMounts:
        - mountPath: /volume-dentro-do-container
          name: segundo-volume
    - name: jenkins-container
      image: jenkins/jenkins:alpine
      volumeMounts:
        - mountPath: /volume-dentro-do-container
          name: segundo-volume
  volumes:
    - name: segundo-volume
      hostPath:
        path: /c/users/daniel/desktop/segundo-volume
        type: DirectoryOrCreate

```

Então, kubectl apply –f e vamos executar aqui o nosso pod-volume.yaml e ele vai criar.

Se nós dermos um kubectl get pods aqui, ele vai estar em criação, se nós dermos um kubectl describe pods no nosso pod-volume e que vai acontecer? 

Ele já inicializou, então se nós viermos aqui agora em execução, sem nenhum problema.

E vamos conferir, vou acessar o nosso Minikube e vamos dar um cd/home e um ls, está aqui o nosso segundo volume criado de maneira dinâmica.

Então, vai funcionar da mesma maneira, os nossos testes, nós vamos conseguir fazer utilizando o kubectl exec –it no nosso pod-volume e também vamos falar aqui que nós queremos utilizar o nosso nginx-container executando o bash.

Dentro dele podemos acessar o nosso diretório volume dentro do container e criar algum arquivo aqui também qualquer.

Se nós voltarmos aqui agora ao nosso host e acessar o Minikube com ssh, dentro dele, cd/home e segundo-volume está aqui o nosso arquivo também criado.

Então, mesma maneira que vai funcionar, nós só precisamos nos atentar a essa questão da virtualização e também DirectoryOrCreate que nós podemos utilizar para fazer a criação do diretório de modo dinâmico.

Então, essa primeira parte que nós vimos de criar volumes para persistir dados entre containers, é isso que nós temos, o Volume, o recurso que o Kubernetes nos dispõe.

Mas, nós precisamos também ter maneiras mais específicas de compartilhar e conseguir persistir dados, através desses outros recursos que são um pouco mais complexos. 

Os PersistentVolumes, os PersistentVolumesClaims e os StorageClasses.

### Persistencia com PersistentVolumes
Como eu falei, agora nós vamos pausar o nosso projeto para que nós entendamos como funciona um PV, PVC num Cloud Provider, no caso aqui, do Google Cloud Platform.

#### criando um disco
Então, o que nós precisamos, de início, nós temos que criar inicialmente um disco, porque esse disco vai ser, assim como nós tivemos o nosso hostPath usando a nossa máquina, nós vamos criar um disco do Google Cloud Platform para armazenar esses dados efetivamente.

Então, de início, nós precisamos criar um disco de dados, no Google Cloud Platform para que depois nós pensemos em criar um PV e um PVC.

E como que nós criamos um disco no Google Cloud Platform? É bem simples.

Basta nós pesquisarmos nos recursos por Discos e acessar essa página do Google Platform que eu já tenho aberta, clicar no botão “Criar Disco” e ele vai pedir quais são as informações que nós queremos criar para nós definirmos esse disco.

Eu vou chamar ele, por exemplo, de pv-disk, escrevendo o nome dentro da aba “Nome” e a descrição é opcional. 

Eu preciso informar qual é o tipo de disco que eu estou criando, se ele é um HD padrão, se ele é um SSD, se ele é um híbrido, eu vou colocar o padrão porque nós não estamos nos preocupando com leitura e escrita.

A zona, eu vou definir como a mesma do meu cluster que é us-central1-c que foi o que eu coloquei no Clusters do Kubernetes.

E o tamanho do meu disco, que eu vou definir como 10Gigabytes, por fim, eu crio, clicando no botão “Criar” no final da página, sem nenhum mistério e ele vai criar esse disco para nós.

Então, agora o que nós temos? 

Nós já temos aqui o nosso disco onde nós vamos armazenar os nossos dados de maneira bem estável e nós precisamos criar um Persistent Volume que vai consumir desse disco para que nós consigamos persistir esses dados.

#### Criar um PersistentVolume
E como que eu crio esse Persistent Volume? 

É bem simples, eu vou utilizar o Visual Studio Code para nós editarmos e criarmos esse arquivo e eu vou chamar ele de pv.yaml.

E dentro dele nós vamos definir as informações desse Persistent Volume, que vai ser utilizando a apiVersion: v1, sem nenhuma novidade nesse ponto e o tipo do que nós vamos criar agora é um PersistentVolume.

No metadata nós vamos definir um name para ele que eu vou chamar de pv-1 e temos uma especificação, a mesma receita de sempre.

E agora eu preciso informar algumas coisas e como eu sei que coisas são essas? 

Se eu vier, novamente, na parte da documentação do Kubernetes falando sobre volumes.

Lembra que nós viemos aqui e vimos sobre os tipos de Volumes que existem? 

Nós utilizamos já o hostPath, o que nós estamos querendo utilizar agora é o gcePersistentDisc, que é o Google Cloud Engine Persistent Disc.

E ele mostra para nós todas as informações do que nós precisamos para criar um disco e um Persistent Volume para esse disco, olha que legal.

Então, nós precisamos definir qual vai ser a capacidade desse volume, quanto ele vai utilizar do disco, então, eu quero que ele utilize os 10 gigabytes.

Precisamos definir outras coisas, como por exemplo, qual é o modo de acesso a esse disco, a esse Volume aqui também? Então, eu preciso definir se eu quero que múltiplos Pods possam ler e escrever ao mesmo tempo nesse Volume, se apenas um Pod por vez tem a permissão de ler e escrever, ou, se múltiplos Pods podem ler apenas e uma vez só.

Eu vou colocar aqui ReadWriteOnce para que nós possamos escrever apenas um Pod por vez.

Depois eu preciso explicitar qual é o nome do disco que eu quero utilizar, então, eu vou colocar gcePersistentDisk e o nome dele que eu tenho aqui é pv-disk sem nenhuma novidade. Que é o que eu defini na listagem de discos.

E por fim, eu preciso definir também, como eu vou utilizar um PVC, eu preciso colocar qual é o StorageClassName que eu estou utilizando e eu vou chamar de standart.

```
apiVersion: v1
kind: PersistVolume
metadata:
  name: pv-1
spec:
  capacity:
    storage: 10Gi
  accessModes:
    - ReadWriteOnce
  gcePersistentDisk:
    pdName: pv-disk
  storageClassName: standard
```

Agora basta nós copiarmos esse trecho todo que eu escrevi no terminal e no Google Cloud Platform eu crio um arquivo chamado pv.yaml.

Eu colo ele e se eu executar agora o comando kubectl apply –f nesse meu pv, o que que vai acontecer? 

Ele vai criar esse cara aqui para nós, sem nenhum mistério.

#### kubectl get pv
Então, a partir desse momento se eu der um 

```
kubectl get pv 
```

ele vai listar para nós esse pv que eu acabei de criar, com o nome de pv-1 com esses 10 gigas de capacidade, ReadWriteOnce e esse RECLAIM POLICY está falando que, caso ele não tenha nada vinculado a ele, nenhum Claim desejando esse Persistent Volume, ele vai continuar existindo porque ele deve permanecer independente do que aconteça.

O status dele já está disponível e não temos um Claim ainda, precisamos resolver isso utilizando o nosso Storage Class Standard.

#### Criar um PersistentVolumeClaim
E como é que nós vamos fazer isso aqui agora? 

Basta nós fazermos também a criação de um PersistentVolumeClaim, com a mesma ideia, apiVersion: v1 e o tipo do que queremos criar é um PersistentVolumeClaim. 

E aqui no metadata vamos dar um nome para ele que vai pvc-1.

Nas especificações precisamos agora, vou dividir aqui a nossa tela, ter alguma maneira de falar que esta especificação do pv.yaml é acessado através deste pvc.yaml.

E como é que eu faço isso? Como é que ele vai fazer esse bind? Não vai ser através dos labels dessa vez, ele vai fazer isso através da definição de igualdade. 

Eles precisam ter o mesmo modo de acesso, eles precisam ter a mesma capacidade.

Eu venho no ReadWriteOnce, coloco os recursos que ele tem, dentro dele eu tenho que ele pede por um armazenamento de 10 gigas e com isso ele vai saber que eu estou utilizando esse pv.yaml, ou seja, essas informações batem na verdade.

Por fim, eu vou colocar no pvc.yaml também que eu estou utilizando o meu storageClassName do standard e ele vai fazer a mágica acontecer. 

Eu vou copiar essas especificações, venho no meu Google Cloud Platform, crio o meu pvc.yaml, colo aqui o trecho copiado e comando kubectl apply –f pvc.yaml que eu acabei de criar.

```
apiVersion: v1
kind: PersistentVolumeClaim
metadata:
  name: pvc-1
spec:
  accessModes:
    - ReadWriteOnde
  resources:
    requests:
      storage: 10Gi
  storageClassName: standard
```

Dou um "Enter" e olha o que ele vai fazer, ele criou o meu PVC. 

#### kubectl get pvc
Então, 

```
kubectl get pvc 
```

eu tenho ele recém criado, há 6 segundos, o meu pvc-1 com status de bound, ou seja, ele fez a ligação entre o PV e o PVC para este meu Volume, que é o pv-1 que nós definimos, com capacidade de 10 gigas, ReadWriteOnce com o standard como Storage Class criado há 6 segundos.

Então, agora nós precisamos fazer o que? 

Nós precisamos criar um Pod que vai acessar esse disco através do nosso PersistentVolume.

E como é que nós vamos criar esse Pod? 

Bem simples também, eu vou fechar essa divisão de tela do nosso terminal e vou criar o nosso pod-pv e vou definir as informações dele.

Mais uma vez, a apiVersion vai ser a v1, o tipo do que eu quero criar aqui é um Pod, sem nenhum mistério.

No metadata vamos colocar um nome para ele, eu vou chamar de pod-pv e nas especificações eu defino as informações do container, nesse caso vou colocar um só para ele, o nome vai ser nginx-container, ele vai utilizar a imagem do ngnix na versão latest.

E repara, se nós voltarmos aqui na definição do nosso pod-volume, o que nós fizemos? 

Nós definimos que ele monta um Volume.

A ideia aqui vai ser basicamente a mesma, eu preciso dentro do meu pod-pv montar um Volume, para, por exemplo, um diretório chamado /volume-dentro-do-container e eu vou chamar ele de primeiro-pv.

E como é que eu faço isso agora? 

É bem simples, basta assim como eu também fiz a declaração de um Volume no meu pod-volume aqui embaixo, eu vou fazer a mesma coisa.

Então, alinhado aqui com containers, mais uma vez eu vou definir um nome primeiro-pv, só que ele não é mais um hostPath. 

Eu vou falar que ele vai utilizar um persistentVolumeClaim.

E qual é o Persistent Volume Claim que eu quero utilizar? 

Eu preciso informar qual é o nome dele, então qual é o ClaimName dele? É o nosso pvc-1, que foi o que nós definimos no arquivo pvc.yaml, olha que simples.

```
apiVersion: v1
kind: Pod
metadata:
  name: pod-pv
spec:
  containers:
    - name: nginx-container
      image: nginx-latest
      volumeMounts:
        - mountPath: /volume-dentro-do-container
        name: primeiro-pv
  volumes:
    - name: primeiro-pv
      persistentVolumeClaim:
        claimName: pvc-1
```

Então, nós pegamos esse trecho todo do arquivo pod-pc.yaml, vem no nosso Google Cloud Platform e coloca o nosso cat > pod.yaml e define essas informações, colando o trecho copiado.

Agora, se eu dou um kubectl apply –f neste meu Pod, ele vai criar este Pod e se eu comandar kubectl get pods, se eu acessar ele para ver se está tudo ok, ele está criando, o que que ele vai fazer agora?

Ele vai terminar a criação, vamos dar aqui um kubectl describe pod pod-pv, ele fez toda a mágica e agora vocês dão um kubectl get pods. Está aqui ele em execução.

E agora se eu acessar ele com kubectl exec -it, vamos lá, eu quero acessar com o bash, vamos colocar pod-pv.

Isso significa que eu posso agora acessar essa minha pasta que é o meu volume-dentro-do-container e criar algum arquivo aqui, por exemplo, o meu arquivo-persistente.

E agora, por mais que este Pod deixe de existir, eu vou dar um kubectl delete –f neste arquivo que eu criei agora do meu Pod e vou deletar ele, o que vai acontecer? Se eu der um kubectl get pods não tenho mais Pod nenhum.

Mas, se eu recriar ele aqui agora usando kubectl apply –f pod.yaml vamos ver o que vai acontecer, criou, vou entrar nele em modo interativo mais uma vez, ele ainda está criando aqui, provavelmente, vamos tentar mais uma vez, fazer kubectl get pods, ele ainda está criando, vamos aguardar um pouco. Vamos ver, vai criar, pronto.

Agora, nós acessamos ele em modo interativo, demos um cd volume-dentro-do-container, se nós damos um ls está aqui o nosso arquivo persistente, mágica.

Então, agora nós temos uma maneira de persistir dados em um disco, no nosso caso no Google Cloud Platform, completamente independente do ciclo de vida do nosso Pod, porque através do Persistent Volume nós estamos guardando esses dados dentro desse disco e através do PVC nós estamos acessando esse Persistent Volume com um Pod.

### Para saber mais: Mais informaçoes sobre PersistentVolumes
Como dito, existem diversos tipos de plugins de volumes que podem ser utilizados pelos Cloud Providers, cada um com seu respectivo modo de acesso e nomes. Por exemplo, o GCEPersistentDisk que usamos nos vídeos anteriores, permite apenas a criação de um PersistentVolume em modo de ReadWriteOnce ou ReadOnlyMany. Diversas outras informações sobre plugins de volumes e modos de acesso podem ser conferidas nesse link da documentação oficial.

https://kubernetes.io/docs/concepts/storage/persistent-volumes/

### o que aprendemos?
* como criar volumes atraves de arquivos de definiçao
* volumes persistem dados de containers dentro de pods e permitem o compartilhamento de arquivo dentro dos pods
* que volumes possuem ciclo de vida independente dos containers, porem, vinculados aos pods
* como criar PersistentVolumes atraves de arquivos de definiçao
* PersistenVolumes persitem dados de pods como um todo
* PersistentVolumes possuem ciclo de vida independente de quaisquer outros recursos, inclusive pods
* como criar e para que servem os PersistentVolumeClaims
* que precisamos de um PersistentVolumeClaim para acessar um PersistentVolume

### Utilizando Storage Classes
Nós criamos manualmente um disco, criamos manualmente um PersistentVolume e um PersistentVolumeClaim, para que o Pod conseguisse persistir os dados de maneira estável, independentemente do ciclo de vida dele.

E o que que o Storage Class muda efetivamente? 

```diff
+ Ele muda no sentido de que agora nós vamos conseguir criar Volumes, Persistent Volumes, no caso, e discos dinamicamente.
```

Quando nós fizermos o bound de um Pod com o PVC utilizando agora um Storage Class e não diretamente um PV, nós vamos conseguir criar o disco e o Persistent Volume dinamicamente, conforme nós necessitamos.

Como nós vamos fazer isso? 

Primeiro, nós precisamos entender como o Storage Class é definido.

Na documentação do Kubernetes ele vai dar a mesma apresentação para vocês que eu falei sobre criar esses recursos de volumes dinamicamente.

Mas, se nós olharmos mais aqui embaixo, nos tipos que nós temos, nos provisionadores que nós temos, assim como em Volumes, nós temos aqui GCE Persistent Disk.

E ele mostra para nós toda a receita de como criar um Storage Class, então vamos pegar essa base e vamos colocar dentro do nosso arquivo que nós vamos criar para nós entendermos como tudo vai funcionar.

Então, eu vou criar um arquivo, chamado sc.yaml e dentro dele nós vamos definir: nós vamos criar um Storage Class chamado slow com tipo StorageClass, utilizando a versão da API, storage.k8s.io/v1.

O provisioner que nós temos que utilizar é kubernetes.io/gce-pd que é específico do Google Cloud Platform, então, em outros clouds providers vai ser diferente.

E os parâmetros que nós estamos utilizando? 

Nós estamos criando um disco standard que se nós formos olhar na documentação é o padrão.

Então, o type ou é o pd-standard ou o pd-ssd. Por padrão, se nós não definirmos, é o nosso standard.

Definimos a zona que, por padrão, ele também vai criar dinamicamente, mas ela já está até defasada, por isso que nós nem definimos.

E também, qual é o file system que nós queremos utilizar? 

Vamos utilizar o ext4, e o replication-type é caso nós queiramos replicar esse Storage Class através do nosso cluster.

Que por padrão, se nós nem colocarmos ele aqui, já é o none, nós não queremos lidar com replicação aqui.

A princípio, está meio abstrato ainda, mas vamos fazer o seguinte, nós estamos falando que nós queremos provisionar um disco no Google Cloud Engine Platform e queremos criar um disco do tipo standard padrão com o fstype: ext4. 

E o nome desse Storage Class é slow.

Então, vamos pegar esse trecho do comando, copiar e vamos voltar no nosso Google Cloud Platform que eu deletei os discos anteriores que nós criamos o nosso PV Disk e também não tenho mais nenhum PV, nem PVC, nem Pod, eu zerei aqui o nosso cluster.

Então, se nós criarmos esse arquivo agora, o nosso sc.yaml vamos colar dentro dele esse trecho copiado anteriormente. Usando o comando kubectl apply –f sc.yaml , ele criou o nosso Storage Class.

```
apiVersion: storage.k8s.io/v1
kind: StorageClass
metadata:
  name: slow
provisioner: kubernetes.io/gce-pd
parameters:
  type: pd-standard
  fstype: ext4
  replication-type: none
```

Se nós viermos aqui e der um 

```
kubectl get sc 
```

de Storage Class, nós temos aqui o padrão que já vem com o nosso cluster que é o default que nós não criamos, ele já vem manualmente, ele já vem por padrão.

E temos aqui o slow que nós acabamos de criar, que foi provisionado pelo mesmo cara do Google Cloud Platform há 7 segundos, como nós fizemos.

A grande questão é a seguinte: como nós podemos utilizar esse Storage Class para criar discos dinamicamente e Persistent Volumes, também, dinamicamente?

É bem simples, agora basta nós criarmos um PVC, então, eu vou criar um novo arquivo chamado, ou melhor, eu vou utilizar o mesmo que nós já utilizamos antes, o pvc.yaml, porque nós só estamos utilizando para editar.

Vou copiar esse arquivo e vou criar um novo chamado pvc-sc.yaml e dentro dele eu vou chamar ele de pvc-2. A questão do modo de acesso é o mesmo, os recursos que eu quero, por exemplo, 10 gigabytes, também eu quero 10 gigabytes, que seja criado dinamicamente.

E o StorageClassName que eu estou utilizando não é mais standard, eu defini, que eu estou utilizando uma definição 'slow'.

Então, nós temos o nosso arquivo ´pvc-sc.yaml temos também o nosso arquivosc.yaml, então, eu preciso definir noStorageClassNameque eu estou utilizando o slow`.

```
apiVersion: v1
kind: PersistentVolumeClaim
metadata:
  name: pvc-2
spec:
  accessModes:
    - ReadWriteOnde
  resources:
    requests:
      storage: 10Gi
  storageClassName: slow
```  

Vou pegar o comando todo, vou criar um arquivo no nosso Google Cloud Platform, ´pvc.yaml, e o que vai acontecer se eu executar o kubectl apply –f no nosso PVC, olha a mágica que acontece. 

Ele fez a criação e se eu der um kubectl get pvc temos o que nós criamos, que está com status de bound para o PVC.

Inclusive, se agora nós usarmos o comando 

kubectl get pv 

nós temos um PV que foi criado agora há 16 segundos com status de bound e vinculado ao nosso pvc-2, que é exatamente, se nós conferirmos aqui o nosso ID, o nosso nome, é igual ao que nós temos mais acima.

Com a capacidade de 10 gigas, ReadWriteOnce, sem nenhum mistério e ele já está com status de bound também.

Inclusive, se nós viermos no nosso disco e atualizar, repara que nós temos um disco recém criado de 10 gigabytes que é o nosso gke-cluster com todas as informações do nome que nós acabamos de definir.

Então, agora nós já criamos dinamicamente o nosso disco e o nosso PV. 

E agora, basta nós utilizarmos o nosso Pod para consumir esses dados utilizando um PVC, sem nenhum mistério.

Então, podemos, mais uma vez, criar um arquivo pod-sc.yaml e dentro dele nós vamos definir a apiVersion que vai ser a v1, kind é um Pod, no metadata vamos colocar o name para ele, então, name vai ser pod-sc.

E nas especificações vai ser bem parecido com o que nós já fizemos. 

Nós temos o nosso pod-pv, a grande diferença vai ser que nós vamos utilizar agora outro PVC, então, vamos colocar as nossas especificações. E nós não vamos utilizar o nosso pvc-1 e sim o pvc-2, que é o que nós criamos agora.

```
apiVersion: v1
kind: Pod
metadata:
  name: pod-sc
spec:
  containers: 
    - name: nginx-container
      image: nginx:latest
      volumeMounts: 
        - mountPath: /volume-dentro-do-container
          name: primeiro-pv
  volumes:
    - name: primeiro-pv
      persistentVolumeClaim: 
        claimName: pvc-2
```

Então, o nosso pvc-2 vamos utilizar ele no arquivo pod-sc.yaml e basta nós simplesmente copiarmos e executarmos ele dentro do nosso Google Cloud Platform.

Então, vamos colocar no nosso pod.yaml e usamos o comando kubectl apply –f pod-sc.yaml. E executamos.

E agora, nós temos o nosso Pod, que está vinculado a esse Volume criado dinamicamente através do nosso Storage Class.

Então, se agora nós colocarmos um --watch para aguardar a criação dele, o que vai acontecer? Assim como nós fizemos antes, os dados que nós persistirmos vão ser armazenados para sempre dentro desse disco até nós apagarmos esse disco ou remover o volume manualmente.

Então, se nós viermos aqui e executar o comando kubectl exec –it pod-sc -- bash, nós conseguimos, também, dar um ls e acessar o nosso volume dentro do container.

Se nós dermos um ls está aqui só o lost found por padrão, que já vem do próprio ext4 e podemos criar uma pasta ou até mesmo um arquivo chamado arquivo-sc.txt.

Vou sair, vou remover esse Pod, para nós removermos ele e recriar e nós vamos ver que tudo continua funcionando da mesma maneira.

Só que agora nós definimos só um arquivo, que foi o nosso Storage Class e o PVC para nós acessarmos esses recursos criados dinamicamente.

Então, agora se nós viermos no Google Cloud Platform e executar mais uma vez, ele ainda está em criação, provavelmente. 

Se nós entrarmos nele mais uma vez, vamos acompanhar aqui com o watch, assim que ele criar esse Pod e nós acessarmos ele nós vamos ver que todos os dados vão continuar persistidos ali, mesmo que dinamicamente.

Isso é muito bom, porque isso significa que agora nós, através de um simples arquivo de definição, que é todo o nosso propósito que nós viemos fazendo até então, nós conseguimos criar e definir dinamicamente Discos e Volumes dentro do nosso cluster de maneira extremamente simples, só definindo o tipo e o file system. Fazendo o bind com um Persistent Volume.

E agora, se nós viermos aqui e tentar acessar novamente...vamos ver se ele criou, vamos executar. Acho que eu acabei não criando de novo, por isso que estava demorando tanto.

Vamos criar ele, agora sim. Se nós acompanharmos, ele vai criar e o nosso arquivo –sc que nós criamos, ainda vai estar lá.

E enquanto ele cria, eu vou mostrar aqui para vocês, também, a questão que basta olhar na documentação que vocês vão ver que existem diversas outras, como, por exemplo, NFS, RBD, VsphereVolume, PortworxVolume, vários outros que nós podemos utilizar, inclusive o próprio Local.

Então, agora que ele criou vamos acessar, mais uma vez, dentro do nosso Pod e temos o nosso Volume. 

Comandando cd volume-dentro-do-container ls está aqui o nosso arquivo-sc.txt.

Então, se agora, eu deletar os nossos Pods, vou deletar todos que estão aqui em execução, deletar também os nossos PersistentsVolumesClaim e os nossos SC, o que vai acontecer?

Vamos lá, delete pvc --all e também delete sc --all, o que vai acontecer? 

Vou clicar no botão "F5" aqui nos Discos e não temos mais os Discos, ele também é removido dinamicamente, assim como os nossos Persistent Volumes que foram criados.

Então, se nós dermos um get pv, nós vamos ver que o Persistent Volume não existe mais.

Então, graças ao Storage Class nós conseguimos também criar recursos dinamicamente conforme demanda do nosso cluster e isso é muito legal. 

### Conhecendo StatefulSets
Agora que nós já sabemos sobre Volumes, Persistent Volumes, Persistent Volumes Claims e Storage Classes, nós temos a capacidade de resolver aquele primeiro problema que nós vimos de maneira muito mais fácil. Agora que nós temos o conhecimento, botar na prática vai ficar muito mais simples.

E qual era o nosso problema inicial? 

Nós temos um Deployment do nosso sistema de notícias, mas quando o Pod desse sistema falha, o Deployment, através do ReplicaSet, vai fazer ele ser recriado.

Mas, os arquivos são perdidos, então, nós precisamos ter alguma maneira que, por mais que o Pod seja reiniciado, o arquivo seja persistido.

E nós vimos agora, uma maneira de fazermos isso acontecer, e nós temos um recurso, que é o PersistentVolume, que possui um ciclo de vida independente do nosso Pod e vai persistir os dados por mais que o Pod venha a falhar.

#### StatefulSet
Mas, o Kubernetes ainda facilita mais para nós, ele possui um recurso chamado StatefulSet e 

```diff
+ ele funciona de maneira bem similar a um Deployment, mas, ele é voltado para aplicações a Pods que devem manter o seu estado que eles são Stateful.
```

Isso significa que quando um Pod reinicia ou falha por algum motivo dentro de um StatefulSet e volta a execução, o arquivo é mantido porque ele vai fazer a mágica acontecer.

Mas, essa mágica acontecer nada mais é do que quando nós criarmos um Pod dentro de um Stateful Set, nós também temos que definir que ele vai ter um PersistentVolumeClaim para acessar um PersistentVolume.

E isso vai ser para cada Pod dentro de um Stateful Set, a diferença é que nós vamos fazer isso de uma maneira um pouco mais rápida, um pouco mais enxuta. 

Mas, nós vamos entender isso na prática.

E o que isso quer dizer? 

Que por mais que nós possamos ter diversos Pods dentro de um Stateful Set, cada um deles ganha uma identificação única, ordinal.

E caso, por exemplo, o nosso primeiro Pod aqui falhe, vai ser criado um novo Pod para cima dele, para substituir a ausência dele.

Mas, ele vai usar a mesma identificação para o Stateful Set, então, ele vai ser tratado como o mesmo Pod.

Então, ele vai ter acesso ao mesmo PersistentVolumeClaim que vai dar acesso à ele as informações do nosso PersistentVolume. 

 E como isso funciona na prática, vamos entender agora.

Eu vou abrir o nosso Visual Studio Code e, de início, eu vou fazer aquela pequena limpeza nas pastas da lista, tirando o nosso db-noticias, o nosso db-noticias-deployment. Vamos manter só o que nós temos em execução para a nossa visualização ficar mais enxuta.

Vou apagar tudo o que não diz respeito ao nosso projeto, agora vou apagar o nosso portal-noticias. O nosso portal-noticias-deployment fica, para tudo ficar devidamente organizado.

Eu vou tirar o nosso sistema-noticias, os nossos serviços ficam. Pronto, agora nós temos uma visão mais enxuta do que realmente precisamos.

O que nós precisamos de início? Nós precisamos, nos baseando no nosso sistema-noticias-deployment, criar um Stateful Set.

#### Criar um StetefulSet
Então, eu vou criar um novo arquivo chamado sistema-noticias-statefulset.yaml e vamos definir ele aqui agora.

A apiVersion do nosso Stateful Set, assim como o ReplicaSet e o Deployment, está em apps/v1 e o tipo do que nós queremos criar é um StatefulSet.

Vamos definir um metadata para ele, que eu vou chamar de sistema-noticias-statefulset e agora as especificações spec.

Vamos colocar uma réplica e vamos definir aqui agora as nossas informações de template assim como nós temos num Deployment e vamos colocar um metadata também, que são as informações agora do Pod que vai ser criado dentro desse StatefulSet.

Vamos definir a label e vamos colocar aqui um nome de sistema-noticiais. 

Vamos definir também um name como nós fizemos aqui e vamos chamar ele de sistema-noticias com o mesmo padrão, então name: sistema-noticias.

Agora, definimos aqui o nosso metadata e vamos definir as especificações spec desse Pod, em que nós vamos definir os containers.

O que que tem dentro desses containers? 

Vamos colocar um nome para ele, eu vou chamar da mesma forma que nós chamamos aqui no nosso Deployment, então vamos colocar aqui todas as mesmas informações, pronto. E agora basta o que? A princípio, nós salvarmos esse arquivo e rodar.

Na verdade, ainda faltam algumas coisas, além é claro, você deve estar se perguntando: Daniel, cadê o seletor? 

Realmente, eu ainda vou colocar, mas o ponto não é nem esse, falta nós definirmos outras coisas ainda, além do seletor que nós definimos aqui para o nosso sistema-noticias, no StatefulSet precisa definir outras informações.

Como, por exemplo, qual é o nome do serviço que vai gerenciar esse StatefulSet, então, por mais que nós tenhamos aqui o label para os nossos Pods que estão dentro desse StatefulSet, nós precisamos explicitar o nome do serviço que nós queremos utilizar para gerenciar essa StatefulSet, que nada mais é do que svc-sistema-noticias.

```
apiVersion: apps/v1
kind: StatefulSet
metadata:
  name: sistema-noticias-statefulset
spec:
  replicas: 1
  template: 
    metadata: 
      labels:
        app: sistema-noticias
      name: sistema-noticias
    spec: 
      containers:
        - name: sistema-noticias-container
          image: aluracursos/sistema-noticias:1
          ports:
            - containerPort: 80
          envFrom:
            - configMapRef:
              name: sistema-configmap
  selector:
    matchLabels:
      app: sistema-noticias
  serviceName: svc-sistema-noticias
```

Então, se eu salvar esse arquivo, o que deve acontecer? 

Eu vou no nosso PowerShell e vou dar um kubectl apply -f no nosso sistema-noticas-statefulset.yaml, ele foi criado, perfeito.

Mas, vamos dar um kubectl get pods para nós entendermos. 

Agora nós temos o nosso Pod do Stateful Set e temos também o Pod do nosso Deployment.

E como nós queremos trabalhar em cima de um StatefulSet e não de um Deployment podemos, inclusive, remover o nosso Deployment.

Então, kubectl get deployments e kubectl delete deployments e colocamos aqui no nosso sistema-noticias-deployment para ele ser removido.

Agora, como nós estamos fazendo a seleção a partir do nosso serviço, tudo deve estar funcionando de maneira externa sem nenhuma diferença, então, se eu acessar a nossa aplicação, vamos fazer o login. Tudo parece estar funcionando, vou cadastrar uma notícia com um conteúdo.

E vou colocar imagem da Alura mais uma vez, e clicar no botão “Salvar” dentro da janela de seleção. Se eu der um "F5" está aqui.

Mas, vamos testar agora, fazer a prova real, eu vou dar um kubectl delete pod e vou deletar o Pod que foi criado para o nosso sistema de notícias no Stateful Set.

Nós vamos ver que ele vai ser recriado, então, podemos acompanhar que ele está sendo removido e vai ser recriado a partir desse momento. Foi, então, kubectl get pods está aqui, criado há 4 segundos.

Então quando eu clicar "F5" a ideia é que nós tenhamos ainda a imagem. Vamos ver, e sumiu, por que será?

Vamos tentar entender o que aconteceu aqui, vou dar um clear aqui no nosso terminal e vou dar um kubectl get pv de PersistentVolume, porque como eu falei para vocês, para cada Pod dentro do nosso Stateful Set, nós temos que ter um Persistent Volume Claim e um PV.

Então, vamos ver, eu tenho algum PV aqui? 

Não tenho, e um Persistent Volume Claim, será que eu tenho? Também não.

Então, é esse o problema. 

Apesar do nosso Stateful Set estar cadastrado, feito aqui da maneira certa, nós não definimos para ele um Persistent Volume Claim e um Persistent Volume.

Mas, vocês vão ver que nós vamos resolver isso de uma maneira bem mais elegante através do nosso Storage Class.

### utilizando um StatefulSet
[00:00] O que aconteceu? Além de nós termos perdido as nossas imagens, nós também perdemos a nossa sessão. Quando nós tentamos acessar a aplicação novamente ele pede para nós nos autenticarmos.

[00:13] Então, nós precisamos ter duas maneiras de persistir, uma as nossas imagens e outra a nossa sessão.

[00:21] E se nós olharmos aqui mais uma vez na nossa apresentação, isso significa que nós precisamos criar um Persistent Volume Claim para um Persistent Volume que vai armazenar as nossas imagens e um Persistent Volume Claim que vai permitir o acesso com Persistent Volume que vai armazenar a nossa sessão.

[00:38] Então, vamos lá e vamos criar esses Persistent Volume Claim, clicando no botão “New File”, no canto superior esquerdo. Eu vou chamar o primeiro de imagem-pvc.yaml e dentro dele nós vamos definir o que nós já sabemos, a versão da api vai ser a v1, o tipo do que nós queremos criar é um PersistentVolumeClaim.

[01:01] E precisamos colocar, também, o nosso metadata, que vamos colocar um nome chamado imagens-pvc. Nas especificações dele vamos colocar o modo de acesso onde vamos definir como ReadWriteOnce, para um acesso por vez.

[01:21] E em resources nós vamos definir o que? O quanto nós pedimos de acesso, de armazenamento. Eu quero colocar, por exemplo, 1 giga.

[01:35] Temos a definição do nosso imagens-pvc e precisamos agora criar um arquivo para a nossa sessão.

[01:41] Vou chamar sessao-pvc.yaml e só vou trocar o nome do metadata de imagens-pvc para sessão-pvc. A ideia do resto é a mesma coisa, ReadWriteOnce com um armazenamento de 1 gigabyte.

[01:56] Agora eu já tenho os meus dois Persistent Volume Claim, e preciso utilizá-los no meu Pod para que os meus containers, aqui no caso o meu único container, tenha acesso a este Volume que nós vamos utilizar.

[02:09] E nós já sabemos fazer isso, alinhado aqui com o nosso envFrom, nós vamos falar que o nosso container vai montar um Volume que vai se chamar, no caso, eu vou dar o nome quando nós declararmos ele de imagens e o caminho que nós queremos montar dentro do nosso container vai ser para o caminho que ele tem as nossas imagens.

[02:32] Que nós vimos que é /var/www/html/uploads que nós vimos dentro do nosso exec.

[02:42] Então, eu vou até colocar no Powershell o nosso exec mais uma vez e nós temos nele o nosso uploads que é a pasta que nós temos as nossas imagens.

[02:52] E agora nós precisamos fazer a mesma coisa para sessão, então vamos criar, montar um outro Volume que vai ser para a sessão e ele vai estar em /tmp como nós vimos em uploads.

[03:05] Então cd/tnt vai ser armazenado na nossa sessão.

[03:11] Falamos que o nosso container quer montar esses dois Volumes dentro dele, mas nós precisamos definir esses Volumes, como nós vimos. Alinhado com os nossos containers nós precisamos definir, nas especificações desse Pod, que ele vai ter esse Volume.

[03:31] Um deles nós já sabemos o nome que é imagens e ele vai utilizar um Persistent Volume Claim para ele poder acessar este Volume e o nome dele, o nome deste Claim é o nosso imagens-pvc.

[03:50] A mesma coisa vai acontecer para a nossa sessão, então, vamos ter um Volume chamado sessão, o nosso Persistent Volume Claim e o Persistent Volume Claim dele é sessao-pvc.

[04:04] Então, salvamos isso e a ideia agora é a seguinte, nós precisamos criar este Persistent Volume Claim para que nós possamos criar o nosso Stateful Set. Então, vamos lá.

[04:17] Vou abrir o nosso terminal do Powershell, mais uma vez, e vou aplicar e vou criar esses dois Persistent Volume Claim, o nosso imagens-pvc e o nosso sessao-pvc.

[04:31] Então, se nós voltarmos na nossa apresentação, mais uma vez, o que nós temos já? Nós já temos o nosso Persistent Volume Claim e o nosso Pod. Falta o nosso Persistent Volume.

[04:43] Mas, vamos dar uma olhada no Powershell. Eu tenho um comando para isso, kubectl get pvc o que ele está falando? Vamos lembrar, ele está falando que eu tenho esses dois PVC, que eu realmente criei, mas, o que é mais importante além dele bater com as configurações que eu defini aqui é que ele já está com status de bound, ele já fez ligação com algum volume.

[05:07] E ele tem o nome desse Volume, inclusive. Então, vamos comandar um kubectl get pv. Repara, ele criou dois Volumes, automaticamente, para nós.

[05:18] E como que ele fez isso? Exatamente, nós temos por padrão um Storage Class, o nosso cluster, assim como nós tínhamos lá no Google Cloud Platform, nosso cluster possui também um Storage Class padrão, que é um default aqui.

[05:34] Então, se nós criarmos um Persistent Volume Claim sem definir qual volume nós queremos utilizar, ele vai utilizar o Storage Class para criar, dinamicamente, o nosso Persistent Volume.

[05:47] Então, olha que mágica, nós não precisamos nem nos preocupar nesse cenário em criar o nosso Persistent Volume manualmente, porque o próprio Storage Class está fazendo isso para nós.

[05:57] Isso, por si só, já é um grande adianto. Não é à toa que nós temos agora, graças ao dinamismo do Storage Class, a criação desses Volumes em demanda, conforme nós vamos tendo novos Persistent Volume Claim, ele vai criando novos Persistent Volumes para nós.

[06:15] Isso é fantástico. Agora, finalmente, nós podemos aplicar o nosso sistema-noticias-statefulset.yaml, mas antes nós precisamos remover ele, porque ele já está em execução. Então, vamos remover ele e vamos aplicar apply, novamente.

[06:33] O que vai acontecer aqui? Ele foi criado e agora se nós voltarmos na nossa aplicação, vamos, mais uma vez, entrar no Portal de Notícias do site, digitar admin na aba “Usuário” e admin na aba “Senha”. Temos a nossa notícia anterior ainda, que nós tínhamos sem imagem quebrada. Vamos excluir ela e vamos cadastrar uma nova notícia, clicando no botão “Nova Notícia”.

[06:52] Vamos digitar ‘Uma notícia’ na aba “Título” e digitar ‘Um conteúdo’ na aba “Notícia”, mais uma vez, adicionando a imagem da Alura, clicando no botão “Escolher Arquivo”. Vou salvar, clicando no botão “Salvar” no canto inferior direito da janela. Se eu der um "F5", a princípio, tudo funcionando.

[07:04] Vou criar uma nova notícia, vou chamar de ‘Outra notícia’, na aba “Título”, com “Outro conteúdo”, na aba “Notícia” e vou colocar agora a imagem da Caelum e vou salvar também. Se eu der um "F5" tudo, a princípio, funcionando.

[07:21] Agora, vamos fazer a real prova. Eu vou executar o comando kubectl get pods e vou dar um kubectl delete no nosso Pod do sistema-noticias-statefulset-0. E ele foi deletado.

[07:42] Se nós acompanharmos, através de um outro aqui, que na verdade ele já até deletou, não precisamos acompanhar. Nós vamos dar um kubectl get pod mais uma vez, ele está criando.

[07:51] Então, vamos lá, "kubectl get pod --watch" ele está criando e criou, pronto, foi bem rápido de novo.

[07:58] Se nós dermos um "F5", estão as nossas notícias e as imagens. Se nós viermos aqui de novo e acessar o mesmo link, a nossa sessão foi persistida.

[08:09] Então, tudo continua funcionando da mesma maneira. Se nós voltarmos no nosso terminal e agora vou dar uma olhada mais específica, vou dar um kubectl describe pod e vamos descrever o nosso describe pod sistema-noticias-statefulset-0.

[08:29] E o que nós temos, primeiro ele deu todo o problema para montar, mas, ele conseguiu montar depois sem nenhum problema e logo depois o que aconteceu? Ele fez o mapeamento para esse Volume usando o Persistent Volume Claim que nós definimos e não é ReadOnly. Todas as informações que nós definimos a mesma coisa para a nossa sessão.

[08:55] Então, tudo funciona, todo o bind foi feito e agora nós temos a questão da persistência ao nosso lado, nós conseguimos salvar essas informações, por mais que o nosso Pod venha a falhar. Isso é muito legal.

[09:09] Para essa parte de Volumes e persistência de dados, nós paramos por aqui e eu vejo vocês no próximo vídeo, na próxima aula, onde nós vamos falar sobre um novo conteúdo e eu vejo vocês lá. Até mais!

### o que aprendemos?
* como criar PersistentVolumes dinamicamente com StorageClasses
* StorageClasses tambem sao capazes de criar discos de armazenamento
* o que é um StetefulSet
* como utilizar StatefulSets para garantir uniciadade de pods durante reinicios e atualizaçoes
* clusters possuem StorageClasses 'default' e podem ser usados automaticamente se nao definirmos qual será utilizado

### conhecendo probes
[00:00] Agora vamos falar de um tópico bem importante, mas, que ao mesmo tempo, vai ser bem fácil de entendermos e colocar a mão na massa. E, a questão agora é a seguinte: nós temos uma requisição que pode chegar para esse serviço e ele, nós sabemos, vai fazer o balanceamento de carga entre os três Pods que temos.

[00:20] Vai chegar a requisição pro container dentro desse Pod, ele vai fazer algum processamento e vai exibir o resultado, seja uma página web, seja o retorno de alguma API, o que seja, tanto faz.

[00:31] E ele retorna o Status Code, por exemplo, de 200, que a requisição foi ok ou algum de 300 que seja um redirecionamento, qualquer coisa do tipo. Mas, o que importa é que o SVC pode balancear a carga entre qualquer um destes Pods.

[00:49] O que podemos acabar vendo acontecer? Em algum momento este Status Code recebido tem a possibilidade de ser um erro 500 ou algum erro de 404, de Not Found um erro interno no servidor de 500 e isso significa que a aplicação dentro deste Pod não está respondendo de maneira esperada. Ela não está funcionando da maneira que esperávamos.

[01:19] Mas, a pergunta que fica é: o Kubernetes sabe que o Pod está em funcionamento, mas, a aplicação dentro deste Pod não tem como saber, a princípio, se ele deve reiniciá-la ou não. Então, apesar do Pod estar saudável e funcionando, a aplicação dentro do container deste Pod não está respondendo da maneira esperada.

[01:42] Como assim? Vamos visualizar o caso do nosso portal de notícias. Eu vou abrir a abra do console do navegador e se eu recarregar a página vemos, por exemplo, que quando fazemos uma requisição para localhost 30 mil, recebemos um código de status 200, ou seja, a requisição foi ok.

[02:01] Tivemos tudo sem nenhum problema, mas, pode ser que se tivermos algum código de 400 pra cima e ali na faixa dos 500 também, essa aplicação não esteja respondendo da maneira esperada. Porque, ou nós tomamos um erro de Not Found ou um erro interno ou um Bad Request, qualquer outra coisa do tipo.

[02:21] E para resolver este tipo de problema, nós temos os Configure Liveness, Readiness e Startup Probes. Vamos falar sobre cada um deles, mas, nós vamos começar falando sobre o Liveness Probes, que é nada mais do que uma prova de vida que a aplicação dentro de um container de um Pod está funcionando.

[02:40] Então, o kubelet vai usar um Liveness Probe como um critério para saber quando reiniciar o container de um Pod. Então, quando cair em algum deadlock ou a aplicação está rodando, mas, incapaz de manter progresso. Os cenários que exibimos aqui, por exemplo.

[02:55] E, nesse cenário , o que podemos fazer, o que podemos visualizar? O kubelet, que é aquele componente que mostrei pra vocês lá dos nossos nodes, eles são responsáveis por, através do nosso Liveness Probe, saber se a aplicação deve ser reiniciada ou não.

[03:15] Então, como que podemos informar ao kubelet utilizando os Liveness Probe, que essa aplicação deve ser retornada caso ela não tenha nenhum status favorável http.

[03:26] Ele tem um pequeno guia para nós, mas, reparem que não precisamos declarar um arquivo só para o Liveness Probe. Dentro dele, da definição do nosso container, podemos definir qual é a prova de vida, como garantimos que este container dentro do nosso Pod está vivo.

[03:44] Então, são essas perguntas que precisamos responder. No próximo vídeo vamos colocar a mão na massa e criar o nosso primeiro Liveness Probe, pra sabermos quando o nosso Pod já está pronto com o container dentro dele para ser reiniciado em caso de falhas.

[04:01] Então, por esse vídeo é só, vamos parar por aqui, e no próximo começamos a pôr a mão na massa e eu vejo vocês lá. Até mais!

### utilizando Liveness Probes
[00:00] Pessoal, então, vamos colocar o nosso Liveness Probe. Qual vai ser o critério para considerarmos o container do nosso Pod do portal-noticias como saudável. É bem simples.

[00:12] Vamos definir um Liveness Probe e o que precisamos para definir? Eu vou definir que vamos fazer uma requisição utilizando o verbo get para um caminho em uma determinada porta.

[00:27] Qual é a porta que eu quero fazer o meu teste? Em que porta está sendo executado o meu portal de notícias? Na porta 30 mil? Na verdade, não. Porque como eu estou fazendo o teste no escopo do container, eu preciso colocar em que porta o meu container está executando essa aplicação e nós sabemos que ele está fazendo isso na porta 80.

[00:53] Então, dentro deste cenário, nós estamos fazendo o teste dentro do Pod que está executando o container e sua aplicação na porta 80. E qual é o caminho? Por exemplo, temos o nosso localhost:3000, nós temos, também, o nosso sistema de noticias com o nosso localhost:30001/inserir_noticias.php, então, nesse caso, se quiséssemos testar essa rota, nós definiríamos este caminho.

[01:23] Mas, como estamos testando o nosso portal de notícias, simplesmente, vamos colocar o nosso localhost:30000 e como não temos um caminho auxiliar a esse, nós temos só o nosso principal, que é o localhost:30000, sem nada depois da barra, o nosso caminho nada mais é, simplesmente, do que barra.

[01:46] E, agora, nós precisamos definir, também, o seguinte: de quanto em quanto tempo eu quero fazer este teste? Então, a cada quantos segundos eu quero executar esse teste? A cada 10 segundos eu quero fazer a validação deste container.

[02:02] E qual é o número máximo de falhas que eu tolero para este teste antes dele executar o reinício do container. Então, qual é o meu Threshold o que eu tenho de limite para isso? Eu vou definir como três falhas sendo o número máximo, antes dele executar o reinício desse meu container.

[02:22] E, por fim, o que eu preciso definir também? Eu preciso informar a partir de qual momento ele vai começar a executar esses testes, porque o container subiu, mas, não necessariamente ele já está pronto para receber esses testes. Então, eu vou definir um atraso inicial de, por exemplo, 20 segundos antes dele começar a executar o primeiro teste.

[02:48] Então, o container vai subir depois de 20 segundos ele vai começar a executar este teste a cada 10 segundos. Mas, a pergunta que temos nesse momento é como que podemos definir qual é o nosso critério? Porque estamos fazendo um get na porta 80, mas, o que ele vai considerar como saudável ou não?

[03:11] Se viermos na documentação, mais uma vez, do nosso Liveness Probe, nós vamos ver que ele tem um intervalo específico para considerar a aplicação saudável. Então, qualquer código html que seja igual ou maior a 200 e menor do que 400, indica sucesso. Qualquer outro código maior ou igual a 400 ou menor do que 200 indica falha.

[03:41] Logo, vamos ter essa garantia que teremos uma requisição com status ok, um redirecionamento e assim por diante. Então, ele vai ter essa garantia de que a aplicação está funcionando.

[03:53] Então, vamos lá! Vamos salvar e nesse cenário não vamos precisar reiniciar este Pod e basta aplicarmos ao nosso \portal-noticias-deployment.yaml e ele vai configurar.

[04:09] E agora, se dermos um kubectl describe pod portal-noticias-deployment o que temos aqui são todas as nossas informações que ele foi iniciado, depois de ter sido criado e tudo muito bem definido. Nós temos tudo certo, nenhum problema, ele está em execução.

[04:31] Não é à toa que se dermos um kubectl get pods estão aqui os três Pods em execução. Nós conseguimos acessar nossa aplicação normalmente, com status de 200, então, nossa aplicação está saudável e nós temos a garantia de que, se em algum momento, ao fazer essa requisição tivermos um Status Code de 500, por exemplo, conseguiremos fazer com que nossa aplicação, dentro do nosso container, seja reiniciada sem nenhuma preocupação e vamos informar que queremos que isso aconteça porque não aconteceu o que esperávamos.

[05:10] Então, paramos com essa parte Liveness Probe. Nós sabemos, agora, garantir, definir uma prova de vida para nossas aplicações, que vimos que é bem simples. Basta adicionarmos o trecho do livenessProbe do arquivo portal-noticias-deployment.yaml nós podemos, inclusive, fazer a mesma definição para nosso sistema-noticias-statefulset.yaml, porque nada vai mudar.

[05:30] Eu vou, inclusive, salvar o mesmo trecho e só vou aplicar com kubectl apply -f no nosso sistema-noticias-statefulset.yaml e ele também foi configurado e tudo continuou funcionando, normalmente, sem nenhum mistério.

[05:46] Se eu dou um "F5" na página do Portal de Notícias no navegador, ele está configurando, ele está subindo, novamente. Pronto, e agora tudo continua funcionando. Repare que ele só demorou um pouco para subir, porque ele estava reconfigurando e subindo tudo, os nossos Persistent Volums, mas, nenhum problema.

[06:09] Então, para esse vídeo, finalizamos agora e no próximo vamos falar sobre outro tipo de provas de vida, que são os Readiness Probe e eu vejo vocês lá. Até mais!

### Utilizando Readiness Probes
[00:00] Estamos de volta ao nosso cenário original porque veremos outro problema que tem a possibilidade de acontecer. Temos algumas requisições chegando ao nosso serviço e ele vai fazer o balanceamento entre cada um desses Pods.

[00:14] Mas, o que temos a possibilidade de ver acontecer? Em algum momento, algum desses Pods, por exemplo, tem a capacidade total de falhar. Eles são suscetíveis a erro, ou um container dentre deste Pod também. E o que vai acontecer?

[00:32] Nós já vimos a possibilidade de definir um Liveness Probe para o container desse Pod e ele vai voltar à execução, ou também, se o Pod, como um todo, tiver falhado, temos a possibilidade de usar Deployments, StatefulSets, ReplicaSets para garantir que este Pod vai voltar à execução.

[00:52] Mas, o que importa é que enquanto ele volta à execução, o Pod já está pronto, mas, o container que, também, já subiu, ainda não terminou, não está pronto para receber essas requisições. Ele ainda não terminou de executar os scripts que ele tem para iniciar ou qualquer outra coisa do tipo.

[01:12] Então, precisamos ter uma maneira de garantir quando o container deste Pod estará pronto para receber as requisições e consigamos parar de fazer essa divisão entre só o nosso segundo e terceiro Pod, para que o primeiro receba um sinal de ok e passe a receber as requisições, novamente.

[01:31] E a questão para fazermos isso é bem simples. Basta definirmos os nossos Readiness Probes, que são bem fáceis e é, basicamente, definirmos uma situação bem parecida, só vão mudar as consequências.

[01:46] Então, vou colocar um Readiness Probe com a mesma declaração de um Liveness Probe, onde eu vou fazer uma requisição utilizando o verbo get para o meu caminho barra na porta 80 a cada 10 segundos e o failureThreshold, onde vimos que no nosso Liveness Probe significa que se ele não conseguir executar este teste três vezes, ele vai reiniciar a aplicação.

[02:14] Nesse caso significa que se ele não conseguir executar esse teste três vezes, na quarta vez, ele vai enviar as requisições, mesmo assim, então ele vai passar a ignorar esse Readiness Probe.

[02:31] Então, podemos definir que um número maior, como, por exemplo, cinco, dez, e um tempo inicial, podemos colocar, por exemplo, três segundos depois que o Pod iniciar e o container estiver subido também, nós precisamos esperar três segundos antes de começar a fazer estes testes, que ele vai executar a cada 10 segundos.

[02:54] Então, pegamos o trecho do readnessProbe e podemos também aplicar ao nosso statefulset, aos containers que estão no nosso statefulset, no caso, do nosso sistema. Então, o que precisamos fazer? A mesma coisa, Readiness Probe, mas, podemos, também, colocar outro critério, que ele vai definir essa aplicação como pronta se ele conseguir enviar requisições para o nosso inserir-noticias.php.

[03:25] Então, vamos definir a nossa aplicação como pronta para receber requisições, quando o inserir-noticias.php retornar um código entre 200, inclusive 400, exclusive. Basta voltarmos no nosso PowerShell, dar um kubectl apply -fno nosso portal-noticias-deployment.yaml, ele vai configurar, e também, no nosso sistema-noticias-statefulset.yaml, que vai ser configurado, também.

[03:54] Agora, podemos dar um kubectl get pod --watch que ele vai começar a fazer a mágica acontecer. Ele vai encerrar os containers e Pods anteriores e vai começar a executar novos, mas, ainda não estão prontos, porque ele está esperando aquele tempo de delay inicial para que seja feito.

[04:12] No nosso caso do nosso sistema-notícias do statefulset, ele está como 01, ele esperou três segundos para começar a executar o teste e, daqui a pouco, ele vai ficar com status de running 1/1, significando que ele já está pronto para receber requisições.

[04:31] Se viermos no navegador e tentar fazer uma requisição, conseguimos, porque se viermos no PowerShell, ele já terminou. Ele só não tinha terminado de atualizar, mas, já está em execução há oito segundos.

[04:45] Então, tudo continua funcionando. Temos o nosso portal, temos o nosso sistema, vamos colocar uma notícia, de novo, com outro assunto novo, mas, vamos repetir a mesma imagem da Alura, salvando, clicando no botão “Salvar” dentro da janela. Tudo continua funcionando, vamos dar um "F5" e perfeito.

[05:06] Então, agora temos a garantia que nossa aplicação está saudável, pronta para receber requisições e também para ser reiniciada com a nossa criterização.

[05:18] E podemos ir mais além, posso mostrar para vocês que além de toda essa questão, de definir através de request HTTP, nós podemos, também, fazer definições através de TCP, então, podemos enviar através de um Socket com o TCP, por alguma porta, para validar se a aplicação está saudável ou não.

[05:41] Então, essa aula foi sobre isso. Para vermos como podemos garantir que nossas aplicações estão prontas para serem executadas, receberem requisições e também, se elas estão saudáveis ou devem ser reiniciadas, através dos nossos Liveness Probes. Então, por esse vídeo é só. Nós nos vemos na próxima aula e até mais!

### Para Saber Mais: Startup Probes
Há um terceiro tipo de probe voltado para aplicações legadas, o Startup Probe. Algumas aplicações legadas exigem tempo adicional para inicializar na primeira vez. Nem sempre Liveness ou Readiness Probes vão conseguir resolver de maneira simples os problemas de inicialização de aplicações legadas. Mais informações sobre Startup Probes podem ser adquiridas por aqui.

https://kubernetes.io/docs/tasks/configure-pod-container/configure-liveness-readiness-startup-probes/#define-startup-probes

### o que aprendemos?
* o kubernetes nem sempre tem como saber se a aplicaçao dentro do container esta saudavel
* podemos criar criterios para definir se a aplicaçao esta saudavel atraves de probes
* como criar LivenessProbes com o campo 'livenessProbe'
* LivenessProbes podem fazer a verificaçao em diferentes intervalos de tempo via HTTP
* como criar ReadinessProbes com o campo 'readinesProbe'
* ReadinessProbes podem fazer a verificaçao em diferentes intervalos de tempo via HTTP
* LivenessProbes sao para saber se a aplicaçao esta saudavel e/ou se deve ser reiniciada, enquanto ReadinessProbe sao para saber se a aplicaçao já esta pronta para receber requisiçoes depois de iniciar
* alem do HTTP, tambem podemos fazer verificaçoes via TCP

### Escalando pods automaticamente - Horizontal Pod Autoscaler
[00:00] Agora nós vamos ver um cenário um pouco diferente do que nós estamos habituados.

[00:04] Nós temos um Pod sendo gerenciado por um service e as requisições vão chegando para esse service e ele vai enviando para o nosso Pod, até aí nada de novo.

[00:13] Mas, o que nós temos a capacidade de imaginar aqui? Vamos colocar um cenário novo, vamos dizer que nós estamos falando do nosso portal de notícias e agora nós estamos recebendo diversas requisições porque nós colocamos uma notícia nova no nosso portal e várias pessoas agora querem ler.

[00:29] Então, mais pessoas vão passar a acessar o nosso portal. Isso quer dizer o que? Que o nosso Pod vai passar a consumir mais recursos porque ele vai precisar lidar com mais requisições e enviar mais respostas. Isso quer dizer que ele vai ter um consumo maior de processamento, memória e afins.

[00:46] Qual é o problema disso? O problema é que se ele ficar consumindo de vários, por vários momentos, muitos momentos esse recurso, esse processamento, essa memória, ele vai passar a demorar responder os nossos usuários.

[01:00] Porque ele vai estar ali meio que lento por faltar recursos para ele conseguir trabalhar de maneira hábil.

[01:07] E pior ainda, nós temos a possibilidade desse Pod parar de funcionar por falta de recurso e por mais que ele esteja dentro de um Deployment ou de um StatefulSet ou de um ReplicaSet e seja reiniciado, ele vai continuar caindo pela falta de recurso. Então, a nossa aplicação fica comprometida.

[01:28] Como que nós podemos resolver isso? Basta nós adicionarmos mais Pods. Com mais Pods agora nós temos mais poderes de processamento para cada um deles e vamos conseguir trabalhar sem nenhum problema.

[01:40] Então, nós conseguimos responder os nossos usuários de maneira hábil e, caso o número de acessos ao nosso portal caia, basta diminuir o número de Pods em execução. Perfeito!

[01:53] Só que o problema é: será que temos alguma maneira automatizada de fazer isso? Nós temos e quem vai nos ajudar, esse recurso se chama Horizontal Pod Autescaler. Vamos dar uma olhada na documentação para ver o que esse recurso vai fazer por nós.

[02:13] Se dermos uma lida na documentação do Kubernetes, ele resume para nós que o Horizontal Pod Autoescaler é um recurso capaz de, automaticamente, escalar o número de Pods em um Deployment, em um ReplicaSet, em um StatefulSet, baseado na observação da CPU, então, nós temos um primeiro ponto que vamos precisar nos preocupar.

[02:31] E ele vai fazer isso de maneira automática, que é o que importa para nós. Então, vamos fazer um Horizontal Pod Autoescaler para o nosso Deployment do nosso portal-noticias, baseado num consumo de CPU dele, nós vamos aumentar ou diminuir, para suprir essa demanda, o número de Pods.

[02:50] Só que, antes de começarmos, repara se voltarmos na documentação e lermos mais uma vez, ele faz isso baseado em métricas, como, por exemplo, a utilização de CPU.

[03:02] Só que nós precisamos informar, nós temos essa necessidade de declarar quanto esse container, dentro desse Pod, consome de CPU. Quanto ele pede de CPU para funcionar?

[03:16] Então, nós podemos definir que dentre as informações que ele requer, por exemplo, ele pede por algum recurso, que é a nossa CPU. Então, podemos colocar que este container exige 10 milicores de CPU para funcionar.

[03:35] E, como ele pede por esse recurso de CPU, nada mais válido do que colocarmos ele dentro de um campo chamado recursos. E alinhamos tudo para ficar certo.

[03:48] Então, nós estamos falando que cada Pod que tenha um container dentro do resources vai pedir 10 milicores de CPU para funcionar.

[04:00] Então, agora que definimos isso, como fazemos o Horizontal Pod Autoescaler para este Pod? Simples! Assim como os nossos outros recursos da API, se voltarmos à documentação, nós vemos que o Horizontal Pod Autoescaler também é um objeto da API.

[04:17] Então, nós podemos criar para ele um arquivo de definição no terminal, que vou chamar de portal-noticias-hpa.yaml. Dentro dele podemos definir a versão da API, que se olharmos com clareza, vemos que tem ou um autoescaling/v1 ou um autoescaling/v2beta2.

[04:37] Nós vamos utilizar a v2beta2 porque toda a documentação está começando a ser mais baseada nela. Ela já está em vias, em ficar 100% estável e ela tem novas instruções e mais enxutas também, então, e por isso vamos utilizar ela.

[04:55] Então, vamos definir nossa versão da API, o tipo do que nós queremos criar é um HorizontalPodAutoescaler e ele tem um metadata, assim como nos outros recursos e vamos dar o nome para ele de portal-noticias-hpa.

[05:10] Nas especificações dele, nós precisamos nos preocupar com o seguinte: nós queremos que este Horizontal Pod Autoescaler faça o que? A referência ao nosso portal de notícias. Então, eu preciso definir à quem eu quero fazer a referência.

[05:31] Então, qual é o meu alvo que eu quero fazer referência? Mais além, quem eu quero escalar automaticamente? Eu preciso informar qual é a versão da API do meu alvo. Então, qual é a versão do API do meu alvo, que é esse Deployment? É apps/v1.

[05:49] Qual é o tipo do que eu quero escalar automaticamente? É um Deployment. Qual é o nome desse Deployment? É portal-noticia-deployment.

[06:01] E agora, eu preciso informar o seguinte: qual o número mínimo e máximo de réplicas que eu quero ter para esses Pods do meu Deployment? Eu quero manter sempre um número mínimo de uma réplica e nunca vou poder passar, por exemplo, de 10.

[06:17] Então, por mais que chegue 1 trilhão de requisições e eu precise colocar 200 Pods, eu não vou passar, nunca, de 10.

[06:28] E eu preciso, agora, informar quais são as métricas que eu quero definir para esse Horizontal Pod Autoescaler. Então, o que eu quero definir como o tipo de métrica?

[06:37] Eu quero, baseado nos recursos, não nos recursos do Kubernetes em si, e sim nos recursos do sistema, porque temos recursos de processamento, memória e afins; eu quero definir qual eu vou utilizar.

[06:50] Então, qual é esse recurso que eu quero usar como critério? Eu quero utilizar um recurso chamado CPU. E o que eu almejo com esse recurso? Eu quero que baseado na utilização dele, ele mantenha sempre um uso médio de 50%, por exemplo.

[07:10] 50% de que? Por isso que nós definimos esses 10 milicores. Então, se o consumo médio da nossa aplicação desse Deployment chegar a mais de 5 milicores, o nosso Horizontal Pod Autoescaler vai fazer a mágica dele acontecer, ele vai criar mais Pods para que o consumo médio não passe de 50% de 10 milicores, então, para que ele não passe de 5 milicores, ele fique nessa faixa.

[07:47] Então, vamos fazer isso agora. Salvamos o nosso portal-noticias-deployment com a mudança dele e o nosso Horizontal Pod Autoescaler. Vamos, então, aplicar essas mudanças no PowerShell kubectl apply –f vou passar o nosso portal-noticias-deployment.yaml e agora vou passar o nosso kubectl apply –f e vou passar o nosso portal-noticias-hpa.yaml.

[08:18] Agora, nós criamos. E ele foi criado. Se nós dermos, agora, um kubeclt get hpa, de Horizontal Pod Autoescaler, o que vai acontecer? Que legal!

[08:27] Ele está falando que nós temos o nosso Horizontal Pod Autoescaler, que faz referência a este nosso Deployment do portal-notícias, mas, se temos um olhar de que, por enquanto, ele ainda não reconheceu as nossas réplicas, isso é um primeiro problema, mas, ele também não sabe quanto estamos utilizando daqueles 50% que nós definimos.

[08:50] Vamos dar um comando, de novo, para ver se alguma coisa muda. Temos um positivo, ele já identificou as três réplicas, que por padrão, nós definimos no nosso arquivo. As três réplicas estão em execução, perfeito, mas, ele ainda não consegue identificar quantos por cento do processamento está sendo usado.

[09:11] Vamos tentar mais uma vez e nada. Vamos fazer o seguinte, vamos dar uma olhada, vamos ser abelhudos e vamos descrever o nosso Horizontal Pod Autoescaler chamado portal-noticias-hpa.

[09:25] Olha o que aconteceu. Vamos dar uma olhada no que está descrito após o comando. Ele foi incapaz de pegar as métricas para recurso de CPU. Ele não foi capaz de pegar esses dados da API de métricas. O servidor não pôde encontrar esse recurso pedido. E aqui ele fala que essa métrica foi inválida e nós precisamos definir o que é uma CPU.

[09:50] Então, temos um pequeno problema. O que é esse servidor de métricas que ele falou para nós. Como conseguimos utilizá-lo para fazer o nosso Horizontal Pod Autoescaler funcionar? Isso vamos ver no próximo vídeo e eu vejo vocês lá. Até mais!

### utilizando o HPA no windows
Atenção! Para fazer o download do script de stress, basta acessar esse link. Já para o arquivo de definição do servidor de métricas, basta baixá-lo através desse link.

(disponiveis junto ao codigo)
arquivo de stress: stress.zip
arquivo de definiçao: componentes.yaml

[00:00] Estou aqui no Github na página do metrics-server, que é um repositório do kubernetes-sigs e nós temos as informações necessárias para utilizarmos um servidor de métricas no nosso cluster.

[00:15] Se viermos na documentação, em Kubernetes Metrics Server, temos uma questão bem simples de caso de uso. Nós podemos usar um Servidor de Métricas para definir, basear as nossas informações de consumo de CPU e memória para utilizar o Horizontal Pod Autoescaler e, também, fazer esse ajuste de maneira automática, conforme recursos necessitados pelos containers.

[00:37] Então, é basicamente o que queremos. E como utilizamos ele? É bem simples, é só descermos até a descrição de Deployments, clicar na parte Metrics Server releases e nós vamos baixar a versão v0.37, basta clicar mais embaixo em components.yaml e ele vai fazer o download para nós.

[00:56] Eu vou já arrastar ele direto para dentro do Visual Studio Code e você que está utilizando o Windows comigo, (teremos um vídeo somente para o Linux), vamos precisar fazer o seguinte.

[01:08] Se você reparar o trecho descritivo da apiVersion é nada mais do que um arquivo de definição, que nós já viemos trabalhando, mas, mais abaixo temos a parte toda da definição do nosso Metric Server, que está, exatamente, descrita no API.

//código omitido

---
apiVersion: v1
kind: ServiceAccount
metadata:
    name: metrics-server
    namespace: kube-system
---

//código omitidoCOPIAR CÓDIGO
[01:22] Dentro dele, nós temos essa parte em que ele define os argumentos que serão passados para este Pod do nosso Metric Server.

[01:30] E, no caso do Windows, nós vamos precisar fazer o seguinte: mais aqui embaixo na documentação, ele fala na questão de configuração que, caso nós não tenhamos o objetivo de utilizar, fazer uma verificação de certificados, nós podemos desabilitar com essa flag --kubelet-insecure-tls.

[01:50] No caso do Windows, nós vamos precisar definir essa flag dentro do nosso arquivo de definição. Então, um traço aqui em args e definimos os --kubelet-insecure-tls. Basta, agora, darmos um kubectl apply -f no PowerShell e passar o nosso arquivo recém baixado e editado, que é o nosso \.componets.yaml.

[02:13] Dando um "Enter" ele vai criar todos os recursos definidos lá dentro e agora, o que vai acontecer? Temos o nosso kubectl get hpa e ele continua um tanto quanto engraçado, isso não é um erro, ele continua falando que não está identificado.

[02:32] Então, mais uma vez, vamos dar um kubectl describe hpa e passar o nosso portal-noticias-hpa. Ele, há 51 segundos tentou, de novo, pegar, mas, ainda não conseguiu, então, o que iremos fazer, o que precisamos fazer? Precisamos esperar ele terminar de carregar todas as informações, para que ele consiga ler todos os detalhes de consumo de CPU.

[02:59] Isso é “um bug", que ele demora a fazer esse reconhecimento, então, assim que ele terminar, voltamos e seguimos com nosso Horizontal Pod Autoescaler.

[03:10] Então, o que temos aqui? Temos que nós estamos utilizando 10% e não 50%, então, como estamos utilizando abaixo do nosso alvo, do nosso limite, temos, apenas, um Pod, uma réplica.

[03:25] Então, como será que ele vai se comportar se nós colocarmos mais recursos sendo consumidos, se nós enviarmos diversas requisições para nossa aplicação do nosso local host, que neste caso, definimos na porta 30000, o nosso portal.

[03:40] Então, eu vou no nosso Visual Studio Code fazer o seguinte: eu tenho um arquivo, que é um scriptshell, que vai enviar diversas requisições para o nosso local host na porta 30000, que é onde foi definido nosso portal de notícias, e vou fazer isso enviando indefinidamente. Só que para executarmos este script com SH, nós precisamos ter alguma ferramenta no Windows, que seja capaz de executá-la.

[04:07] Nesse caso, eu vou utilizar o Git Bash. Então, vou deixar o link de download para vocês fazerem sem nenhum problema da ferramenta e para vocês poderem executar. Eu vou acessar o nosso diretório, que é o nosso kubernetes-alura e para executar ele é bem simples.

[04:24] Eu vou colocar SH, vou colocar o nome do nosso script, que é stress.sh, e eu preciso definir, ele recebe um parâmetro aqui, o nosso intervalo. Eu vou colocar de 0,001 segundos e, por fim, vou colocar para vermos a saída dele, para imprimirmos tudo certo neste arquivo de saída.

[04:45] Dou um "Enter" e ele vai começar a executar. E para sermos mais gananciosos, eu vou abrir o outro Git Bash e vou fazer a mesma coisa, executar dois ao mesmo tempo. Vou acessar o nosso kubernetes-alura e vou executar o SH também, no nosso stress.sh, a cada 0,0001 segundos e salvar em outro arquivo de saída.

[05:09] Agora, nós vamos observar no nosso PowerShell o que? Eu vou colocar para analisarmos o nosso Horizontal Pod Autoescaler com o --watch e se nós repararmos ele já está com consumo de 30%, em relação ao alvo, e conforme esse consumo for subindo, nós vamos ver a mágica acontecer.

[05:26] Então, em algum momento, esse consumo vai ficar tão visível para o nosso Pod, para o nosso container, que nós vamos precisar criar mais Pods. Então, como mais uma vez, não temos a garantia de quanto tempo ele vai demorar em nos exibir isso, eu vou fazer um pequeno corte no vídeo e quando estiver vendo os resultados, eu volto para comentarmos.

[05:48] O que está acontecendo é que tivemos esse consumo todo. Eu já vou parar para irmos dando tempo dele voltar ao normal; nós tivemos um consumo que ele foi subindo, ficou 30%, e 30% ainda está abaixo do nosso alvo, ele continuou com um Pod, com uma réplica.

[06:11] Ficou em 100% ele viu que é melhor criar agora mais uma réplica e foi o que ele fez, então, ele se manteve e conforme a demanda foi subindo, ele viu que ainda estava longe do alvo, que era de 50%, e ele criou mais uma réplica.

[06:27] E agora, como eu interrompi toda essa criação e envio de requisições, a ideia é que, aos poucos, ele vai voltar ao estado inicial de uma réplica, porque, todo o nosso recurso, que era cobrado, não precisa mais, porque não estamos mais enviando requisição, e ele vai voltar, automaticamente, para uma réplica.

[06:49] Então, reparem que já caiu aqui, ele atualizou o consumo para 53% e ele vai continuar nessa queda, até voltar para o 10%, que era o padrão dele, utilizando uma réplica, apenas.

[07:03] Então, o que conseguimos fazer: definindo, não o nosso arquivo de stress, mas, o nosso Horizontal Pod Autoescaler, nós definimos que queremos manter um consumo médio de 50% da CPU, que é requisitada por cada Pod, por cada container dentro do Pod.

[07:21] Nesse caso, de 10 milicores, e sempre que ficarmos acima desse consumo, ele vai colocar mais Pods, tendo um limite de 10, como definimos, para que esse consumo seja ajustado.

[07:37] Então, o máximo que chegamos foi três, mas, ele agora vai regredir, aos poucos, como não está recebendo mais nada, ele vai ficar abaixo desses 50%, que é a nossa média, e vai voltar para o estado inicial dele, que é de uma réplica, a aplicação está ociosa.

[07:51] Então, por essa aula é só, por esse vídeo. Eu vou, agora, mostrar para o pessoal do Linux como vai ser a pequena diferença na questão do IP, que teremos que utilizar no nosso arquivo e, também, como vai funcionar no Minikube. Então, por esse vídeo aqui é só e eu vejo vocês no próximo e até mais!

### Utilizando o HPA no linux
[00:00] Assim como no Windows, nós também vamos precisar de um servidor de métricas no Linux. E o que ele é, caso você não tenha visto o vídeo anterior ou esteja relembrando agora?

[00:10] Ele nada mais é do que uma aplicação usada para fazer nossa escalabilidade horizontal em conjunto com o nosso Horizontal Pod Autoescaler, baseado no nosso consumo de CPU e memória.

[00:22] Então, ele é o responsável por ser o servidor de métricas, o nome já diz. Ele vai ser responsável por servir essas informações para todos os nossos recursos dentro do nosso cluster.

[00:34] E como fazemos para utilizar esse servidor de métricas? No Windows, nós precisamos utilizar esse arquivo de componentes descrito na documentação, que nós declaramos e definimos e aplicamos no nosso cluster. No caso no Linux, nós estamos utilizando o Minikube e ele, no Linux, tem diversas possibilidades para utilizarmos.

[00:54] Como, por exemplo, se dermos uma olhada na documentação ele já tem uma parte voltada apenas para as extensões, então, se nós executarmos esse comando minikube addons list reparem o que ele vai nos mostrar. Ele mostra uma série de extensões que podemos utilizar e estão desabilitadas, a maioria.

[01:17] Dentre elas, nós temos o servidor de métricas e para utilizar ele é bem simples, basta habilitá-lo com comando minikube addons enable metrics-server. E, a partir de agora, nós vamos ter isso habilitado, só que, antes de mais nada, antes de habilitarmos, eu vou mostrar para vocês que nós estamos com o mesmo estado que tínhamos no Windows.

[01:40] Nós temos os nossos Pods, das nossas aplicações, e temos também o nosso Horizontal Pod Autoescaler, já em execução com o arquivo que definimos. Então, agora vamos dar o nosso minikube addns enable metrics-server.

[01:58] E, agora, ele vai habilitar esse recurso para nós. Bem simples. O ponto agora é que assim que ele terminar de sincronizar, nós vamos ter o nosso alvo definido dentro do nosso cluster, quanto de consumo estamos tendo para os containers dos Pods desse Deployment.

[02:16] E como não sabemos quanto tempo ele vai demorar para fazer essa sincronização, eu vou pausar o vídeo e quando ele começar a exibir os resultados, eu volto para nós seguirmos.

[02:25] Pessoal, então foi. Se eu executar o comando kubectl get hpa ele está utilizando 0% dos nossos 50% definido, da nossa média, e ele está utilizando uma réplica, que é o mais próximo que ele consegue manter dentro da nossa média de consumo de 50%, não tem como ele consumir de graça para ficar mais perto da nossa média.

[02:46] Então, o máximo que ele tem é 0% para ficar próximo dos nossos 50%, então, ele está usando só uma réplica. Então, o que vamos fazer agora? Vamos estressar a nossa aplicação e para gente utilizar, fazer esse estresse, eu tenho um arquivo que é o nosso stress.sh e nele precisamos definir o IP do nosso nó.

[03:11] No caso da minha máquina, quando eu criei esse cluster com o Minikube, eu vou abrir uma nova aba do terminal, se dermos um kubectl get nodes –o wide foi aqui que ele definiu para nós esse IP no INTERNAL-IP 192.168.99.106.

[03:33] Então, é esse IP que vou colocar aqui na porta 30000, que é onde definimos que o nosso portal de notícias está em execução. Então, dito isso, temos o nosso script e vamos executá-lo.

[03:46] Vou colocar o nosso bash e vou passar o nosso arquivo, o nosso script de estresse, para ele executar a cada 0.001 segundos, e vou salvar e sair do out.pxt.

[04:01] Vamos ver a mágica acontecer. Ele vai começar a enviar diversas requisições e agora, no outro terminal (vou colocar os dois lado a lado) vou executar o kubectl get hpa --watch e nós vamos ver a mágica acontecer.

[04:19] Eu vou expandir o terminal direito mais um pouco, porque ele é mais relevante e nós vamos ver que ele está utilizando, até então, ainda um Pod, uma réplica dele, porque o consumo ainda está em 0%, mas, aos poucos ele vai começar a atualizar esse valor porque a nossa aplicação está recebendo diversas requisições, então, vamos ver os resultados acontecendo.

[04:41] E o que ele vai fazer? Será que ele vai criar muitos Pods a mais para manter esse consumo médio em 50%? Vamos dar uma pausa no vídeo e assim que ele começar a exibir os resultados voltamos para analisar.

[04:57] O que aconteceu foi que as requisições pararam de ser enviadas (vou maximizar esse segundo terminal à direita, clicando e arrastando com o mouse na extremidade esquerda da tela deste terminal).

[05:02] Ele começou a enviar tantas requisições e o consumo foi ficando tão acima da nossa média esperada de 50% em TARGETS, ficando na faixa de 500%, por exemplo, que ele foi precisando criar mais e mais réplicas, até chegar ao nosso limite de 10, onde ele não pôde mais passar, porque esse era o nosso máximo.

[05:20] E, a partir daí, como no nosso outro terminal eu já parei de enviar as requisições, ele vai passar a diminuir esses recursos.

[05:30] Porque como eles não estão sendo mais utilizados da mesma maneira de antes, reparem que ele já caiu pra 5%, a ideia é que ele vai começar a diminuir, aos poucos, o número de Pods que estão em execução, para não ficar nenhum Pod ocioso ali, para manter tudo da maneira mais básica possível.

[05:49] Então, mais uma vez, como agora paramos de enviar as requisições e não sabemos o tempo que ele vai demorar para atualizar, eu vou pausar o vídeo, de novo, para assim que ele voltar e tivermos um resultado mais enxuto, de quantos Pods ele está utilizando, eu volto para analisarmos.

[06:09] E voltamos ao nosso estado inicial de um Pod, apenas, porque nosso consumo voltou para 0%. Perfeito, pessoal!

[06:17] Então, agora o que conseguimos fazer, tanto no Windows quanto no Linux, nós conseguimos definir, automaticamente, critérios para que nosso cluster consiga automatizar se ele vai colocar mais ou menos Pods conforme o consumo de recursos que nós temos.

[06:35] E isso de maneira bem simples e fácil, através de um arquivo de definição. Então, nós vamos terminar essa aula agora, onde nós vimos como definir um Horizontal Pod Autoescaler e utilizar um Servidor de Métricas tanto no Windows quanto no Linux e eu vejo vocês no próximo vídeo. Até lá!