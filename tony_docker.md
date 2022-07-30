# Passo a passo - Aula 5

Este guia tem a intenção de te auxiliar a "dockerizar" o seu projeto Django e fazer deploy do mesmo na AWS a partir da aula que tivemos no Busertech dia 01/07 sobre essa tecnologia.

## **Imagens** são diferentes de **Containers**

<p>Essa afirmação pode parecer simples tendo em vista que coisas que têm nomes diferentes frequentemente não são iguais. Porém, essa diferenciação se faz ainda mais necessária quando o assunto são <strong>imagens</strong> e <strong>containers</strong> em docker.</p>
<p>Quando falamos de <strong>imagens</strong> em docker estamos nos referindo a ao estado primordial que um projeto pode assumir no contexto docker. Isso porquê a <strong>imagem</strong> é o que dá origem ao <strong>container</strong>.</p>
<p>Ao longo deste guia faremos a "dockerização" de projetos e uma dessas etapas é tratar estes projetos em formas <strong>imagens</strong>, que são comumente encontrados no <a href='https://hub.docker.com/'>Docker Hub</a></p>

## Um **container** é uma lasanha ?

<p>Sim.</p>
<img src='https://media.istockphoto.com/photos/piece-of-baked-lasagna-closeup-isolated-on-white-background-picture-id1316558471?b=1&k=20&m=1316558471&s=170667a&w=0&h=6pbAWxtmUPyhVHWpUJMT8atTX5MgCIWVbzufk1P9WOM=' alt='Lasagna' width='400'>
<p>Quando o docker faz ou recebe qualquer alteração em seu container o que ele faz é: considerar todo o conteúdo, e não executar todo o ciclo de transformação no que se manteve igual nos procedimentos que lhe forem comandados durante a dockerização do projeto.</p>

#### Mas como essa atualização é feita ?

<p>Para responder essa pergunta precisamos entender como está disposta a organização do nosso projeto por todo o caminho desde o diretório em nossa máquina até estar online através de uma máquina AWS</p>
<p>
Inicialmente a estrutura seria:

Repositório local >>>>**t1**>>>> Docker Hub >>>>**t2**>>>> AWS

Perceba que entre esses 3 ambientes existem duas transferências que apelidei de **t1** e **t2**. Isso porque em cada ocasião o docker é a tecnologia que fará essa transferências para nós, mas elas têm particularidades, mas vamos a resposta enfim. Ao criar um projeto e criar uma imagem docker dele o próprio docker reconhecerá que todo o corpo do projeto é novo e portanto transferirá tudo na t1 sem muito critério. Esse container receberá o comando `docker push` e assim nosso container estará em nosso Docker Hub e o mesmo tipo de situação acontecerá em **t2** exceto que t2 será executada a partir do comando `docker pull`, mas chegaremos lá.

</p>
<p>Uma das ocasiões em que o docker se sobresai é quando você precisa atualizar um container que já foi deployado. Isso porquê como já dito anteriormente, ao fazer novas transferências o docker vai olhar somente para o que de fato foi alterado, fazendo com que assim as suas transferências abram bem menos brechas para erros, sejam bem mais velozes e por consequência mais eficientes.</p>
<p>"Tá, mas e a parte da lasanha ?" você deve estar se perguntando. Simples. Quando vamos montar uma lasanha consideramos que cada camada recebe alguns componentes como molho, massa e recheio. Mas a construção da lasanha como um todo depende das camadas anteriores que servem como base e o mesmo vale para o nosso projeto que se apoia em todas as outras transferências anteriores que já fizemos e assim como para termos uma "lasanha alta" precisamos contar com o que já foi construído até o momento o mesmo vale para o projeto. Com o acréscimo de que o docker é esperto o bastante para trabalhar mais apenas o que é novidade no container.</p>

```
Tecnologias estudadas nessa aula:

1. Docker
2. Postgresql | Dbeaver
3. AWS
```

```
Objetivos:

- Aprender a utilizar o docker e se familiarizar com ele.
- Usar imagens externas no docker e rodar localmente.
- Dockerizar nosso projeto Django e subir na AWS.
```

Comandos úteis ao longo do projeto:

