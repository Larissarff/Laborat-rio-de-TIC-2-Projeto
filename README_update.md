# <h1 align="center"> Laboratório de TIC - 2° Projeto </h1>
<h1 align="center"> 
     <img src="https://cdn.jsdelivr.net/gh/devicons/devicon@latest/icons/docker/docker-original-wordmark.svg" height="95" width="95" />
     <img src="https://cdn.jsdelivr.net/gh/devicons/devicon@latest/icons/html5/html5-original-wordmark.svg" height="95" width="95" /> 
     <img src="https://cdn.jsdelivr.net/gh/devicons/devicon@latest/icons/python/python-original-wordmark.svg" height="95" width="95" /> 
     <img src="https://cdn.jsdelivr.net/gh/devicons/devicon@latest/icons/css3/css3-original-wordmark.svg" height="95" width="95" /> 
      <img src="https://cdn.jsdelivr.net/gh/devicons/devicon@latest/icons/postgresql/postgresql-plain-wordmark.svg" height="95" width="95" />
</h1>

 # Descrição do Projeto
 
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
    - Jinja2: Ferramenta que ajuda a preencher modelos de HTML com dados dinâmicos. Com Jinja2, você pode usar a sintaxe de template (como um molde) para incluir variáveis e lógica no seu HTML, facilitando a criação de páginas web dinâmicas e interativas.

O filtro safe é usado para marcar uma string como segura para ser renderizada como HTML sem escapamento automático.

* exemplo sem ```'safe'```:
  ```ruby
  {% set message = "<strong>Isso é importante!</strong>" %}
  <p>{{ message }}</p>
  ```
  Pode gerar uma devolutiva:  < strong> Isso é importante! </ strong>
  
* exemplo com ```'safe'```: 
```ruby
  {% set message = "<strong>Isso é importante!</strong>" %}
   <p>{{ message | safe }}</p>
```
Nesse caso, irá gerar uma devolutiva: <strong>Isso é importante!</strong> (em negrito) sem que sea corrompido.


### Uso da Sintaxe Jinja2 para Loop e Renderização de Tabelas: 

Estratégia para a renderização dinâmica de tabelas com base nos dados fornecidos no arquivo em python (será abordado posteriormente), tornando o código funcional e dinâmico. A implementação correta dos loops Jinja2 garante que qualquer conjunto de resultados seja exibido corretamente na tabela. Ele utiliza estratégias para percorrer cada linha da lista desejada

```ruby
  <thead>
    <tr>
        {% for coluna in colunas %} // Percorre cada linha da lista desejada.
            <th>{{ coluna }}</th> // Atribui um título para cada coluna.
        {% endfor %}
    </tr>
</thead> 
```
Também se utiliza para compor o corpo da tabela, da seguinte forma:
```ruby
<tbody>
    {% for row in consulta_resultado %} // Percorre cada linha na lista
        <tr>                            // Para cada linha, ele cria uma nova linha na tabela
            {% for value in row %}      // Percorre cada nova linha e cria uma célula de dados
                <td>{{ value }}</td>
            {% endfor %}
        </tr>
    {% endfor %}
</tbody>
```
- Exemplo de funcionando (dado pelo chat GPT)
```ruby
<!DOCTYPE html>
<html lang="pt-br">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Relatório de Notas</title>
</head>
<body>
    <h1>Relatório de Notas dos Alunos</h1>
    <table border="1">
        <thead>
            <tr>
                <th>Nome</th>
                <th>Matemática</th>
                <th>História</th>
                <th>Ciências</th>
            </tr>
        </thead>
        <tbody>
            <tr>
                <td>Alice</td>
                <td>85</td>
                <td>78</td>
                <td>92</td>
            </tr>
            <tr>
                <td>Charlie</td>
                <td>95</td>
                <td>92</td>
                <td>85</td>
            </tr>
        </tbody>
    </table>
</body>
</html>
```

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
