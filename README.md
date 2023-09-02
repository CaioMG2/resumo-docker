Resumo sobre os estudos de Docker.

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