```
Para instalar o docker:
    1. sudo apt-get remove docker docker.io containerd runc
    2. sudo apt update
    3. sudo apt install -y apt-transport-https ca-certificates curl software-properties-common curl -fsSL https://download.docker.com/linux/ubuntu/gpg | sudo apt-key add - sudo add-apt-repository "deb[arch=amd64] https://download.docker.com/linux/ubuntu focal stable"
    4. apt-cache policy docker-ce
    5. sudo apt-get install docker-ce docker-ce-cli containerd.io docker-compose
Para verificar a versão instalada do docker:
    - docker -v
Para verificar a versão instalada do docker-compose:
    - docker-compose -v
Comandos referentes ao usuário (PERGUNTAR):
    1. sudo usermod -aG docker ${USER}
    2. su - ${USER}
    3. groups
    4. sudo usermod -aG <insiraaquiseuusername>
Para verificar se a instalação foi realizada corretamente:
    - docker run hello_world
```

Caso o docker responda que não foi capaz de encontrar a imagem "hello_world" localmente, parabéns, seu docker foi instalado corretamente. Caso contrário, tente novamente a sequência de comandos, se o problema persistir, busque ajuda.

## 1 - Iniciando um projeto em Docker

- Conheça suas imagens, use o comando: `docker images`
- Baixe o mais novo ubuntu usando o comando: `docker pull ubuntu`
- Rode o `docker images` novamente e perceba que agora ele lista também a imagem ubuntu que baixamos no último comando.
- Rode o `docker ps` para listar todos os containers que estão rodando no momento.
- Rode o `docker ps -a` para visualizar todos os containers já rodados no seu docker, inclusive os que já faleceram.
- Rode `docker rm <insira aqui o nome do container> ou <insira aqui o id do container>` para apagar um container
- Rode `docker rmi <insira o nome da imagem>` para apagar uma imagem.
- Rode `docker run -it ubuntu bash` para rodar um bash a partir da imagem ubuntu.
- A partir deste momento seu comandos de docker não irão funcionar, já que você está em um terminal bash.
- Use `exit` para encerrar o bash atual e por consequência encerrar o container que executava o ubuntu.
  - **Explicação**
    - Isso acontece porque toda vez que o docker roda uma imagem ele cria um container a partir daquela imagem. Porém, a execução desse container só acontece enquanto ele executar alguma atividade. Caso não seja incluída a partícula `-it` que significa "aguardar interação com o usuário", ele vai rodar e encerrar o container em seguida, caso este não execute nada em particular.
  - Tente abrir um terminal novo e rodar um `docker ps`
  - Caso seu `docker ps` não funcione neste novo terminal use o comando:
  ```
  sudo setfacl --modify user:nomedouser:rw /var/run/docker.sock
  ```
  - Nós obtivemos esse comando a partir do <a href ="www.stackoverflow.com">Stack Overflow</a>, então caso tenha algum erro que não está coberto nesta documentação, crie o hábito de visitar esse site.
- Agora, com dois terminais abertos, em um rode novamente o `docker run -it ubuntu bash` e no segundo terminal rode um `docker ps` para ver no segundo terminal a execução do bash presente no primeiro terminal.
- Para matar seu processo, em seu segundo terminal, rode um `docker kill <insira o nome do container>`
- Perceba que automaticamente seu primeiro terminal retornará ao estado normal e sairá do bash em que estava anteriormente.
- Entre no <a href="https://hub.docker.com/">Docker Hub</a> e crie uma conta.
- Em seu terminal rode `docker login` para conectar sua conta docker com seu repositório local
- Procure a imagem do <a href ="https://hub.docker.com/_/postgres?tab=tags">Postgresql</a>
- Em seu terminal rode `docker pull postgres:10-alpine`
- Rode um `docker ps` para perceber que a imagem do postgres foi adicionada à sua lista.
- Para inicializar o postgres pelo docker rode o comando:

```
docker run -e POSTGRES_USER=app -e POSTGRES_PASSWORD=app -p 5432:5432 postgres:10-alpine
```

- **Explicação**:
  - Este comando seta alguns valores para as variáveis de ambiente presentes na imagem do postgresql que visitamos no dockerhub. Caso haja dúvidas, volte e releia a documentação da mesma. Os valores são "app" e as variáveis são o `POSTGRES_USER` e `POSTGRES_PASSWORD`.
  - Perceba que antes dos nomes das variáveis é passada uma partícula `-e` que serve para setar variáveis de ambiente. Justamente por isso ela precede os nomes=valor
  - Em seguida, antes das portas passamos a partícula `-p` que significa "Publish" ou "Expose port". O que estamos fazendo neste momento é dizendo que a nossa porta 5432 (que é onde o postgres roda seu processo) deve ser exposta e conectada com a porta 5432 do container docker. Desse jeito conseguimos nos conectar com o processo do container docker e interagir com ele em um terminal na nossa máquina.
  - Por fim inserimos o `nome_da_imagem:versão_desejada`
