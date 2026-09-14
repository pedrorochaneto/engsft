# 🐳 Docker Hello World

Guia prático para criar e executar seu primeiro container Docker personalizado.

---

### 📋 Pré-requisitos

* **Docker** instalado no sistema.
* **Git** (opcional).

Para verificar se a instalação está correta:

```bash
docker --version

```

---

### 📁 Estrutura do Projeto

Crie a pasta de trabalho e acesse o diretório:

```bash
mkdir docker-hello-world
cd docker-hello-world

```

Estrutura final esperada:

```text
docker-hello-world/
└── Dockerfile

```

---

### 📝 Criando o Dockerfile

Crie um arquivo com o nome exato `Dockerfile` contendo o seguinte conteúdo:

```dockerfile
FROM alpine:latest

CMD ["echo", "Hello World"]

```

* `FROM alpine:latest`: define uma distribuição Linux ultraleve (~5 MB) como imagem base.
* `CMD ["echo", "Hello World"]`: define o comando executado por padrão ao iniciar o container.

---

### 🔨 Construindo a Imagem

Gere a imagem local a partir do diretório atual (o ponto final indica o diretório de contexto):

```bash
docker build -t meu-hello-world .

```

> **Dica:** O nome `meu-hello-world` evita conflito com a imagem oficial `hello-world` do Docker Hub.

Para confirmar se a imagem foi gerada:

```bash
docker images

```

---

### ▶️ Executando o Container

Inicie o container para visualizar a saída:

```bash
docker run --rm meu-hello-world

```

* A flag `--rm` apaga o container da memória automaticamente logo após o término da execução.

**Saída esperada:**

```text
Hello World

```

---

### 🧹 Limpeza do Ambiente

Para deletar a imagem criada e liberar espaço em disco:

```bash
docker rmi meu-hello-world

```

---

### 🚀 Ciclo de Vida Resumido

```text
Dockerfile ──(build)──> Imagem ──(run)──> Container ──(exit/rm)──> Finalizado

```

| Comando | Descrição |
| --- | --- |
| `docker build -t <nome> .` | Constrói a imagem com base no Dockerfile |
| `docker run --rm <nome>` | Cria, roda e remove o container temporário |
| `docker images` | Lista todas as imagens locais |
| `docker rmi <nome>` | Exclui a imagem do sistema |














# 🚀 Servidor Web com Docker + Nginx

Este projeto utiliza **Docker** para executar um servidor web com **Nginx**, servindo uma página HTML com arquivos CSS e JavaScript.

## 📁 Estrutura do projeto

```text
engsft/
├── Dockerfile
├── index.html
├── style.css
└── script.js
```

## 🐳 Dockerfile

```dockerfile
FROM nginx:latest

COPY index.html /usr/share/nginx/html/index.html
COPY style.css /usr/share/nginx/html/style.css
COPY script.js /usr/share/nginx/html/script.js
```

### Explicação

#### `FROM nginx:latest`

```dockerfile
FROM nginx:latest
```

Utiliza a imagem oficial do Nginx como imagem base.

O Nginx já vem instalado e configurado dentro dessa imagem.

#### `COPY index.html`

```dockerfile
COPY index.html /usr/share/nginx/html/index.html
```

Copia o arquivo `index.html` do projeto para dentro do container.

O Nginx utiliza `/usr/share/nginx/html` como diretório padrão para os arquivos HTML.

#### `COPY style.css`

```dockerfile
COPY style.css /usr/share/nginx/css/style.css
```

Copia o arquivo CSS para dentro do container.

#### `COPY script.js`

```dockerfile
COPY script.js /usr/share/nginx/js/script.js
```

Copia o JavaScript para dentro do container.

---

# 🔨 Criando a imagem

Abra o terminal na pasta onde está o `Dockerfile`:

```powershell
cd "C:\caminho\para\engsft"
```

Execute:

