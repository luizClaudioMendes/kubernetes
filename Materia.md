# Kubernetes
iniciado em 10/03/2022

terminado em ANDAMENTO

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
