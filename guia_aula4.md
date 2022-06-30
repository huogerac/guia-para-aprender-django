# Passoa a passo - Aula 4

Este guia tem a intenção de te auxiliar a criar seu primeiro projeto Django a partir da aula que tivemos no Busertech dia 30/06 sobre este framework.

Para melhor entendimento foi feita a distinção entre: "sugestão de nome" e "boa prática". Isso porque idealmente todos deveriam ter o mesmo projeto e ter os nomes iguais vai facilitar _e muito_ o entendimento e ajuda que somos capazes de oferecer uns aos outros.
Em alguns momentos do tutorial, quando estivermos tratando de arquivos de mesmo nome, será incluído junto o nome do diretório a que este arquivo pertence.
Exemplo: "_django_cursos/urls.py_" != "_cursos/urls.py_"

```
Comandos úteis ao longo do projeto:

Para rodar o server do Django: ./manage.py runserver
```

## 1 - Iniciando um projeto em Django

- Criar um novo repositório no github: _sugestão de nome= "django_cursos"_
- Adicionar o readme e o .gitigonore.
- Clonar o repositório na sua pasta local de Django.
- Navegar até a pasta "Django Cursos" e cria um virtualenv dentro dela: **_sugestão de nome= ".venv"_**
- Ativar o virtualenv usando o comando: `source .venv/bin/activate`
  - Verifique se o virtualenv está ativo através do (.venv) que deve estar aparecendo no começo de sua linha no terminal.
- Instalar o Django usando o comando: `pip install Django`
- Verificar os pacotes instalados usando o comando: `pip freeze`
  - Perceba que haverão outros pacotes instalados além do próprio Django.
- Iniciar o projeto Django usando o comando: `django-admin startproject .`
  - O ponto `.` no fim da linha de comando serve para que o django seja instalado na pasta em que você se encontra com seu terminal, portanto, tenha cuidado e certifique-se de estar no diretório correto.
- Executar o programa usando o comando: `./manage.py runserver`
- Incluir as alterações no git usando o comando: `git add .`
- Criar um commit usando o comando: `git commit -m "mensagem que você deseja inserir"`
  - Boa prática: dar o nome de `"first commit"` ao primeiro commit que você fizer.
- Dar o push para o repositório do GitHub: `git push`
  - Caso aja alguma complicação no que se refere a git, o próprio git costuma dar boas orientações para a resolução.

### 2 - Criando uma app em nosso projeto

- Criar uma app usando o comando: `./manage.py startapp cursos`
  - Boa prática: O nome da app ser dado no plural, o terceiro valor é o nome da pasta.
- Navegar até a raíz do projeto e abri-la na sua IDE.
  - Se for o vscode, use o comando: `code .`
  - Boa prática: use o comando: `pip freeze > requirements.txt`
    - Esse comando "tira uma foto do ambiente virtual" naquele momento, é interessante fazer isso depois de instalar todas as dependências necessárias para o projeto. Dessa forma todo programador, inclusive o você do futuro, sabe exatamente o que é necessário e de uma forma muito simples.
- Pelo terminal da sua IDE navegue até o diretório **_sugestão de nome= "cursos"_** e crie uma pasta chamada **_sugestão de nome= "templates"_**.
- Em sua pasta templates crie uma pasta **_sugestão de nome= "cursos"_** e dentro dela um arquivo html.
  - De fato é um pouco confusa a repetição de nomes, mas essa organização traz muitos benefícios em projetos de maior tamanho onde dentro de uma app você terá seus respectivos templates e dentro dela você irá querer armazenar os arquivos html referentes, como por exemplo:
    - Na app "cursos" você terá seus templates. Na pasta templates você terá uma pasta "cursos" para armazenar apenas os templates estritamente relacionados aos cursos. Vamos supor que dentro da templates também exista a pasta "transacoes_bancarias" para guardar apenas as templates estritamente relacionadas a esse assunto, e por aí vai.
- No seu diretório "cursos" é necessário criar um arquivo chamado **urls.py** para atribuir as rotas deste app.
  - Perceba que existe um arquivo de mesmo nome na sua pasta de projeto ("django_cursos").
- Copie do arquivo o conteúdo do arquivo **urls.py** que está dentro do diretório _django_cursos_ ("_django_cursos/urls.py_") e cole o conteúdo dentro do **urls.py** ("_cursos/urls.py_") que você acabou de criar.
- Em seu arquivo **views.py** crie uma função insira o código:

```
from django.shortcuts import render

def pagina_inicial(request):
    return render(request, "/nome_da_app/<nome_do_seu_arquivo.html>")
```

Importante entender que _nome_da_app_ e _nome_do_seu_arquivo.html_, neste caso, são equivalentes a cursos e um arquivo ".html" que ainda iremos criar.

- Rode seu projeto e tente acessar a url que você pensou em criar em seu projeto, se você seguiu corretamente o tutorial até aqui, você receberá um erro.
- É necessário importar o seu arquivo "_cursos/urls.py_" em seu "_django_cursos/urls.py_" adicionando o comando: `path('cursos/', include('cursos.urls'))`
- Em seu arquivo _django_cursos/settings.py_ inclua o nome da sua app no campo:

```
INSTALLED_APPS = [
    ...,
    ...,
    ...,
    'cursos',
]
```

### 3 - Adicionando estilos às nossas páginas

