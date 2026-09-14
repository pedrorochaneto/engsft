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
