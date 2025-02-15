---
title: Criar contêineres de serviço PostgreSQL
shortTitle: PostgreSQL service containers
intro: Você pode criar um contêiner de serviço PostgreSQL para usar no seu fluxo de trabalho. Este guia mostra exemplos para criar um serviço PostgreSQL para trabalhos executados em contêineres ou diretamente na máquina executora.
redirect_from:
  - /actions/automating-your-workflow-with-github-actions/creating-postgresql-service-containers
  - /actions/configuring-and-managing-workflows/creating-postgresql-service-containers
  - /actions/guides/creating-postgresql-service-containers
versions:
  fpt: '*'
  ghes: '*'
  ghae: '*'
  ghec: '*'
type: tutorial
topics:
  - Containers
  - Docker
ms.openlocfilehash: 9d5ad3e32e5df22101b61aa7ba134e7fe69333e5
ms.sourcegitcommit: 47bd0e48c7dba1dde49baff60bc1eddc91ab10c5
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/05/2022
ms.locfileid: '145096077'
---
{% data reusables.actions.enterprise-beta %} {% data reusables.actions.enterprise-github-hosted-runners %}

## Introdução

Este guia mostra exemplos de fluxos de trabalho que configuram um contêiner de serviço usando a imagem `postgres` do Docker Hub. O fluxo de trabalho executa um script que se conecta ao serviço do PostgreSQL, cria uma tabela e, em seguida, preenche-a com dados. Para testar se o fluxo de trabalho cria e preenche a tabela do PostgreSQL, o script imprime os dados da tabela para o console.

{% data reusables.actions.docker-container-os-support %}

## Pré-requisitos

{% data reusables.actions.service-container-prereqs %}

Também pode ser útil ter um entendimento básico de YAML, a sintaxe para {% data variables.product.prodname_actions %} e PostgreSQL. Para obter mais informações, consulte:

- "[Aprenda a usar o {% data variables.product.prodname_actions %}](/actions/learn-github-actions)"
- "[Tutorial do PostgreSQL](https://www.postgresqltutorial.com/)" na documentação do PostgreSQL

## Executar trabalhos em contêineres

{% data reusables.actions.container-jobs-intro %}

{% data reusables.actions.copy-workflow-file %}

```yaml{:copy}
name: PostgreSQL service example
on: push

jobs:
  # Label of the container job
  container-job:
    # Containers must run in Linux based operating systems
    runs-on: ubuntu-latest
    # Docker Hub image that `container-job` executes in
    container: node:10.18-jessie

    # Service containers to run with `container-job`
    services:
      # Label used to access the service container
      postgres:
        # Docker Hub image
        image: postgres
        # Provide the password for postgres
        env:
          POSTGRES_PASSWORD: postgres
        # Set health checks to wait until postgres has started
        options: >-
          --health-cmd pg_isready
          --health-interval 10s
          --health-timeout 5s
          --health-retries 5

    steps:
      # Downloads a copy of the code in your repository before running CI tests
      - name: Check out repository code
        uses: {% data reusables.actions.action-checkout %}

      # Performs a clean installation of all dependencies in the `package.json` file
      # For more information, see https://docs.npmjs.com/cli/ci.html
      - name: Install dependencies
        run: npm ci

      - name: Connect to PostgreSQL
        # Runs a script that creates a PostgreSQL table, populates
        # the table with data, and then retrieves the data.
        run: node client.js
        # Environment variables used by the `client.js` script to create a new PostgreSQL table.
        env:
          # The hostname used to communicate with the PostgreSQL service container
          POSTGRES_HOST: postgres
          # The default PostgreSQL port
          POSTGRES_PORT: 5432
```

### Configurar o trabalho executor

{% data reusables.actions.service-container-host %}

{% data reusables.actions.postgres-label-description %}

```yaml{:copy}
jobs:
  # Label of the container job
  container-job:
    # Containers must run in Linux based operating systems
    runs-on: ubuntu-latest
    # Docker Hub image that `container-job` executes in
    container: node:10.18-jessie

    # Service containers to run with `container-job`
    services:
      # Label used to access the service container
      postgres:
        # Docker Hub image
        image: postgres
        # Provide the password for postgres
        env:
          POSTGRES_PASSWORD: postgres
        # Set health checks to wait until postgres has started
        options: >-
          --health-cmd pg_isready
          --health-interval 10s
          --health-timeout 5s
          --health-retries 5
```

