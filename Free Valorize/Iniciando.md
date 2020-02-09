# Iniciando aplicação

O free valorize é uma aplicação que foi desenvolvida em uma estrutura monolítica, ou seja, todo o código backend e frontend da aplicação se encontra em um mesmo pacote/repositório.

Para iniciar a aplicação em um ambiente de desenvolvimento são necessários algumas configurações iniciais.

Primeiro certifique-se que seu node está rodando na versão 8.9. Para saber disso basta executar o comando:

```properties
  node --version
```

Caso não esteja na versão correta, aconselho você a baixar uma ferramenta chamada **nvm**, onde você pode fazer o controle de versão do node que deseja utilizar.

Após instalar o nvm execute:

```properties
  nvm install 8.9
  nvm use 8.9
```

Depois de instalar o node em sua versão correta, você pode instalar as dependências do free valorize:

```properties
  npm install
```

Após instalar as dependências você precisa setar as variáveis de ambiente corretamente, no free valorize existe um arquivo chamado **staging.sh** dentro de uma pasta .env com todas as variáveis de ambiente necessárias para executar a aplicação.

Para definir esse arquivo como as variáveis de ambiente do sistema, execute:

```properties
  source .env/staging.sh
```

Após configurar as variaveis de ambiente, execute o comando para buildar e executar a aplicação:

```
  make run
```

Caso ocorra algum erro, vá no arquivo **./source/server/configuration/staging.js** procure as configurações da variável **server** e altere-o para:

```js
  {
    port: appEnv.port,
    host: 'http://localhost',
    forceHttps: false
  }
```

Apoś as alterações execute novamente o comando:

```
  make run
```
