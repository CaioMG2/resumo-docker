Resumo sobre os estudos de Docker, Docker Swarm e Kubernetes.

1. **Introdução ao Docker:**
   - O Docker é um software que simplifica a configuração de aplicações, permitindo criar e gerenciar containers que funcionam como ambientes isolados para executar aplicações.
   - Containers são unidades leves e portáteis que contêm tudo o que é necessário para executar uma aplicação, incluindo código, runtime, bibliotecas e configurações.

2. **Vantagens do Docker:**
   - Facilidade na criação de ambientes independentes e portáteis.
   - Suporte a diferentes sistemas operacionais.
   - Eficiência de recursos e performance.
   - Agilidade na configuração de ambientes de desenvolvimento.
   - Execução consistente em diferentes ambientes.

3. **Desafios Resolvidos pelo Docker:**
   - Complexidade na configuração de ambientes.
   - Manutenção simplificada.
   - Performance otimizada.
   - Abstração de ambientes e dependências.

4. **Docker Swarm e Kubernetes:**
   - **Docker Swarm:** É uma ferramenta nativa do Docker para orquestração de containers, permitindo gerenciar e escalar aplicações distribuídas.
   - **Kubernetes:** É uma plataforma de orquestração de containers de código aberto que automatiza o deployment, o escalonamento e a operação de aplicações em containers.

5. **Uso de Comandos no Terminal:**
   - `docker ps` ou `docker container ls`: Lista os containers em execução.
   - `docker version`: Exibe informações sobre a versão do Docker.
   - `docker run <imagem>`: Cria e executa um container baseado em uma imagem.
   - `docker ps -a`: Lista todos os contêineres, inclusive os que não estão em execução.

6. **Exemplo de Uso do Docker:**
   - Utilizando a imagem "docker/whalesay" para exibir uma baleia com uma mensagem de texto.
   - Comando: `docker run docker/whalesay cowsay Hello_World`

7. **Conceitos Fundamentais:**
   - **Containers:** São pacotes que podem executar ações, como rodar aplicações em diferentes linguagens.
   - **Imagens:** São representações estáticas dos aplicativos ou serviços, contendo configurações e dependências.
   - **Docker Hub:** É o repositório público de imagens Docker, onde é possível encontrar e compartilhar imagens prontas para uso.

8. **Fluxo de Utilização do Docker:**
   - Programa-se uma imagem, que contém as instruções para a execução de uma aplicação.
   - A imagem é utilizada para criar um container, onde a aplicação é executada de maneira isolada e controlada.

