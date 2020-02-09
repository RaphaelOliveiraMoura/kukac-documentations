# Estrutura Gestão e Inovações

Esse é um projeto que podemos dividir em três partes:

- Frontend (Construido em ReactJS)
- Backend (Construido em NodeJS)
- Relatório (Construido com HTML, CSS e JS vanilla)

## Frontend

Para executar o frontend da aplicação:

Primeiro instale as dependências:

```properties
  yarn install
```

Configure as variáveis de ambiente assim como descrito no arquivo .env.example

Logo após:

Para executar em modo de desenvolvimento:

```properties
  yarn dev
```

Para executar em modo de produção:

```properties
  yarn start
```

## Backend

Prerequisitos:

- Instalar dependências
- Configurar as variáveis de ambiente
- Ter um banco de dados Postgres configurado

Nesse projeto esta configurado o docker, logo você pode iniciar o banco Postgres em um container facilmente.

Para isso execute:

```porperties
  docker-compose up -d
```

Para configurar o banco de dados:

```properties
  yarn sequelize db:create
  yarn sequelize db:migrate
  yarn sequelize db:seed:all
```
