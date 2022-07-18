# Guia para aprender Django

![Imagem do filme do Tarantino, Django Livre](./assets/django-o-filme.png)

### Objetivos

- 👉 Aprender misturando prática 👾 e teoria 📚
- 👉 Seguir pequenos passos (Baby Steps 👶)
- 👉 Melhorar este guia com sua ajuda (sua colaboração e participação é fundamental)

### ALERTA VERMELHO 🚨

- LEIA TUDO, melhor ir mais devagar com atenção e entedimento ao invés de rápido sem saber o que está acontecendo 😎
- DIGITE tudo, tudo mesmo! NUNCA copie o `comando` ou `código` deste tutorial
- **CTRL + C** & **CTRL + V**, vão fazer você esquecer tudo em 42 minutos e além disto vai ficar sonhando com Django o Filme! 🎞 ou seja, perdeu seu tempo! 🤡
- NUNCA PULE os passos, acredita que tem algo desnecessário (e pode ter 😔), registre sua sugestão nas [Issues 🐞](https://github.com/huogerac/guia-para-aprender-django/issues/) da parte correspondente!
- NÃO ESQUEÇA! Django é um `Framework` (O que❓) e Python sua fundação, desta maneira, quanto mais você souber desta incrível linguagem 🐍, mais fácil você vai entender o Django Web Framework

### Iniciando

É muito simples para iniciar este tutorial, **NÃO PRECISAR FAZER FORK!!!**
A melhor forma é simplesmente seguir os arquivos de texto no formato [Markdown](https://www.markdownguide.org/cheat-sheet/) diretamente neste repositório! Assim você vai garantir que sempre está lendo a última atualização (E vai ser diária)

### Pré-Requisitos

- 🐍 Python 3 instalado (Inicialmente não vamos se preocupar com a versão)
- 🖥️ Um terminal Linux (que já vem por padrão em qualquer distribuição Linux 🤘 ou pode ser instalado facilmente no Windows via WSL2)
- Um editor de texto instalado, pode ser qualquer um da sua preferência

### Legenda

- 🎯 Material complementar ou slides
- 👾 Prática
- 📚 Teoria
- 🐞 Enviar dúvida

### Parte 1) Olá Mundo | Mão na massa 👾

- 👀 Acompanhe a vídeo aula, veja o [guia textual](Parte01-ola-mundo.md) e assim saiba o passo a passo para fazer o primeiro Olá Mundo usando o mais popular framework web no mundo do Python
- ▶️ Replique cada passo e faça exatamente o mesmo Olá mundo rodar na sua máquina
- 📝 Faça um guia com TODOS os passos necessários, desta forma você poderá revisar toda vez que for iniciar um projeto Django.
- 🐞 Alguma coisa não ficou clara? Alguma dúvida ou achou algo estranho ou muito mágico? Faça um comentário [AQUI 💬](https://github.com/huogerac/guia-para-aprender-django/issues/1)

### Parte 2) Entendendo um pouco da Web | Teoria 📚

- 👀 Acompanhe a vídeo aula
- A importancia do `Request/Response` em projetos Web
- Requisição e Resposta (`Request/Response`) em projetos web estático
- Arquitetura (alto nível) Cliente/Servidor (`Client/Server`) também conhecido como Front-end/Back-end
- 🎯 Veja os [slides sobre o Request/Response + Cliente/Servidor](./assets/Web-Request_Response-v1.pdf)
- 🐞 Alguma coisa não ficou clara nesta parte? Alguma dúvida ou achou algo estranho ou muito mágico? Faça um comentário [AQUI 💬](https://github.com/huogerac/guia-para-aprender-django/issues/2)
- **✅ Links úteis...**
- [API em imagens - Tks Fabricio](https://twitter.com/EngineerRabbit/status/1541798162075193345?t=nGI4dWQg8Yg-L45HRF55Mw&s=19)

### Parte 3) Anatomia do Django & Web | Teoria 📚

- Django é **Front-end** e **Back-end** ao mesmo tempo? 🤯 (WTF?)
- A importância da estrutura de projetos no Django
- 🎯 Veja os [slides sobre a Anatomia do Django](./assets/Anatomia-Django-E-Web-v1.pdf)
- 🐞 Alguma coisa não ficou clara nesta parte? Alguma dúvida ou achou algo estranho ou muito mágico? Faça um comentário [AQUI 💬](https://github.com/huogerac/guia-para-aprender-django/issues/3)

### Parte 4) Nosso segundo projeto | Mão na massa 👾👾

- 👀 Acompanhe a vídeo aula
- Qual a diferença entre `project & app`
- Vamos fazer os mesmos passos do [Passo 1)](README.md#parte-1-olá-mundo--mão-na-massa-), mas agora criando uma aplicação para listar uma lista de cursos (explorando apenas componentes Front-end)
- Templates?
- Como usar a linguagem de template para fazer reuso de páginas web? 👌
- Como linkar páginas
- Como importar arquivos CSS & Imagens
- Salvar as dependências instaladas para compartilhar com outros Devs 👌 (a.k.a `requirements.txt`)
- Apaga tudo, e vamos subir (rodar) tudo novamente em minutos? (não é muito difícil ser segundos) - I love you Git 💙 + uns scripts (a.k.a como automatizar processos que executa coisas)
- 🐞 Alguma coisa não ficou clara nesta parte? Alguma dúvida ou achou algo estranho ou muito mágico? Faça um comentário [AQUI 💬](https://github.com/huogerac/guia-para-aprender-django/issues/4)

### Parte 5) Vamos continuar no projeto django_cursos | Mão na massa 👾👾

- 👀 Acompanhe a vídeo aula
- Usar variáveis de ambiente para modificar o settings.py
- Rodar migrações
- Faz sentido usar SQLite? 📈
- Quais Apps 🧩 temos no projeto?
- Admin?
- Criar usuário e logar
- Exibir o usuário logado
- Descobrir os [SQLs gerados pelo Django](https://django-debug-toolbar.readthedocs.io/en/latest/installation.html)
- **✅ Links úteis...**
- [django packages](https://djangopackages.org)
- [django awesome](https://github.com/wsvincent/awesome-django)
- [post sobre algumas apps bem usadas](https://www.crowdbotics.com/blog/best-open-source-django-packages-2020)
- [Código Fonte da AULA](https://github.com/huogerac/django_cursos/tree/aula-05) 👌
- 🐞 Dúvidas ou qualquer informação adicional [AQUI 💬](https://github.com/huogerac/guia-para-aprender-django/issues/5)

### Parte 6) ORM, Models e um pouco do lado do DB | Mão na massa 👾👾

- 👀 Acompanhe a vídeo aula
- Utilizar um DB de produção no nosso Django local (Postgres ao invés SQLite)
- Criar uma tabela usando Model
- DDL com makemigrations
- Gerar script de migração
- Aplicar migração
- Criar dados
- Acessar dados (DML Com MeuModel.objects)
- Adicionando model no Admin
- Null vs Blank
- Unique, slug fields & sobreescrevendo o save()
- **✅ Links úteis...**
- [Código Fonte da AULA](https://github.com/huogerac/django_cursos/tree/aula-06) 👌
- https://docs.djangoproject.com/en/4.0/ref/models/fields/
- 🐞 Dúvidas ou qualquer informação adicional [AQUI 💬](https://github.com/huogerac/guia-para-aprender-django/issues/9)

### Parte 7) Entendendo algumas coisinhas do Python & Django | Teoria 📚

- 👀 Acompanhe a vídeo aula
- Virtualenv?
- Instalar dependências de S.O. (a.k.a `apt install`) e dependências da aplicação Python/Django (a.k.a `pip install`)
- Fiquem tranquilos, logo mais também vamos falar de `Pipenv & Poetry` (Baby steps, lembra?)
- Gerenciar mais de uma versão do Python? (a.k.a `pyenv`)
- 🎯 Veja os [slides sobre Virtualenv & dependencias Python/SO](./assets/Virtualenv-Dependencias-SO-vs-Python.pdf)
- 🐞 Dúvidas ou qualquer informação adicional [AQUI 💬](https://github.com/huogerac/guia-para-aprender-django/issues/10)

### Parte 8) Models continuação | Mão na massa 👾👾

- 👀 Acompanhe a vídeo aula
- Clonar o projeto (aula06), subir banco, subir projeto com as dependencias
- Exibir os dados do Banco no Template (via context da View)
- ForeignKey para relacionamentos 1 para N
- Usando 'related_name' para consulta invertida do ForeignKey: `js.aulas.all()` ou `autor1.cursos.all()`
- Ver os SQLs gerados (usando debug_toolbar)
- Criar tabela Aulas (1 Curso pode ter N Aulas)
- **✅ Links úteis...**
  - [Iniciando a parte de Models](https://docs.djangoproject.com/pt-br/4.0/intro/tutorial02/)
  - [Exemplo de consultas usando Django ORM](https://speakerdeck.com/huogerac/django-orm-vs-sqlalchemy-queries)
  - [Tutorial para setup do projeto em menos de 5min](https://github.com/huogerac/django_cursos#readme)
  - 🐞 Dúvidas ou qualquer informação adicional [AQUI 💬](https://github.com/huogerac/guia-para-aprender-django/issues/11)
- **👾 Tarefas**
  - Se liga nos canais do slack com as dicas & instruções de cada aula
  - Se liga no código completo da [Aula 08](https://github.com/huogerac/django_cursos/tree/aula-08)
  - Se liga **neste repositório guia** e no repositório [django_cursos](https://github.com/huogerac/django_cursos/)
  - Pratique o passo de clonar e rodar o projeto, isto deveria ser feito em poucos minutos!
  - Procure documentação extra sobre os assuntos da aula (Links Úteis & Links abaixo)
  - **NÃO CONSEGUIU FAZER TUDO?** Avisa na hora 🐞, NUNCA deixe para o dia seguinte!

### Parte 9) Models continuação | Mão na massa 👾👾

- 👀 Acompanhe a vídeo aula
- Redirect de `/` para `/cursos` usando RedirectView
- Criar rota `/cursos/pk/aulas/` (url com filtro de PK)
- Criar template que exiba todas aulas de um determinado curso
- App django_extensions (clean_pyc, create_command, generate_secret_key, graph_models)
- Mudar a ordem da listagem de cursos conforme o campo no template
- Páginas de Signin & Singup (login/cadastro)

### Parte 10) Mais sobre os componentes | Teoria 📚

- 👀 Acompanhe a vídeo aula
- Componentes fundamentais da parte Front-end 🕹️ (onde o show acontece, os usuários fazem interação com a aplicação)
- Componentes fundamentais da parte Back-end 🪁 (os batidores para organizar os dados, validar ou fazer algum processamento e depois devolver a `Resposta/Response` para Front-end)
- É possível fazer um projeto Django apenas com uma das duas partes (Front-end ou Back-end)?
- Como é feito a comunicação 🧵 entre Front-end e Back-end no Django?
- 🐞 Dúvidas ou qualquer informação adicional [AQUI 💬](https://github.com/huogerac/guia-para-aprender-django/issues/8)

### Parte 11) Class Based Views para Criar e Editar Models | Mão na massa 👾

- 👀 Acompanhe a vídeo aula
- Criar uma página para cadastrar um novo curso
- Criar uma página para editar um curso
- Rodando Django em modo Debug
- [GIT] Usando branch local para trabalhar em equipe
- [GIT] Usando rebase, resolvendo conflitos
- **✅ Links úteis...**
  - [Post sobre rebase](http://blog.billcode.com.br/search/label/Git)
  - [Codigo da AULA 11](https://github.com/huogerac/django_cursos/tree/aula-11)
- **👾 Tarefas**
  - Pratique o que foi feito na aula
  - Adicione o campo imagem para não ter a imagem fixa para todos os cursos
- 🐞 Dúvidas ou qualquer informação adicional [AQUI 💬](https://github.com/huogerac/guia-para-aprender-django/issues/12)

### Parte 12) APIs no Django

- 👀 Acompanhe a vídeo aula
- Like de Cursos com Forms
  - get_object_or_404
- Entendendo os tipos de retornos da View
- Like de Cursos usando API
- Módulo de services para melhor organização e reuso de código
- Entendendo as camadas da aplicação
- Como está os SQLs gerados na tela de litar cursos? Algum problema?
- **✅ Links úteis...**
    - [unique together](https://docs.djangoproject.com/en/4.0/ref/models/options/#unique-together)
    - [tipos de joins](https://www.pinterest.com.au/pin/780319072954977213/)
- **👾 Tarefas**
  - Pratique o que foi feito na aula
  - Adicione a funcionalidade para permitir ordenar por cursos com mais Likes
- 🐞 Dúvidas ou qualquer informação adicional [AQUI 💬](https://github.com/huogerac/guia-para-aprender-django/issues/13)

### Parte 13) Vamos publicar nossa aplicação? | Mão na massa 👾🚀

- Usar slug ao invés do id
- Usar o método `get_absolute_url`
- Vamos publicar nossa aplicação Django (a.k.a Deploy)

### Parte 14) 👾

- Em construção 🧩 👷

### Links úteis para quem quer se aprofundar 🤿 ⛏️

- [Tutorial.djangogirls.org](https://tutorial.djangogirls.org/pt/) 👌
- [Docs.djangoproject.com pt-br](https://docs.djangoproject.com/pt-br/4.0/) 👌
- [CodeMy Django Youtube Playlist](https://www.youtube.com/watch?v=HHx3tTQWUx0&list=PLCC34OHNcOtqW9BJmgQPPzUpJ8hl49AGy)
- [Gettingstartedwithdjango.com](http://www.gettingstartedwithdjango.com/)
- [Realpython.com/get-started-with-django-1](https://realpython.com/get-started-with-django-1/)
- [Tangowithdjango.com](https://www.tangowithdjango.com/)
- [Go Django.com](https://godjango.com/)
- [Go Django Youtube Playlist](https://www.youtube.com/c/Godjango/videos)

### Ideias de conteúdo para alunos apresentarem

- Paginação no Django
- Django Robots & Sitemaps
- Gerar DER do Banco & Transformar um DB em models
- Customizando o Django Admin
- Django Templates
- Permissão & Autorização
- Registro de usuários (Signup & Signin)
- Customizando os campos da tabela User (Profile)
- django_extensions
- django-waffle
- django honeypot
- Usar AJAX no template para fazer uma chamada ao Django
- Consultas avançadas no Django ORM (RAW SQL vs Django ORM)
- Django Class Based Views
- Criando um template (Estrutura modelo) de projeto Django
- Django Forms
- Montar um S3 local com Min.io para salvar imagens em storage exerno

### Ideias de projetos

- **Speaker Fight**: Quando temos chamadas para envio de palestras, sempre temos um formulario apenas. Imagine uma aplicacao onde voce faz cadastro e depois pode submeter uma paletra. E qualquer pessoa pode entrar e votar qual
  palestra quer assistir. A ideia e fazer um algoritmo que identifica as 2 paletras com a menor quantidade de `fight`. [Palestra 10] vs [Palestra 21]
  exibindo uma descricao legal e quem sabe uma imagem bacana para cada paletra.
  Assim o usuario consegue indicar entre as duas palestras, qual e a vencedora!
  Fazendo este loop infinito, vamos conseguir obter a lista das paletras mais interessantes. Obs: Já existiu um app com este nome, mas uma interface bem diferente que não fazia o que o nome sugere

- **Contador de caloria**: Um app onde cada usuário poderá registrar seu consumo de calorias por dia

- **Todo App**: Um app para gerencia tarefas (todoist like)

- **Pinterest Clone**: Um app para cada usuário postar imagens

- **Tweeter Clone**: Auto explicativo

- **Blog like hashnode**: Um blog para postar textos na ordem cronológica

- **App para salvar notas**: Um lugar para cada usuário organizar suas notas (Google Keep Like)

- **App para salvar senhas**: Um gerenciador de senhas

- **App gerar VCard**: Um app onde obtem dados de contato e gera um VCard para o usuário conseguir compartilhar seu contato de forma mais profissional

- **App para encurtar URLs**: Um app onde passamos URLs originais (geralmente longas), o app irá gerar uma versão super reduzida. Desta forma quando qualquer pessoa tentar acessar a versão reduzida, será redirecionada para a URL original

- **App para salvar melhores links**: App para cada usuário organizar os infinitos links interessantes que recebemos por ai, já pensou ter categorias e que seja fácil localizar links sobre assuntos específicos

- **Site status Checker**: Um app que podemos cadastrar outros sites que temos publicado, dai teremos um serviço que a cada 5 ou 10min irá verificar se nossos sites cadastrados estão retornando código de sucesso (Exemplo 200), em caso de um dos nossos sites ficar fora do ar (404, 500), devemos receber uma notificação ou email

- **API de Ceps**: Fazer um app importanto todos os CEPs do site correios, e criar APIS amigáveis de forma que qualquer pessoa possa fazer uma requisição passando um CEP e ter na resposta um endereço completo ou mensagem de CEP inválido.

### Quer ajudar? 👷

- Estamos trabalhando neste material, tem muito rascunho ainda! Se tiver qualquer tipo de crítica ou sugestão, queremos saber! 💡
- Acesse o link abaixo e crie uma **nova discussão**
- 👉 [Qualquer tipo de ajuda é mais que bem-vinda!](https://github.com/huogerac/guia-para-aprender-django/discussions)

1 - O que voces entenderam para fazer no período da tarde?

- Replicar o que já faz de manhã
- Django
- Django Girls
- Pra tentar todo dia avançar no projeto final

2 - O que é para fazer sobre os assuntos de sexta-feira?

- Aprender Django, mas temos a oportunidade de escolher o assunto
- Podemos trazer qualquer coisa de Django

3 - Qual entendimento sobre o "Projetinho Um"

- Fazer em grupo - OK
- Prazo - ASAP
