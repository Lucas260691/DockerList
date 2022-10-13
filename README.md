<h1 align="center">Docker Todo-List</h1>

## Descrição do Projeto
<p align="center"> O objetivo desse projeto é "conteinerizar" as aplicações de frontend, backend e testes, criando uma conexão entre elas</p>

# Habilidades
Neste projeto, você será capaz de:
  * Usar comandos dockers no CLI - Interface de linha de comando;
  * Criar um contêiner Docker para uma aplicação de front-end;
  * Criar um contêiner Docker para uma aplicação de back-end;
  * Criar um contêiner Docker para uma aplicação de testes;
  * Orquestrar os três contêineres utilizando o Docker compose.
  
  # Requisitos do projeto


## Comandos docker

#### 1. Crie um novo container de modo interativo sem roda-lo nomeando-o como `01container` e utilizando a imagem `alpine` usando a versão `3.12`

  - **Observações técnicas:** 
    - O container **não deve ser inicializado**, somente criado;
    - O container deve estar preparado para acesso interativo;
    
#### 2. Inicie o container `01container`

  - **Observações técnicas:** 
    - O container que está parado, deve ser iniciado;
    - Se o container tiver sido iniciado de modo interativo, ele deve se manter ativo ao inicia-lo.
    
#### 3. Liste os containers filtrando pelo nome `01container`

  - **Dica:** 
    - Praticamente todo comando de listagem no Docker possui uma forma de filtragem.

#### 4. Execute o comando `cat /etc/os-release` no container `01container` sem se acoplar a ele

  - **Observações técnicas:**
    - O container deve estar rodando, e você deve ser capaz de **executar um comando** nesse container.
  
  - **Dica:** 
    -  É possível fazer isso sem usar o comando `attach`.
    
#### 5. Remova o container `01container` que está em andamento.


#### 6. Faça o download da imagem `nginx` com a versão `1.21.3-alpine` sem criar ou rodar um container.


#### 7. Rode um novo container com a imagem  `nginx` com a versão `1.21.3-alpine` em segundo plano nomeando-o como `02images` e mapeando sua porta padrão de acesso para porta `3000` do sistema hospedeiro.


#### 8. Pare o container `02images` que está em andamento.

## Dockerfile

**⚠️ As aplicações a seguir contam com um [**README.md**](./docker/todo-app/README.md) próprio, que deve ser usado como referência na criação dos scripts!**

#### 9. Gere uma build a partir do Dockerfile do `back-end` do `todo-app` nomeando a imagem para `todobackend`.

  **Dica:** O comando `ADD` do Dockerfile, também pode ser utilizado para descompactar arquivos dentro do container.

#### 10. Gere uma build a partir do Dockerfile do `front-end` do `todo-app` nomeando a imagem para `todofrontend`.

  **Dica:** O comando `ADD` do Dockerfile, também pode ser utilizado para descompactar arquivos dentro do container.
  
#### 11.Gere uma build a partir do Dockerfile dos `testes` do `todo-app` nomeando a imagem para `todotests`.

  **Dica:** O comando `ADD` do Dockerfile, também pode ser utilizado para descompactar arquivos dentro do container.
  
  **Observação**: A aplicação `todotests` só funciona corretamente se estiver dockerizada e dentro de uma rede docker configurada corretamente.

#### 12. Suba uma orquestração em segundo plano com o docker-compose de forma que `backend`, `frontend` e `tests` consigam se comunicar.

  **Dica:** use as imagens já **"buildadas"** que foram executadas nos requisitos 9,10 e 11 para a criação do compose.

  - **O que será testado:** 
      - Se existe um arquivo `docker-compose.yml` na pasta `./docker/`:
        - O docker-compose deve rodar na versão 3.

      - **tests**
        - O container de `todotests` deve ter como dependencia os containers `frontend` e `backend`;
        - O nome do _service_ deverá ser `todotests`;
        - Deve ter uma variável de ambiente `FRONT_HOST` que recebe como valor o nome do container do `frontend`
          - Lembrando que, dentro de uma rede docker, o host de um container é indentificado pelo seu nome.

      - **front-end**
        - O container de `todofrontend` deve rodar na porta `3000`;
        - O nome do _service_ deverá ser `todofront`;
        - Deve ter como dependencia o container `backend`;
        - Deve ter uma variável de ambiente `REACT_APP_API_HOST` que recebe como valor o nome do container do `backend`.
          - Lembrando que, dentro de uma rede docker, o host de um container é indentificado pelo seu nome.

      - **back-end**
        - O container de `todobackend` deve rodar na porta `3001`;
        - O nome do _service_ deverá ser `todoback`;

  - **Dica:**
    - Consulte a documentação em `./docker/todo-app/README.md`;
    - É possível adicionar e extrair arquivos `.tar.gz` no `Dockerfile` com apenas um comando.

---