### Configurar as etapas

{% data reusables.actions.service-template-steps %}

```yaml{:copy}
steps:
  # Downloads a copy of the code in your repository before running CI tests
  - name: Check out repository code
    uses: {% data reusables.actions.action-checkout %}

  # Performs a clean installation of all dependencies in the `package.json` file
  # For more information, see https://docs.npmjs.com/cli/ci.html
  - name: Install dependencies
    run: npm ci

  - name: Connect to PostgreSQL
    # Runs a script that creates a PostgreSQL table, populates
    # the table with data, and then retrieves the data.
    run: node client.js
    # Environment variable used by the `client.js` script to create
    # a new PostgreSQL client.
    env:
      # The hostname used to communicate with the PostgreSQL service container
      POSTGRES_HOST: postgres
      # The default PostgreSQL port
      POSTGRES_PORT: 5432
```

{% data reusables.actions.postgres-environment-variables %}

O nome do host do serviço PostgreSQL é o rótulo configurado no fluxo de trabalho, nesse caso, `postgres`. Uma vez que os contêineres do Docker na mesma rede da ponte definida pelo usuário abrem todas as portas por padrão, você poderá acessar o contêiner de serviço na porta-padrão 5432 do PostgreSQL.

## Executar trabalhos diretamente na máquina executora

Ao executar um trabalho diretamente na máquina executora, você deverá mapear as portas no contêiner de serviço com as portas no host do Docker. Você pode acessar os contêineres de serviço do host do Docker usando o `localhost` e o número da porta do host do Docker.

{% data reusables.actions.copy-workflow-file %}

```yaml{:copy}
name: PostgreSQL Service Example
on: push

jobs:
  # Label of the runner job
  runner-job:
    # You must use a Linux environment when using service containers or container jobs
    runs-on: ubuntu-latest

    # Service containers to run with `runner-job`
    services:
      # Label used to access the service container
      postgres:
        # Docker Hub image
        image: postgres
        # Provide the password for postgres
        env:
          POSTGRES_PASSWORD: postgres
        # Set health checks to wait until postgres has started
        options: >-
          --health-cmd pg_isready
          --health-interval 10s
          --health-timeout 5s
          --health-retries 5
        ports:
          # Maps tcp port 5432 on service container to the host
          - 5432:5432

    steps:
      # Downloads a copy of the code in your repository before running CI tests
      - name: Check out repository code
        uses: {% data reusables.actions.action-checkout %}

      # Performs a clean installation of all dependencies in the `package.json` file
      # For more information, see https://docs.npmjs.com/cli/ci.html
      - name: Install dependencies
        run: npm ci

      - name: Connect to PostgreSQL
        # Runs a script that creates a PostgreSQL table, populates
        # the table with data, and then retrieves the data
        run: node client.js
        # Environment variables used by the `client.js` script to create
        # a new PostgreSQL table.
        env:
          # The hostname used to communicate with the PostgreSQL service container
          POSTGRES_HOST: localhost
          # The default PostgreSQL port
          POSTGRES_PORT: 5432
```

### Configurar o trabalho executor

{% data reusables.actions.service-container-host-runner %}

{% data reusables.actions.postgres-label-description %}

O fluxo de trabalho mapeia a porta 5432 no contêiner de serviço do PostgreSQL com o host do Docker. Para obter mais informações sobre a palavra-chave `ports`, confira "[Sobre os contêineres de serviço](/actions/automating-your-workflow-with-github-actions/about-service-containers#mapping-docker-host-and-service-container-ports)".

```yaml{:copy}
jobs:
  # Label of the runner job
  runner-job:
    # You must use a Linux environment when using service containers or container jobs
    runs-on: ubuntu-latest

    # Service containers to run with `runner-job`
    services:
      # Label used to access the service container
      postgres:
        # Docker Hub image
        image: postgres
        # Provide the password for postgres
        env:
          POSTGRES_PASSWORD: postgres
        # Set health checks to wait until postgres has started
        options: >-
          --health-cmd pg_isready
          --health-interval 10s
          --health-timeout 5s
          --health-retries 5
        ports:
          # Maps tcp port 5432 on service container to the host
          - 5432:5432
```

