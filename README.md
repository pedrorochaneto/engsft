# 🚀 Servidor Web com Docker + Nginx

 Este projeto utiliza **Docker** e **Nginx** para executar um servidor web com HTML, CSS e JavaScript.

 ## 📥 1. Clonar o repositório

 Clone o repositório:

```
git clone URL_DO_REPOSITORIO
```

 Entre na pasta do projeto:

```
cd NOME_DO_REPOSITORIO
```

 ## 🐳 2. Criar a imagem Docker

 Execute:

```
docker build -t meu-site .
```

 ## ▶️ 3. Executar o container

 Execute:

```
docker run -d --name meu-servidor -p 8080:80 meu-site
```

 ## 🌐 4. Acessar o site

 Abra o navegador e acesse:

```
http://localhost:8080
```

 O site estará disponível através do Nginx.

 ## ⏹️ Parar o servidor

 Para parar o container:

```
docker stop meu-servidor
```

 ## ▶️ Iniciar novamente

 Para iniciar o container novamente:

```
docker start meu-servidor
```

 ## 🗑️ Remover o container

 Para remover o container:

```
docker rm -f meu-servidor
```

 ## 📌 Comandos resumidos

```
git clone URL_DO_REPOSITORIO
cd NOME_DO_REPOSITORIO

docker build -t meu-site .
docker run -d --name meu-servidor -p 8080:80 meu-site
```

 Depois, acesse:

```
http://localhost:8080
```