- Se seu terminal retornou um `UTC [1] LOG: database system is ready to accept connections`, então parabéns, deu tudo certo!
- Senão, caso você já possua um postgres rodando, precisará dar um `sudo service postgresql stop` para encerrar o processo referente ao postgres que já estará aberto e em seguida rode o comando anterior.
- **TAKE A BREAK**
  - Pode ser que tudo o que tenha feito até aqui tenha sido novo e tem bastante coisa que fez sem necessariamente entender o porquê. Pensando nisso, este pode ser um bom momento para beber uma água e respirar por uns 5min.
- Agora vamos nos conectar com o banco postgresl que subimos pelo docker. Para otimizarmos nosso tempo vamos usar um cliente de banco de dados, assim será mais fácil criar a conexão. O cliente escolhido para este tutorial é o _Dbeaver_.
- Abra seu dbeaver e crie uma conexão com banco de dados e preencha com "app" os campos _database_, _username_ e _password_.
  - EXPLICAÇÃO:
    - <p> Lembra das variáveis de ambiente que passamos ? O docker criou um banco postgresql de nome="app", username="app" e password="app". Conforme nós passamos no comando de inicialização.</p>
- Crie uma tabela com uma coluna dentro e em seguida acrescente um dado na tabela.
- Em seguida rode um `select * from newtable n` para visualizar o dado que você incluiu.
- Volte no seu terminal e derrube o container do banco. Em seguida suba o banco novamente.
- Perceba que sua tabela já não existe mais.
- Em seu terminal rode o comando:

```
docker run -e POSTGRES_USER=app -e POSTGRES_PASSWORD=app -p 5432:5432
-v /home/seuusuario/tmppostgres:/var/lib/postgresql/data postgres:10-alpine
```

- Agora em seu Dbeaver crie uma tabela e uma coluna novamente e preencha com algum dado.
- Derrube seu docker e suba de novo a aplicação do banco.
- Em seguida entre em seu banco pelo Dbeaver e perceba que seus dados estão salvos. Parabéns! A partir de agora seus dados persistem.
- Mas não acredite em mim! Confira.
  - Em seu terminal rode `cd ~` e em seguida rode o comando `ll`
  - Perceba que dentre muitas pastas _provavelmente_ só existe uma que foi criada pelo "root" e não pelo seu usuário padrão.
  - Rode `cd tmppostgres` e tenha sua permissão negada. Isso porque a pasta foi criada pelo usuário root e portanto só pode ser acessada pelo mesmo.
  - Sendo assim use o comando `sudo su` e insira sua senha.
  - Agora sim podemos rodar `cd tmppostgres` e lá dentro estão todas as informações que foram criadas pelo container.
  - Qual a beleza da coisa ? Mate o seu processo do docker e todas as atualizações permanecerão salvas. Agora sim você pode concluir por conta própria, que seus dados persistem!
- **Explicação**
  - Vamos analisar a anatomia deste comando. Até a parte das portas ele é exatamente a mesma coisa que rodamos anteriormente.
    - A primeira partícula passada após as portas é o `-v` ou `--volume` que faz referência ao volume.
    - Isso porquê volumes são diretórios de um container docker que são externos ao container. Eles são muito usados para uma finalidade: persistir dados.
    - Vamos relembrar como um container docker funciona: Ele é criado, executa o que tem para ser executado dentro dele e por padrão é encerrado. Portanto, se nós derrubamos nosso container rodando o postgres e subirmos de novo, vemos que os dados que inserimos na primeira execução **não são mantidos para a segunda execução**.
    - Como volumes são diretórios externos ao container, é possível guardar as alterações criadas na primeira execução em uma máquina que não será encerrada com o fim do projeto, como por exemplo, a nossa máquina pessoal. E é exatamente isso que fizemos com esse comando, passamos o -v e em seguida o endereço em nossa máquina que irá receber tudo o que for gerado de alteração durante a execução do container.
    - Uma vez que este container for encerrado e seu processo perdido, nós teremos armazenado tudo em nossa máquina e quando subirmos outro container, basta conectar com esse caminho e pronto.
    - Agora não importa em qual processo um dado foi criado, ele será persistido.

## 2 - Vamos brincar com uma imagem do DockerHub ?