### Configurar as etapas

{% data reusables.actions.service-template-steps %}

```yaml{:copy}
steps:
  # Downloads a copy of the code in your repository before running CI tests
  - name: Check out repository code
    uses: {% data reusables.actions.action-checkout %}

  # Performs a clean installation of all dependencies in the `package.json` file
  # For more information, see https://docs.npmjs.com/cli/ci.html
  - name: Install dependencies
    run: npm ci

  - name: Connect to PostgreSQL
    # Runs a script that creates a PostgreSQL table, populates
    # the table with data, and then retrieves the data
    run: node client.js
    # Environment variables used by the `client.js` script to create
    # a new PostgreSQL table.
    env:
      # The hostname used to communicate with the PostgreSQL service container
      POSTGRES_HOST: localhost
      # The default PostgreSQL port
      POSTGRES_PORT: 5432
```

{% data reusables.actions.postgres-environment-variables %}

{% data reusables.actions.service-container-localhost %}

## Testar o contêiner de serviço do PostgreSQL

Você pode testar o seu fluxo de trabalho usando o seguinte script, que se conecta ao serviço do PostgreSQL e adiciona uma nova tabela com alguns dados de espaço reservado. Em seguida, o script imprime os valores armazenados na tabela do PostgreSQL no terminal. Seu script pode usar qualquer idioma desejado, mas este exemplo usa o Node.js e o módulo npm `pg`. Para obter mais informações, confira o [módulo npm pg](https://www.npmjs.com/package/pg).

Você pode modificar o *client.js* para incluir todas as operações do PostgreSQL necessárias para o fluxo de trabalho. Neste exemplo, o script se conecta ao serviço PostgreSQL, adiciona uma tabela ao banco de dados `postgres`, insere alguns dados de espaço reservado e recupera os dados.

{% data reusables.actions.service-container-add-script %}

```javascript{:copy}
const { Client } = require('pg');

const pgclient = new Client({
    host: process.env.POSTGRES_HOST,
    port: process.env.POSTGRES_PORT,
    user: 'postgres',
    password: 'postgres',
    database: 'postgres'
});

pgclient.connect();

const table = 'CREATE TABLE student(id SERIAL PRIMARY KEY, firstName VARCHAR(40) NOT NULL, lastName VARCHAR(40) NOT NULL, age INT, address VARCHAR(80), email VARCHAR(40))'
const text = 'INSERT INTO student(firstname, lastname, age, address, email) VALUES($1, $2, $3, $4, $5) RETURNING *'
const values = ['Mona the', 'Octocat', 9, '88 Colin P Kelly Jr St, San Francisco, CA 94107, United States', 'octocat@github.com']

pgclient.query(table, (err, res) => {
    if (err) throw err
});

pgclient.query(text, values, (err, res) => {
    if (err) throw err
});

pgclient.query('SELECT * FROM student', (err, res) => {
    if (err) throw err
    console.log(err, res.rows) // Print the data in student table
    pgclient.end()
});
```

O script cria uma conexão com o serviço PostgreSQL e usa as variáveis de ambiente `POSTGRES_HOST` e `POSTGRES_PORT` para especificar a porta ou o endereço IP do serviço PostgreSQL. Se `host` e `port` não estiverem definidos, o host padrão será `localhost` e a porta padrão será 5432.

O script cria uma tabela e preenche com dados de espaço reservado. Para testar se o banco de dados `postgres` contém os dados, o script imprime o conteúdo da tabela no log do console.

Ao executar este fluxo de trabalho, você verá a seguinte saída na etapa "Conectar ao PostgreSQL", que confirma que você criou com sucesso a tabela do PostgreSQL e adicionou dados:

```
null [ { id: 1,
    firstname: 'Mona the',
    lastname: 'Octocat',
    age: 9,
    address:
     '88 Colin P Kelly Jr St, San Francisco, CA 94107, United States',
    email: 'octocat@github.com' } ]
```
