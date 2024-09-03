# docker-training-codespace
Training docker with codespaces


### Definir o que é uma imagem
- Uma imagem no contexto de container é o resultado do build de um Dockerfile
No Dockerfile é definido as instruções para ditar cada processo que será executado nessa imagem que será gerada.
Definir o que é um container
- Um container é uma instância de uma imagem que é executada. 
Fazendo com que seja possível criar um ambiente ideal para sua aplicação ou serviço que é desejada a execução.
O container ele se utiliza de ferramentas que já existem no Linux, que é o CGROUP e Namespace

### Definir o docker

### O que é?
É um software open-source para gerenciar containers e criação de imagens através de um arquivo Dockerfile ou criação de várias imagens Docker.
  - Dockerfile x docker-compose
    - Dockerfile: Arquivo simples que define as instruções para criar uma imagem de um container.
    - docker-compose: Arquivo yaml que define um conjunto de contêineres e quais serviços devem ser configurados e executados juntos.
				
### Definido em 3 partes essenciais
  - Docker CLI: é o Client em linha de comando que você pode instruir comandos docker para criar volumes, imagens e containers.
  - REST API: Camada de comunicação HTTP que recebe os inputs do Client e através dos métodos HTTP (POST, GET, DELETE, PUT) interage com o docker daemon.
  - docker daemon: É a camada que de fato executa as tarefas e gerencia os contêineres, é o núcleo operacional do Docker.

### Para que serve?
- Docker serve para evitar problemas de compatibilidade entre ambientes distintos, assegurando que os aplicativos sejam executados de forma consistente, independentemente do sistema operacional ou das configurações da máquina. Ele isola o ambiente da aplicação, empacotando todo o necessário para sua execução (como código, bibliotecas e dependências) em containers leves e portáteis. Isso garante a portabilidade, permitindo que os aplicativos sejam movidos facilmente entre diferentes etapas do desenvolvimento, teste e produção.
- Além disso, Docker facilita o desenvolvimento do projeto, pois simplifica a configuração do ambiente, acelera a execução de testes e melhora a colaboração entre equipes, reduzindo erros de ambiente e incompatibilidades de software.