- Neste momento iremos puxar uma imagem do DockerHub e fazer o rodá-la localmente. A imagem escolhida é a Saleor que é um e-commerce.
- Visite o <a href='https://github.com/saleor/saleor'>Saleor</a> e também o <a href='https://hub.docker.com/r/saleordev/saleor'>DockerHub do Saleor</a>
- E faça o `docker pull` do caminho indicado na página do <a href='https://hub.docker.com/r/saleordev/saleor'>DockerHub Saleor</a>
- Em seguida rode `docker run -it saleordev/saleor bash`
- Rode `ls --color -lh` e agora você tem a capacidade de visualizar os arquivos deste projeto django.
- Rode `exit`
- Agora, somos capazes de rodar o projeto Django como se estivesse em nossa máquina local, porém, não é o que faremos neste momento.
- Rode o comando `docker run -it saleordev/saleor`
- Agora você está rodando o projeto, mas, o que está acontecendo ?
- A resposta para essa pergunta está em visitar a <a href='docs.saleor.io'>documentação</a>.
- A ideia agora é proteger a sua secret key.
  - Quando o django cria um projeto ele gera uma secret key porque este campo não deve ficar vazio. Porém, não devemos deixar esta informação sensível tão fácil de encontrar em nosso código. É por isso que iremos criar uma rede para nos conectarmos sem ter que deixar a secret key transparente.
- Criaremos a rede através deste comando: `docker network create netsaleor`
- Em seguida o `docker network list`
  - Caso apareça uma lista com o nome 'netsaleor'. Parabéns, você criou uma rede!
- Em seu terminal rode o:

```
docker run --rm -d --name postgres -e POSTGRES_USER=app -e POSTGRES_PASSWORD=app --net netsaleor \
-v /home/seuusuario/tmppostgres:/var/lib/postgresql/data postgres:10-alpine
```

- **Explicação**

  - _--rm_ : Comando para remover (rm) automaticamente um container quando ele deixar de existir.
  - _-d_ : Comando para desacoplar (detach) o container e portanto rodá-lo em segundo plano sem printar suas saídas.
  - _--name_ : Comando para passar um nome (name) para o container.
  - _-e_ : Comando para acessar as variaveís de ambiente (environment).

- E em seguida rode o `docker logs postgres` para visualizar os logs do container de nome _postgres_ que criamos no último container.
- Agora rode o seguinte comando:

```
docker run -d --rm --name=saleor -p 8000:8000 --net netsaleor -e DATABASE_URL=postgres://app:app@db:5432/app -e SECRET_KEY=hjagdsjyatqt83652oiygjyrqi36 --link postgres:db saleordev/saleor
```

- Verifique o <a href='http://localhost:8000/'>localhost:8000</a> e veja: a aplicação Saleor está rodando!
- Rodando tão bem, que está fazendo o que se espera: dando um erro! <img src='https://bot.to/wp-content/uploads/2020/10/sadface_5f7f351b46a7b.png' width='30'>
- Vamos corrigir esse problema:
- Rode o `docker exec -it saleor bash` para criar um novo processo dentro de um container que já está rodando. E este novo processo será um bash.
- E rode um `ps -ef` para ver todos os processos disponíveis naquelea máquina.
- Rode o comando `env` para verificar todas as variáveis de ambiente disponíveis desta máquina.
- Rode um `./manage.py migrate` para criar as tabelas que não existiam até então (cuja ausência era a razão do erro que encontramos no browser.)
- Em seu browser atualize sua aba <a href='http://localhost:8000/'>localhost:8000</a> e voilà, a aplicação está rodando, sem erros.
- Para visualizar a área de admin rode o comando: `./manage.py createsuperuser` e insira a seguir o nome de usuário e a senha.
- Depois disso entre no <a href='http://localhost:8000/admin'>localhost:8000/admin</a> e insira as suas credenciais.

## 3 - Vamos deployar nosso projeto!

- Navegue pelo terminal até sua pasta root do projeto desejado.
- Crie um arquivo chamado _Dockerfile_.
- Neste arquivo insira:

```
FROM python:3.8.10
WORKDIR /app
COPY requirements.txt ./
RUN pip install -r requirements.txt
COPY . /app
CMD ./manage.py runserver 0.0.0.0:8000
```

- Garanta que salvou o arquivo.
- E em seguida rode em um terminal o comando `docker build -t nome_do_seu_projeto . ` para buildar a sua imagem.
  - Se o Django do seu projeto está em uma versão menor que 4, isto deve ter funcionado sem problemas.
  - Senão, coloque o python mais atual disponível no momento de sua tentativa no lugar da nossa versão "3.8.10".
