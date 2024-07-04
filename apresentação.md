# Vantagens uso Docker:
### Docker é uma ferramenta poderosa para desenvolver, testar e implantar aplicações de maneira eficiente e confiável.
- consistências: evita de não rodar em uma máquina e em outra sim. aplicação executada da mesma forma.
- portabilidade: se pode transportar o contêiner para qqrl outra pessoa
- automação: simplifica o processo de configuração e implantação. - tempo. - erros humanos.

## Dockerfile Explicado

### 1. Imagem Base
```dockerfile
FROM python:3.9
```
- **O que faz:** Esta linha especifica que a imagem base para o container será a imagem oficial do Python na versão 3.9.
- **Por que usar:** Usar uma imagem base confiável e específica garante que todas as dependências do Python estejam presentes no container. A versão 3.9 foi escolhida provavelmente porque a aplicação requer essa versão específica do Python.

### 2. Diretório de Trabalho
```dockerfile
WORKDIR /app
```
- **O que faz:** Define o diretório de trabalho dentro do container onde os comandos subsequentes serão executados.
- **Por que usar:** Organiza o ambiente do container e garante que todos os arquivos e comandos sejam executados dentro do diretório `/app`, evitando confusões com caminhos relativos.

### 3. Copiar Arquivos
```dockerfile
COPY . .
```
- **O que faz:** Copia todos os arquivos do diretório atual (onde está o Dockerfile) para o diretório de trabalho dentro do container.
- **Por que usar:** Esta linha é essencial para garantir que todos os arquivos do projeto, incluindo código-fonte, requisitos e outros, estejam disponíveis no container para a construção da aplicação.

### 4. Instalar Dependências
```dockerfile
RUN pip install -r app/requirements.txt
```
- **O que faz:** Executa o comando para instalar as dependências listadas no arquivo `requirements.txt` usando `pip`.
- **Por que usar:** Automatiza a instalação das dependências necessárias para a aplicação, garantindo que todas as bibliotecas necessárias sejam instaladas no ambiente do container.

### 5. Expor Porta
```dockerfile
EXPOSE 5000
```
- **O que faz:** Informa ao Docker que o container vai escutar na porta 5000.
- **Por que usar:** É uma convenção para documentar quais portas o container está usando. No entanto, por si só, essa linha não mapeia a porta do host para o container; isso precisa ser feito ao executar o container (por exemplo, usando `-p 5000:5000`).

### 6. Copiar Arquivo de Ambiente
```dockerfile
COPY .env .env
```
- **O que faz:** Copia o arquivo `.env` do diretório local para o container.
- **Por que usar:** Os arquivos `.env` geralmente contêm variáveis de ambiente sensíveis ou de configuração que a aplicação precisa para funcionar corretamente.

### 7. Comando Padrão
```dockerfile
CMD ["python", "app.py"]
```
- **O que faz:** Define o comando padrão que será executado quando o container iniciar. Neste caso, executa o script `app.py` usando o Python.
- **Por que usar:** Garante que a aplicação Flask será iniciada automaticamente quando o container for iniciado, tornando o processo de execução da aplicação simples e direto.

## Conclusão

Esse Dockerfile é usado para criar um ambiente isolado e replicável para uma aplicação Flask escrita em Python. Ele facilita a construção, o teste e a implementação da aplicação, garantindo que todas as dependências e configurações necessárias sejam incluídas e configuradas automaticamente. 

**Benefícios de Usar Docker:**
- **Consistência:** A aplicação será executada da mesma forma em qualquer ambiente, eliminando problemas de "funciona na minha máquina".
- **Isolamento:** As dependências e configurações da aplicação não interferem no sistema host ou em outras aplicações.
- **Portabilidade:** O container pode ser facilmente movido e executado em diferentes sistemas e plataformas.
- **Automação:** Simplifica o processo de configuração e implantação, economizando tempo e reduzindo erros humanos.

Docker é uma ferramenta poderosa para desenvolvedores e engenheiros de software, pois simplifica a criação e a gestão de ambientes de desenvolvimento e produção.

### Dockerfile
Um **Dockerfile** é basicamente um script com um conjunto de instruções que define como criar uma imagem Docker. Pense nele como uma receita de bolo: ele especifica todos os ingredientes e passos necessários para criar um ambiente de software. 

Exemplo de um Dockerfile simples:
```dockerfile
# Usa uma imagem base do Node.js
FROM node:14

# Define o diretório de trabalho dentro do contêiner
WORKDIR /app

# Copia os arquivos do seu projeto para dentro do contêiner
COPY . .

# Instala as dependências do projeto
RUN npm install

# Expõe a porta que a aplicação vai usar
EXPOSE 3000

# Comando para rodar a aplicação
CMD ["npm", "start"]
```

### docker-compose.yml
O **docker-compose.yml** é um arquivo de configuração usado pelo Docker Compose para definir e executar aplicações multicontêiner. Ele permite que você defina serviços, redes e volumes em um único arquivo, tornando mais fácil o gerenciamento de aplicações que requerem múltiplos contêineres.

Exemplo de um docker-compose.yml simples:
```yaml
version: '3'
services:
  web:
    build: .
    ports:
      - "3000:3000"
    volumes:
      - .:/app
    depends_on:
      - db

  db:
    image: postgres:13
    environment:
      POSTGRES_DB: mydatabase
      POSTGRES_USER: user
      POSTGRES_PASSWORD: password
    volumes:
      - db_data:/var/lib/postgresql/data

volumes:
  db_data:
```

### Resumo
- **Dockerfile**: Define como construir uma única imagem de contêiner. É como uma receita para criar um ambiente de software específico.
- **docker-compose.yml**: Define como orquestrar múltiplos contêineres, facilitando a criação de ambientes de desenvolvimento e produção complexos com várias dependências.

Se você pensar em termos de uma aplicação web, o Dockerfile é como configurar um servidor específico, enquanto o docker-compose.yml é como configurar toda a infraestrutura necessária para a aplicação funcionar (servidor web, banco de dados, etc.).