9. **Localização de Imagens:**
   - As imagens podem ser encontradas no repositório oficial do Docker Hub (https://hub.docker.com).
   - Nesse repositório, é possível pesquisar por imagens de diversas tecnologias e aprender como utilizá-las.

O Docker oferece uma abordagem poderosa para simplificar o processo de desenvolvimento, configuração e distribuição de aplicações, permitindo a criação de ambientes consistentes e portáteis para desenvolvedores. O Docker Swarm e o Kubernetes complementam essa jornada, fornecendo ferramentas de orquestração para gerenciar aplicações distribuídas em escala.

Docker para desenvolvedores (com Docker Swarm e Kubernetes)

O Docker oferece uma abordagem poderosa para simplificar o processo de desenvolvimento, configuração e distribuição de aplicações, permitindo a criação de ambientes consistentes e portáteis para desenvolvedores. O Docker Swarm e o Kubernetes complementam essa jornada, fornecendo ferramentas de orquestração para gerenciar aplicações distribuídas em escala.

Executar container com interação:

- Podemos rodar um container e deixá-lo rodando no terminal utilizando a flag -it. Dessa forma, podemos executar comandos disponíveis no container que estamos utilizando o comando run.

O ciclo de vida de um Docker container é:

1. docker run imagename -> create container x from image imagename
2. docker exec x ls -> execute command ls in running container x
3. docker stop x -> stop container (but still visible in docker container ls -a)
4. docker start x -> restart container x
5. docker stop x -> stop container x again
6. docker rm x -> remove container x (now also ls -a won't show it)

Container x Virtual Machine:

- Um container é uma aplicação que serve para um determinado fim e não possui sistema operacional.
- Uma virtual machine possui sistema operacional próprio e pode executar diversas funções ao mesmo tempo.

Rodando container em background:

- Ao iniciar um container, ele fica ocupando o terminal. É possível executar um container em background, para não precisar ficar com diversas abas de terminal abertas, utilizando a flag -d (detached). Verificamos containers em background com docker ps também.

Expor portas:

- Os containers do Docker não têm conexão com nada de fora, portanto, é preciso expor portas. Isso é feito com a flag -p. Pode ser feito assim: -p 80:80, o primeiro é a porta que desejo expor do meu PC e a segunda a que desejo receber do container. Dessa maneira, o container está acessível na porta 80.

Parando containers:

- Podemos parar um container com o comando docker stop <id ou nome>.

Reiniciando containers:

- Para voltar a rodar um container, podemos usar o comando docker start <id>. O comando run sempre cria um novo container, então, caso seja necessário aproveitar um antigo, opte pelo start.

Definir nome de um container:

- Podemos definir o nome de um container com a flag --name <nome>. Se não for colocado, receberemos um nome aleatório. A flag run é inserida junto com o comando run.

Logs:

- Podemos verificar o que aconteceu em um container acessando os seus logs com o comando logs. Docker logs <id>. As últimas ações do container serão exibidas no terminal.

Remover containers:

- Podemos remover containers com o comando docker -rm <id>. Se o container ainda estiver rodando, podemos utilizar a flag -f (force). O container removido não é mais exibido em docker ps -a.

Imagens:

- Imagens são originadas de arquivos que programamos para que o Docker crie uma estrutura que execute determinadas ações em containers. Elas contêm informações como imagens base, diretório base, comandos a serem executados, porta da aplicação, etc. Ao rodar um container baseado em imagem, as instruções serão executadas em camadas.

Criando uma imagem:

- É necessário um arquivo Dockerfile. Ele necessita de algumas instruções para ser executado: from (imagem base), workdir (diretório da aplicação), expose (porta da aplicação), copy (quais arquivos precisam ser copiados).

Executando uma imagem:

- Para executar uma imagem, é preciso realizar o seu build. O comando é: docker build <diretório da imagem>. Depois, utilizamos docker run <imagem> para executa-la. Ao alterar uma imagem, será necessário fazer o build novamente. Para o Docker, é como se fosse uma imagem nova.

Fazendo o download de imagens:

- Docker pull <imagem>.

Múltiplas aplicações no mesmo container:

- É possível inicializar várias containers com a mesma imagem. As aplicações funcionarão em paralelo. Para testar isso, podemos determinar uma porta diferente para cada uma e rodar no modo detached.

Nomeando a imagem criada:

- Podemos nomear a imagem criada utilizando o comando docker tag <nome>. A tag pode ser modificada também. Para inserir a tag, utiliza-se docker tag <nome>:<tag>.

Nomeando a imagem na criação:

- Utiliza-se a flag -t. É possível inserir o nome e a tag, na sintaxe nome:tag. Docker build -t <nome>:<tag>.

- Comando start interativo:
A flag `-it` pode ser utilizada com o comando start também, ou seja, não precisamos criar um novo container para utilizá-lo no terminal. O comando é `docker start -it <container>`.

Rodar um container no modo interativo, indicado pela opção `-it`, permite interagir diretamente com o terminal dentro do container enquanto ele está em execução. Isso significa que você pode fornecer comandos e receber saídas do container em tempo real.

Quando você executa um container no modo interativo, ele não é simplesmente executado em segundo plano como um serviço. Em vez disso, o terminal do seu host se conecta ao terminal do container, permitindo que você:

- Veja a saída do container em tempo real, incluindo mensagens de log e outras informações que normalmente seriam impressas no terminal do container.
- Forneça comandos diretamente para o container. Isso pode ser útil para depuração, testes interativos ou execução de scripts específicos no ambiente do container.
- Visualize e responda a prompts interativos que o container possa apresentar.

Por exemplo, ao rodar um container no modo interativo, você pode iniciar um shell dentro do container e trabalhar no sistema de arquivos do container como se estivesse em um ambiente Linux separado. Isso é útil para fins de desenvolvimento, depuração ou exploração do ambiente do aplicativo dentro do container.

Removendo imagens:
Para remover uma imagem, utilize o comando `docker rmi <imagem>`. Você pode utilizar a flag `-f` para forçar a remoção caso a imagem esteja sendo utilizada.

Removendo imagens e containers:
O comando `docker system prune` permite remover imagens, containers e networks não utilizados. O sistema irá exigir uma confirmação para realizar essa ação.

Autenticação e Logout:
Para autenticar-se pelo terminal, utilize o comando `docker login`. Para sair, utilize `docker logout`.

Enviando imagens para o Docker Hub:
Para enviar imagens para o Docker Hub, utilize o comando `docker push <imagem>`. Antes disso, é necessário criar um repositório, semelhante ao GitHub. Para baixar uma imagem, utilize `docker pull <imagem>`, e depois você pode criar um novo container com `docker run <imagem>`.


Docker Volume:

Uma forma prática de persistir dados em aplicações e não depender de containers. Todo dado criado por um container é isolado por ele, mas quando o container é removido, perdemos os dados. Portanto, precisamos dos volumes para gerenciar os dados e também conseguir fazer backups de forma simples.

Tipos de Volumes:

1. Anônimos: Diretórios criados pela flag `-v`, com nome aleatório.
2. Nomeados: Com nomes específicos.
3. Bind Mounts: Uma forma de salvar dados na máquina sem o gerenciamento do Docker. Informamos um diretório para esse fim.

Comandos Úteis:

- `docker volume ls`: Lista todos os volumes do ambiente.
- `docker run -v nome-do-volume:/caminho/no/contêiner nome-da-imagem`: Cria um container com um volume nomeado.
- `docker volume prune`: Remove todos os volumes não utilizados.
- `docker volume rm <nome-do-volume>`: Remove um volume específico.
- `docker volume inspect <nome-do-volume>`: Exibe informações detalhadas sobre um volume específico.
- `docker volume create <nome>`: Cria um volume manualmente.
- `docker run -v volume:/data:ro`: Cria um volume somente leitura.

Exemplos de Uso:

- Volume Anônimo: `docker run -v /data`.
- Volume Nomeado: `docker run -v nomedovolume:/data`.
- Bind Mount: `docker run /dir/data:/data`.

Redes no Docker:

As redes no Docker são uma forma de gerenciar a conexão do Docker com outras plataformas ou até mesmo entre containers. Elas são criadas separadas do container, assim como os volumes. Além disso, existem alguns drivers de rede que podem ser utilizados para diferentes fins.

Principais Tipos de Comunicação em Containers:

1. Externa: Com uma API de servidor remoto.
2. Com o Host: Com a máquina que está executando o Docker.
3. Entre Containers: Utiliza o driver bridge e permite a comunicação entre dois ou mais containers.

Principais Drivers de Rede:

- Bridge: Conecta containers.
- Host: Conexão entre um container e a máquina que está hospedando o Docker.
- Macvlan: Permite a conexão a um container por um endereço MAC.
- None: Remove todas as conexões de rede de um container.
- Plugins: Permitem extensões de terceiros para criar outras redes.

Comandos Úteis para Redes no Docker:

- `docker network create <nome>`: Cria uma nova rede.
- `docker network ls`: Lista todas as redes disponíveis no sistema.
- `docker network inspect <nome>`: Exibe informações detalhadas sobre uma rede específica.
- `docker network rm <nome>`: Remove uma rede específica.
- `docker network connect <rede> <container>`: Conecta um container a uma rede existente.
- `docker network disconnect <rede> <container>`: Desconecta um container de uma rede.
- `docker run --network <nome-da-rede> <nome-da-imagem>`: Cria um container em uma rede específica.

Conexão com o Host do Docker:

É possível conectar um container com o host do Docker, que é a máquina que está executando o Docker. O IP de host pode ser referenciado como `host.docker.internal`.

Docker Compose e Construção de Imagem:

Podemos gerar o build da imagem durante o Compose, o que elimina a necessidade de gerar o build da imagem a cada atualização.

**Verificando Serviços no Compose:**
- `docker-compose ps`

Docker Swarm para Orquestração:

O Docker Swarm é um serviço que rege sobre outros serviços para verificar se os mesmos funcionam como deveriam. Exemplos incluem o Docker Swarm, Kubernetes e Apache Mesos.

**Conceitos Importantes:**
- **Nodes:** São instâncias (máquinas) que participam do Swarm.
- **Manager Node:** Node que gerencia os demais nodes.
- **Worker Node:** Nodes que executam tarefas em função do Manager.
- **Service:** Um conjunto de tasks que o Manager Node envia para o Worker Node executar.
- **Task:** Comandos que são executados nos nodes.

**Adicionando Novos Nodes:**
- `docker swarm join --token <token> <ip>:<porta>`

**Criando um Serviço no Swarm:**
- `docker service create --name <nome> <imagem>`

**Criando um Serviço com um Número Específico de Réplicas:**
- `docker service create --name <nome> --replicas <numero> <imagem>`

**Checando o Token do Swarm:**
- `docker swarm join-token manager`

Kubernetes:

Kubernetes é outra ferramenta de orquestração de containers que permite a criação de múltiplos containers em diferentes máquinas (nodes), escalando projetos formando um cluster.

**Conceitos Fundamentais:**
- **Control Plane:** Onde é gerenciado o controle dos processos dos nodes.
- **Nodes:** Máquinas gerenciadas pelo Control Plane.
- **Deployment:** Execução de uma imagem/projeto em um Pod.
- **Pod:** Um ou mais containers que estão em um node.
- **Services:** Serviços que expõem os Pods ao mundo externo.
- **kubectl:** Cliente de linha de comando para Kubernetes.

Minikube:
- **Inicializar o Minikube:** `minikube start --driver=<DRIVER>` (Driver depende das dependências).
- **Verificar status do Minikube:** `minikube status`.
- **Parar o Minikube:** `minikube stop`.
- **Acessar a Dashboard do Minikube:** `minikube dashboard` ou obter a URL: `minikube dashboard --url`.

Deployment:
- **Criando um Deployment no Kubernetes:** `kubectl create deployment <nome> --image=<imagem>`.

**Verificação de Deployments:**
- `kubectl get deployments`.
- `kubectl describe deployments`.

**Verificação de Pods:**
- `kubectl get pods`.
- `kubectl describe pods`.

**Verificação da Configuração do Kubernetes:**
- `kubectl config view`.

Services:
- **Criando um Service no Kubernetes:** `kubectl expose deployment <nome> --type=<tipo> --port=<porta>`.

**Verificando Serviços:**
- `kubectl get services`.
- `kubectl describe services/<nome>`.

**Escalando a Aplicação:**
- `kubectl scale deployment/<nome> --replicas=<numero>`.

**Diminuir a Escala (Scale Down):**
- `kubectl scale deployment/<nome> --replicas=<numero_menor>`.

**Atualização de Imagem:**
- `kubectl set image deployment/<nome> <nome-container>=<nova-imagem>`.

**Desfazendo Alterações:**
- `kubectl rollout undo deployment/<nome>`.
-
**Deletar um serviço:**

    Utilize o comando kubectl delete service <NOME>.

**Deletar um deployment:**

    Use o comando kubectl delete deployment <NOME>.

**Modo Declarativo:**

    O modo declarativo baseia-se em arquivos YAML, semelhantes ao Docker Compose, simplificando as configurações e consolidando o gerenciamento em um único comando.

**Chaves Comuns no Arquivo YAML:**

    apiVersion: Especifica a versão da ferramenta utilizada.
    kind: Define o tipo de objeto (deployment, service, etc.).
    metadata: Descreve o objeto, incluindo o nome.
    replicas: Determina o número de réplicas de Nodes/Pods.
    containers: Define as especificações dos contêineres, incluindo nome e imagem.

**xecutando o Arquivo de Deployment:**

    Crie a implantação com base no arquivo .yaml usando o comando kubectl apply -f <arquivo>.

**Parando uma Deployment:**

    Encerre o deployment com o comando kubectl delete -f <arquivo>.

**Criando um Serviço:**

    Para criar um serviço de forma declarativa, crie um arquivo para definir o Service (kind), semelhante  ao deployment.

**Executando o Serviço:**

    Utilize o comando kubectl apply -f <arquivo> para iniciar o serviço, tornando-o disponível. Lembre-se de gerar o IP de acesso com minikube service <nome>.

**Parando o Serviço:**

    Encerre o serviço com o comando kubectl delete -f <arquivo>.

**Atualizando o Projeto no Modo Declarativo:**

    Crie uma nova versão da imagem e faça o push para o hub. Em seguida, atualize a tag no arquivo de implantação e reaplique o comando de apply.

**Unindo os Arquivos:**

    Combine os arquivos de implantação e serviço, separando-os com --. É uma prática recomendada colocar o serviço antes da implantação.