```powershell
docker build -t meu-site .
```

### Explicação

```text
docker build -t meu-site .
            │       │
            │       └── pasta atual
            │
            └── nome da imagem
```

O comando cria uma imagem chamada:

```text
meu-site
```

Para verificar:

```powershell
docker images
```

---

# ▶️ Executando o container

Depois de criar a imagem:

```powershell
docker run -d --name meu-servidor -p 8080:80 meu-site
```

### Explicação

- `docker run` → cria e inicia um container.
- `-d` → executa em segundo plano.
- `--name meu-servidor` → define o nome do container.
- `-p 8080:80` → conecta a porta `8080` do computador à porta `80` do container.
- `meu-site` → imagem utilizada para criar o container.

O mapeamento de portas é:

```text
Computador          Container
localhost:8080  →   porta 80
                       │
                       ▼
                      Nginx
```

---

# 🌐 Acessando o site

Abra o navegador:

```text
http://localhost:8080
```

O Nginx irá servir o seu `index.html`.

---

# 🔍 Verificando o container

Para verificar se o container está rodando:

```powershell
docker ps
```

Você deverá encontrar algo semelhante a:

```text
CONTAINER ID   IMAGE      STATUS         PORTS                  NAMES
xxxxxxxxxxxx   meu-site   Up ...         0.0.0.0:8080->80/tcp   meu-servidor
```

A parte:

```text
8080->80
```

significa:

```text
Porta do computador → Porta do container
       8080         →       80
```

---

# 📜 Visualizando os logs

Para visualizar os logs:

```powershell
docker logs meu-servidor
```

Para acompanhar os logs em tempo real:

```powershell
docker logs -f meu-servidor
```

Pressione `Ctrl + C` para sair.

---

# ⏹️ Parando o container

```powershell
docker stop meu-servidor
```

O container será parado, mas continuará existindo.

---

# ▶️ Iniciando novamente

Se o container estiver parado:

```powershell
docker start meu-servidor
```

Depois acesse:

```text
http://localhost:8080
```

---

# 🗑️ Removendo o container

Para remover:

```powershell
docker rm -f meu-servidor
```

A imagem `meu-site` continuará existindo.

---

# 🔄 Alterando o HTML, CSS ou JavaScript

Os arquivos são copiados para a imagem durante o comando:

```powershell
docker build -t meu-site .
```

Portanto, depois de alterar:

```text
index.html
style.css
script.js
```

é necessário criar a imagem novamente:

```powershell
docker build -t meu-site .
```

Depois remova o container antigo:

```powershell
docker rm -f meu-servidor
```

E crie um novo:

```powershell
docker run -d --name meu-servidor -p 8080:80 meu-site
```

---

# 🔗 Referenciando CSS e JavaScript

Como os arquivos foram colocados em:

```text
/usr/share/nginx/css/style.css
/usr/share/nginx/js/script.js
```

no `index.html`, utilize:

```html
<link rel="stylesheet" href="/css/style.css">
```

E:

```html
<script src="/js/script.js"></script>
```

---

# 📌 Fluxo completo

```text
Dockerfile
    │
    │ docker build
    ▼
Imagem "meu-site"
    │
    │ docker run
    ▼
Container "meu-servidor"
    │
    │ 8080 → 80
    ▼
Nginx
    │
    ├── index.html
    ├── css/style.css
    └── js/script.js
    │
    ▼
http://localhost:8080
```

# 🧾 Comandos principais

```powershell
# Criar a imagem
docker build -t meu-site .

# Criar e iniciar o container
docker run -d --name meu-servidor -p 8080:80 meu-site

# Ver containers rodando
docker ps

# Ver todos os containers
docker ps -a

# Ver logs
docker logs meu-servidor

# Parar
docker stop meu-servidor

# Iniciar
docker start meu-servidor

# Remover container
docker rm -f meu-servidor

# Remover imagem
docker rmi meu-site
```