- Em seguida, rode o comando para executar a sua imagem e criar um container a partir dela:

```
docker run -it -p 8000:8000 nome_da_sua_imagem ./manage.py runserver 0.0.0.0:8000
```

ou

```
docker run -it -p 8000:8000 nome_da_sua_imagem ./manage.py
```

- **Explicação**
  - _0.0.0.0:8000_ significa que estamos expondo essa porta para o mundo e agora ela fica acessível para qualquer um na internet que inserir no browser a url(ip_da_máquina_que_serve:8000)
  - Para esse teste é necessário adicionar no **settings.py** o ip da máquina que vai acessar externamente aos "Allowed Hosts".
- Agora vamos criar um novo repositório no seu DockerHub.
- Rode o comando: `docker tag "nome_do_projeto:latest" username_do_dockerhub/nome_repositorio`
- E em seguida rode o comando `docker push username_do_dockerhub/nome_repositorio`
- A resposta do terminal deve ter sido várias mensagens de "_pushed_"
- A partir deste momento seu projeto está oficialmente dockerizado e pronto para ser servido por qualquer serviço.

## 4 - O último inimigo: AWS.

- Apesar de a AWS terem vários serviços, agora vamos nos concentrar no EC2.
- Aqui nós fomos privilegiados pelo professor que liberou máquinas para a turma inteira então não iremos cobrir esta parte aqui no guia.
- Em sua máquina da AWS rode o comando `sudo apt install nginx`
- E em seguida instale o _docker_
- Depois de _muitas_ configurações (**MUITAS MESMO**), é chegada a hora de adicionar a nossa chave SSH às máquinas criadas lá na AWS.
- Através do seguinte comando:

```
ssh nomedousuario@nomedoprojeto.fimdodominio.com
```

- Em seguida traga a sua imagem do DockerHub para a máquina da AWS com o comando: `docker pull nomedoprojeto`
- Depois rode o projeto baixado com o comando: `docker run -d -p 8000:8000 --name nomedoprojeto`
- A essa altura seu projeto já deveria estar no ar, verifique isso com os comandos `docker ps` e `docker logs -f nomedoprojeto`. Eles devem mostrar a exibição do seu projeto.
- O último passo é acrescentar este domínio ao grupo de segurança da AWS para permitir que ips externos possam acessá-lo.
- Insira no browser a url que você atribuiu ao projeto e perceba o que o browser te retorna. Se for um erro relacionado ao django, parabéns, você falhou com sucesso!
- Neste momento o que acontece é que o nginx precisa ser configurado para fazer o seu papel: gerenciar as urls e atribuir às portas corretas.
- Em seu computador crie um arquivo _nome.conf_ no caminho: _/etc/nginx/sites-enabled/nome.conf_ e este arquivo deve ter o seguinte conteúdo:

```
server {
    listen       80;
    server_name  nomedoprojeto.fimdodominio.com;
    location / {
        proxy_pass http://localhost:8001/;
	include proxy_params;
    }
}
```

- Perceba que neste caso a porta escolhida foi a 8001.

#### Sugestão - Redeploy:

- Em sua máquina da AWS crie um script _deploy.sh_ na raíz do seu projeto com o bloco de comandos:

```
docker build -t username_do_dockerhub/nome_repositorio .
docker login
docker push username_do_dockerhub/nome_repositorio
ssh ubuntu@nome_repositorio.fimdodominio.com.br ./deploy.sh
```

### FAQ

- Perguntas:
  - Qual a diferença de um `docker rm` e um `docker kill` ?
    - `docker rm` **remove** um container que já está morto.
    - `docker kill` **mata** um container que está ativo.
  - Consigo ver as tabelas criadas através do Dbeaver ?
    - Sim, se tiver rodado o comando de criação com _-p_, mesmo sendo derrubado ele vai com os dados escritos.

### Referências

- <a href='https://evolutio.io/curso/deploy_profissa'>Evolutio - Deploy Profissa</a>
- <a href='https://docs.google.com/document/d/17lb15xL53529LRMvlb1rvwYdmy9Vj29Pp-ydli5Mwxg/edit'>Documentação Fantástica do Tony</a>
- <a href='https://docs.docker.com/engine/reference/commandline/run/'>Docker Documentação</a>
- <a href='https://www.linuxtips.io/blogs/novidades/entendendo-volumes-no-docker'>Docker - Volumes</a>
