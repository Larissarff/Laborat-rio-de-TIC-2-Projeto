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

<!-- OBJETIVO OBRIGATÓRIO: TERMINAR DE PREENCHER ESTA DOCUMENTAÇÃO -->
