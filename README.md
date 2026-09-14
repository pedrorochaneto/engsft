🐳 Docker Hello World

Este projeto demonstra como criar e executar um container Docker que imprime Hello World no terminal.

📋 Pré-requisitos

Antes de começar, tenha instalado:

Docker
Git (opcional)

Para verificar se o Docker está instalado:

docker --version

📁 Estrutura do projeto

Crie uma pasta para o projeto:

mkdir docker-hello-world
cd docker-hello-world


A estrutura ficará assim:

docker-hello-world/
└── Dockerfile

📝 Criando o Dockerfile

Crie um arquivo chamado Dockerfile:

FROM alpine:latest

CMD ["echo", "Hello World"]

O que esse Dockerfile faz?
FROM alpine:latest — utiliza uma imagem Linux Alpine como base.
CMD ["echo", "Hello World"] — executa o comando echo quando o container iniciar.
🔨 Criando a imagem

Execute o comando abaixo dentro da pasta do projeto:

docker build -t hello-world .


O parâmetro -t define o nome da imagem como hello-world.

Para verificar se a imagem foi criada:

docker images

▶️ Executando o container

Agora execute:

docker run --rm hello-world


A saída esperada será:

Hello World


O parâmetro --rm faz com que o container seja removido automaticamente após a execução.

🧹 Limpando a imagem

Caso queira remover a imagem criada:

docker rmi hello-world

🚀 Resumo

Os principais comandos são:

# Criar a imagem
docker build -t hello-world .

# Executar o container
docker run --rm hello-world


Resultado:

Hello World

📌 Conclusão

Você criou uma imagem Docker baseada em Alpine e executou um container que imprime Hello World no terminal. Esse é um dos exemplos mais simples para entender o ciclo básico do Docker:

Dockerfile → Build → Image → Container → Execução