- Dentro da sua app cursos crie uma pasta _static_
- Dentro de sua pasta _static_ crie uma outra pasta _cursos_ e dentro dela crie uma pasta chamada _css_
  - Nesta situação a repetição de nomes segue o mesmo conceito explicado anteriormente.
- É dentro desta pasta que iremos adicionar nossos arquivos ".css"
- Dentro da sua pasta _cursos_ crie uma outra pasta chamada: **_sugestão de nome= "imagens"_**
- É dentro desta pasta que iremos adicionar as imagens do nosso projeto.
- Em sua página "_templates/cursos_" crie um arquivo de qualquer nome, com extensão ".html".
- Em **nome_do_seu_arquivo.html** adicione as linhas de código destacadas:

```
{% load static %}
...
...
...
...
<link rel ....... href="{% static 'cursos/css/styles.css' %}">
```

- A partir deste momento os arquivos ".css" já estão sendo reconhecidos pelo Django e por consequência, pelo navegador.

### 4 - Navegando pelas páginas em nosso projeto Django

- Um link leva o usuário para uma página diferente, portanto se certifique de criar a página a que o usuário deve chegar depois de sua interação com o site.
- Dentro de templates, crie o **exemplo.html** que vai ser exibido ao usuário.
- No exemplo a seguir vamos implementar a função de listar cursos do nosso site.
- Em seu arquivo **views.py** crie:

```
def listar_cursos(request):
    return render(request, 'exemplo.html')
```

- E em seguida vá em seu arquivo "_cursos/urls.py_" e acrescente a linha:
  `path('listar/meus-cursos', views.listar_cursos, name='cursos.listar.tudo')`
  - Boa prática: name normalmente é dado considerando 'nome.funcionalidade'.
- Em seguida dentro da anchor (tag de html), "< a >" que você quiser colocar o link, insira `{% url 'cursos.listar.tudo' %}`, como valor de `href`.
- Ex:
  `<a href="{% url 'cursos.listar.tudo' %}">`
  - Perceba que o href recebe (em jinja) url e o name dado a url.

### 5 - Templates

#### _ESTUDE LINGUAGEM DE TEMPLATES DO DJANGO:_ <a href="https://imasters.com.br/desenvolvimento/conhecendo-o-jinja2-um-mecanismo-para-templates-no-flask">JINJA</a>

- Esta parte do tutorial é um pouco mais complicada porque estaremos em boa parte do tempo falando de uma linguagem que não conhecíamos até então: Jinja
- A grande sacada desta parte do guia é que construiremos um arquivo base de html. Este arquivo irá conter todos os conteúdos que são exibidos em mais de um lugar. O objetivo com essa ideia é que a gente possa reutilizar com mais facilidade pedaços de código que já construímos além de ter arquivos com legibilidade muito maior por terem menos coisas escritas, dado que várias partes não serão reescritas.
- Em sua pasta _templates_ crie um arquivo **base.html** e inclua nela os blocos de código que são comuns a outros arquivos de html.
- Insira o código a seguir no arquivo na parte da página em que varia.

```
{% block conteudo %}
<h2> O que está aqui dentro será alterado ao utilizar o bloco conteúdo em outro arquivo html. </h2>
{%endblock conteudo%}
```

- No arquivo que vai utilizar o conteúdo da base é necessário incluir o seguinte código: `{% extends 'cursos/base.html'%}`
- E em seguida colocar as partes que variam dentro da estrutura de mesmo nome `{%block conteudo%}{%endblock conteudo%}`
- O arquivo vai ficar assim:

```
{%extends 'cursos/base.html'%} {%block conteudo%}
alterei aqui
inseri tag html
inseri outra tag html
.
.
.
{%endblock conteudo%}
```

- Onde "conteudo" é o nome do block existente no arquivo **base.html** e a presença deste bloco em outro arquivo irá substituir o que existe dentro deste bloco pelos novos valores passados.
- Ao passo que caso queiramos excluir a exibição de um bloco devemos importá-lo e alterar seu conteúdo por espaços em branco.
  - Exemplo:
  ```
  {%extends 'cursos/base.html'%} {%block conteudo%}
  {%endblock conteudo%}
  ```

### 6 - Docker

- Rode `netstat -nlt` em sua máquina
- Encontre a linha com final :5432
- Para parar o processo do postgresql na máquina: `sudo service postgresql stop`
- O uso do docker é tem 3 frentes.
- 1 - A utilização do postgresql sem precisar instalar localmente.
- 2 - Transformar meu projeto Djando também em um container docker
- 3 - Publicar seu projeto usando docker

- A princípio iremos focar na primeira forma de uso, mas isso é conteúdo para a próxima aula. Hoje nós apenas vimos a estrutura de um compose e como colocá-lo no ar.
- Para subir o docker, o comando é `docker-compose up`

### 7 - Precisa instalar um projeto Django na sua máquina ?

- Na pasta que irá receber o projeto, com seu ambiente virtual ativo, use o comando: `pip install -r requirements.txt` e assim todas as dependências do projeto serão instaladas.

````
Legendas do guia:

- Para um bloco de código use três crases dos dois lados:  ``` bloco de código aqui ```
- Para uma linha de código use: `insira o código aqui`
- Para referenciar um arquivo use: **nome_do_arquivo**
- Para referenciar um caminho use: "*diretorio/arquivo*"
- Para criar um link use a tag anchor do html: <a href="insiraaquiolink.com.br" >Insira aqui o conteúdo</a>
````
