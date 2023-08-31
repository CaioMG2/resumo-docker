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
