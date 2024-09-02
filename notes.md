### Comando Básico do Docker

- `docker container ls` ou `docker ps` - Lista os conteineres ativos rodando no docker
	- Passando a flag -a, eu vejo todos os containers, estejam eles ativos ou não
- `docker container run -ti ubuntu` - Executa um container com a flag -ti, que promove um terminal com interatividade diretamente com o conteiner ( ubuntu é o conteiner que estamos executando nesse momento )
	- Outro exemplo: `docker container run -ti hello-world` - Dá pull na lib de hello-world do docker, e manda uma mensagem de hello world
	- Quando eu passo a flag ti, eu passo a interagir diretamente com o container, como pode ver no print acima, o usuário e a identificação do terminal mudaram
	- Para sair de um container matando o processo principal ( consequentemente encerrando o container ), basta dar ctrl+d ou executar o exit
	- Caso queira sair sem encerrar o processo principal, basta executar ctrl+p+q
	- Não podemos fazer conexão com a flag -ti em um container que o processo principal não é um bash, pois vamos ficar presos em um processo sem ter como interagir com ele, e se sairmos nós matamos o conteiner.
		- Para rodarmos processos assim, como um web server ([[nginx]], [[apache]]), podemos rodar esses containers com a flag -d de daemon ( ou detached )
	- Dá para setar limite de memória e outros parâmetros na hora que se cria um container, como por exemplo: `docker container run -d -m 128M nginx`, criando um container para o nginx com limite de 128MB, posso também passar o `--cpus 1`, para especificar quantos cores do processador quero usar.
- `docker version` - Mostra os metadados da versão atual do docker
- `docker container attach iddocontainerounome` - Anexa o processo principal do container em específico ao seu bash
- `docker container exec -ti iddocontainer ls /` - Serve para rodar comandos dentro de um container que roda como daemon
- `docker container stop iddocontainer` - Encerra a execução do container
- `docker container start iddocontainer` - Starta o container
- `docker container restart iddocontainer` - Restarta o container
- `docker container inspect iddocontainer` - Traz todas as informações do container em específico
- `docker container pause iddocontainer` - Pausa o processo no container
- `docker container unpause iddocontainer` - Volta a execução
- `docker container rm iddocontainer` - Remove um container da lista
- `docker container update` - Atualizo as definições de um container
	- Exemplo: `docker container update --cpus 0.2 iddocontainer`

  
#### Como funciona o docker container hello-world?
- O docker client contata o Docker daemon
- O Docker daemon dá pull para a imagem disponível do container no Docker Hub
- Docker Daemon cria um novo container a partir dessa imagem que pedimos que executasse
- O Docker Daemon mostra a saída ao Docker Client e printa no terminal.

#### Rodando o nginx
- `docker container run -d nginx` - Roda o container do nginx em modo detached
- `docker container ls` - Visualizar os containers
- `docker container stats` - Serve para visualizar os recursos que são utilizados pelo container.
- `docker container inspect iddocontainer` - inspecionar o container pra pegar o ip do nginx
- `curl ip` - Você conseguirá visualizar a página html do nginx pelo ip do container


### Sobre Volumes

- Criar volumes no docker
- Primeiro temos que entender que, ao encerrarmos um container, tudo que estava nele morre, inclusive a aplicação e os dados que estão transitando nesta aplicação.
- Um volume no Docker seria uma forma de persistir a informação que queremos persistir mesmo após o encerramento do container.

### Como criar um volume?
- Você não necessariamente "cria volume", lembre-se, um container é apenas um alocamento de processamento e memória dentro do sistema operacional HOST, portanto, criar um volume é justamente alocar uma parte de armazenamento do HOST, assim como a memória e o processamento.
- `mkdir /opt/teste` : criando um diretório /teste no HOST
- Formas de alocação e criação de volumes:
	- Tipo bind: Eu já tenho um diretório que será montado 
	- Tipo volume: É o padrão, quando não é feita a gestão o diretório criado tem nome aleatório
- `docker container run -ti --mount type=bind,src=/opt/teste,dst=/teste debian` : Esse comando está querendo rodar um container no modo daemon e também montar um volume do tipo bind no diretório /teste dentro do container e os dados do container serão trazidos para /opt/teste no HOST
	- Basicamente, eu faço com que o diretório do container `/teste` espelhe em um diretório do HOST (`/opt/teste`) todos os dados criados.