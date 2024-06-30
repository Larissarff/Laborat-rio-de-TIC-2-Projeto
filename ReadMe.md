# Projeto 02 - Mini-projeto Web utilizando Docker + PostgreSQL

## Documentação para a instalação e configuração necessárias para a execução do mini-projeto Web.

#### Membros da Equipe:

COLOCAR AS MATRÍCULAS E NOMES DE CADA INTEGRANTE AQUI.
<!-- OBJETIVO OBRIGATÓRIO: TERMINAR DE PREENCHER ESTA DOCUMENTAÇÃO -->

### Pré-instalação (Ubuntu - objetivo de avaliação optativo)

0. Primeiramente, vale ressaltar que esse projeto utiliza o framework Flask, escrito em Python, para o back-end da aplicação. O motivo da escolha dessa ferramenta são dois: (i) curva de aprendizado mais rápida e (ii) utiliza Python, que será a linguagem de programação vista no próximo semestre.

1. Antes de tudo, verifique se o Docker está instalado no Ubuntu. Para isso, abra o terminal pelo atalho `Ctrl + Alt + T` e digite o seguinte comando:

```bash
docker --version
```
Caso apareça uma mensagem semelhante a `Docker version 26.1.4, build 5650f9b`, o Docker está instalado. Caso contrário, é preciso seguir o tutorial de instalação Docker presente [aqui](https://drive.google.com/file/d/1kgtSUo5lSGNbZ4mQMIsRnIepf6Haiy91/view?usp=sharing).

2. Em seguida, remova todos os contâineres do PostgreSQL e pgAdmin que podem estar presentes desde a última demonstração. Para isso, execute os seguintes comandos:

```bash
docker stop $(docker ps -a -q)
```
```bash
docker rm $(docker ps -a -q)
```
Caso algum container tenha sido removido, parte de sua numeração hash aparecerá na tela. Execute o comando `docker ps -a` para mostrar todos os contâineres, inclusive os desabilitados. Se nada aparecer, então pule para o Passo 3.

3. Ceritifque-se de estar dentro do diretório `Projeto2` para executar o próximo comando:

```bash
docker compose up --build -d
```
Este comando executará o arquivo `docker compose.yml` presente no diretório `Projeto2`, que orquestrará o download das imagens do PostgreSQL e pgAdmim, como também a criação dos contâineres. Após o término do comando, execute `docker ps` e verifique se todos os côntaineres estão rodando. Neste caso, ainda não estarão porque vocês ainda não configuraram a conexão com o banco de dados no arquivo `app.py`. Para ver mais informações sobre o erro, execute o comando `docker composer logs app`, sendo app o nome do container (substituia por 'db' ou 'pgadmin' se necessário). Verifique o nome do seu container da aplicação Web a partir do comando `docker ps -a`.

Daqui em diante, o projeto está pré-instalado. Para instalá-lo completamente, será preciso atender aos objetivos de avaliação obrigatórios listados no enunciado do trabalho. *Importante:* após a finalização do projeto, rode novamente o comando `docker compose up --build -d` para levantar o container do aplicativo Web. Após configurar o caminho do banco em `app.py`, você precise remover os contâineres com o comando `docker rm -f $(docker ps -a -q)`, rode o comando `docker compose up --build -d` duas vezes para que o container do aplicativo seja devidamente levantado. Para isso, verifique a partir do comando `docker ps` se há três contâineres.

### Pré-instalação (Windows)

Utilize o tutorial disponivel em [https://youtu.be/L_2l8XTCPAE] para instalar o PostgreSQL e verificar onde fica o Query Tool para a execução de comandos. Caso crie o banco de dados PDV conforme mostrado no vídeo, dispense o script *init.sql*.

# <h1 align="center"> Laboratório de TIC - 2° Projeto </h1>
<h1 align="center"> 
     <img src="https://cdn.jsdelivr.net/gh/devicons/devicon@latest/icons/docker/docker-original-wordmark.svg" height="95" width="95" />
     <img src="https://cdn.jsdelivr.net/gh/devicons/devicon@latest/icons/html5/html5-original-wordmark.svg" height="95" width="95" /> 
     <img src="https://cdn.jsdelivr.net/gh/devicons/devicon@latest/icons/python/python-original-wordmark.svg" height="95" width="95" /> 
     <img src="https://cdn.jsdelivr.net/gh/devicons/devicon@latest/icons/css3/css3-original-wordmark.svg" height="95" width="95" /> 
      <img src="https://cdn.jsdelivr.net/gh/devicons/devicon@latest/icons/postgresql/postgresql-plain-wordmark.svg" height="95" width="95" />
</h1>

 # [Descrição do Projeto](#descrição-do-projeto)
 
  Projeto baseado em uma aplicação web com acesso á banco de dados SQL 

# HTML 
O código em HTML é como a alma do site, ele serve como a estrutura central da aplicação web.
Nele escolhemos quais títulos serão incluídos, se haverá botões, quantas subdivisões e tudo que será indispensável para o funcionamento da aplicação.

🔨 Realizamos algumas alterações no HTML fornecido como:

### Adicionamos o atributo ``` required ``` no Input:
  
  Inicialmente, o campo de entrada de texto para comandos SQL não possuia validação HTML, após as modificações, adicionamos o atributo required ao campo de entrada de texto, obrigando o usuário a preenchê-lo antes de enviar o formulário. Se trata de um recurso HTML5 que garante que o campo de entrada deve ser preenchido antes de o formulário ser submetido. Isso melhora a experiência do usuário, prevenindo a submissão de formulários com dados incompletos e reduzindo a necessidade de validação no lado do servidor.

* inicial:
  
  ```ruby
  <input type="text" name="comandoSQL" placeholder="Digite seu comando SQL">

* modificado: 

```ruby
  <input type="text" required name="comandoSQL" placeholder="Digite seu comando SQL">
```
### Filtro ```safe``` no Jinja2:
   obs:
  * Jinja2: Ferramenta que ajuda a preencher modelos de HTML com dados dinâmicos. Com Jinja2, você pode usar a sintaxe de template para 
  incluir variáveis e lógica no seu HTML, facilitando a criação de páginas web dinâmicas e interativas.

O filtro safe é usado para marcar uma string como segura para ser renderizada como HTML sem escapamento automático.


# CSS 
Já o arquivo styles.css será responsável pelo estilo (como seu próprio nome já nos indica) e aparência do site. CSS é associada ao código HTML por um link dentro do ``` <head></head> ``` do  index.html 

```ruby
<link rel="stylesheet" href="{{ url_for('static', filename='css/styles.css') }}"/>
```

# Python

# [Funcionalidades e Demonstração da Aplicação](#funcionalidades-e-demonstração-da-aplicação)
# [Acesso ao Projeto](#acesso-ao-projeto)
# [Tecnologias utilizadas](#tecnologias-utilizadas)
  - O Docker é uma plataforma de código aberto que permite a criação, distribuição e execução de aplicativos em contêineres (Contêineres são unidades leves e portáteis, formados a partir de imagens, que encapsulam
uma aplicação e todas as suas dependências, garantindo que ela possa ser executada de
maneira consistente em qualquer ambiente).
  - Contudo, para este projeto, foi adotada uma abordagem mais indicada e utilizada em
ambientes profissionais que facilita a criação dos contêineres e seu gerenciamento: o [Docker
Compose](#Docker-Compose). Essa ferramenta do Docker visa orquestrar a criação dos contêineres e a ordem no
qual são criados, de forma que os recursos necessários para um container funcionar
adequadamente sejam seguidos na devida ordem.

 ``Docker`` ``Python`` ``HTML`` ``CSS`` ``SQL``

# [Pessoas Desenvolvedoras do Projeto](#pessoas-desenvolvedoras)


# [Conclusão](#conclusão)

<!-- OBJETIVO OBRIGATÓRIO: TERMINAR DE PREENCHER ESTA DOCUMENTAÇÃO -->
