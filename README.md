
                      🐳 DOCKER HELLO WORLD - GUIA RÁPIDO


Este projeto demonstra passo a passo como criar uma imagem Docker personalizada
baseada em Alpine Linux e executar um container que imprime "Hello World".

--------------------------------------------------------------------------------
[1] PRÉ-REQUISITOS
--------------------------------------------------------------------------------

  * Docker instalado e em execução no sistema.
  * Git (opcional, para versionamento).

  Para verificar a instalação do Docker:
    $ docker --version

--------------------------------------------------------------------------------
[2] ESTRUTURA DO PROJETO
--------------------------------------------------------------------------------

  Crie o diretório de trabalho e acesse a pasta:
    $ mkdir docker-hello-world
    $ cd docker-hello-world

  Estrutura de arquivos:
    docker-hello-world/
    └── Dockerfile

--------------------------------------------------------------------------------
[3] CRIANDO O DOCKERFILE
--------------------------------------------------------------------------------

  Crie um arquivo chamado "Dockerfile" com o seguinte conteúdo:

  ----------------------------------------------------------------------------
  FROM alpine:latest
  CMD ["echo", "Hello World"]
  ----------------------------------------------------------------------------

  Entendendo as instruções:
    • FROM alpine:latest  -> Define o Alpine Linux como imagem base (~5MB).
    • CMD [...]           -> Especifica o comando padrão executado ao iniciar.

--------------------------------------------------------------------------------
[4] CONSTRUINDO A IMAGEM (BUILD)
--------------------------------------------------------------------------------

  Execute o comando de build dentro da pasta do projeto:
    $ docker build -t meu-hello-world .

  Nota: O ponto final (.) indica o diretório de contexto atual.
        Utilizamos "meu-hello-world" para evitar conflito com a imagem oficial.

  Para conferir a imagem recém-criada na listagem local:
    $ docker images

--------------------------------------------------------------------------------
[5] EXECUTANDO O CONTAINER (RUN)
--------------------------------------------------------------------------------

  Inicie o container com descarte automático após a execução:
    $ docker run --rm meu-hello-world

  * A flag "--rm" remove o container assim que a execução do processo termina.

  Saída no terminal:
  ============================================================================
  Hello World
  ============================================================================

--------------------------------------------------------------------------------
[6] LIMPEZA E MANUTENÇÃO (CLEANUP)
--------------------------------------------------------------------------------

  Caso queira remover a imagem criada e liberar espaço em disco:
    $ docker rmi meu-hello-world

--------------------------------------------------------------------------------
[7] RESUMO DO FLUXO DOCKER
--------------------------------------------------------------------------------

      +------------+          +-------------+          +---------------+
      | Dockerfile | =(build)>|   Imagem    | =(run)==>|   Container   |
      +------------+          +-------------+          +---------------+
                                                              |
                                                    (imprime saída e finaliza)

  TABELA RÁPIDA DE COMANDOS:
  ----------------------------------------------------------------------------
  Comando                       | Descrição
  ------------------------------+---------------------------------------------
  docker build -t <nome> .      | Constrói a imagem a partir do Dockerfile
  docker images                 | Lista todas as imagens baixadas/criadas
  docker run --rm <nome>        | Instancia e roda o container com auto-delete
  docker ps -a                  | Lista todos os containers (ativos e parados)
  docker rmi <nome>             | Remove a imagem local informada
  ----------------------------------------------------------------------------

================================================================================
Projeto pronto para ser versionado no Git!
================================================================================
