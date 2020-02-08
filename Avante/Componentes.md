# Avante

O projeto do avante consiste em várias **aplicações/microserviços** que funcionam isoladamente.

Abaixo estão listados todos eles:

## Componente de extração

Componente responsável por realizar a comunicação com a **API do Intellims** buscando os posts crawleados e salvando-os em uma collection chamada **"intellims_data"** dentro do **mongoDB**.

Esse componente é executado utilizando um schedule/agendamente, ou seja, de tempo em tempo ele faz a busca na API do Intellims por novos dados e salva eles no banco de dados.

O projeto foi desenvolvido com JavaScript puro, logo para executa-lo basta ter suas dependencias instaladas:

```properties
  npm install
  or
  yarn install
```

Configurar suas variáveis de ambiente, criando um arquivo **.env** no root da aplicação e preenchendo seus dados assim como o arquivo **.env.example**.

Após isso basta executar a aplicação:

```properties
  npm start
  or
  yarn start
```

## Componente de enriquecimento

Esse componente é responsável por pegar os dados que foram crawleados e salvos pelo componente de extração e envialos para uma ferramenta da IBM **(NLU)** para enriquecer esses dados e assim salva-los novamente no banco de dados, porém em outra collection chamada **"enriched_data"**.

Assim como o componente anterior, esse componente é executado via schedule, e esse **schedule** é configurado por **variável de ambiente** no arquivo .env ou nas configurações de ambiente da IBM.

## Componente de limpeza

Outro componente que é executado via schedule, porém sua unica função é **limpar as collections do banco MongoDB** de tempos em tempos. Como são salvos um grande volume de dados, e esses dados são estruturados e salvos em outro banco, não faz sentido mante-los salvos.

## Componente de transformação

Esse é um dos componentes "core" de todo o sistema. Ele é responsável por pegar os dados enriquecidos pelo componente de enriquecimento e verificar se aquele post é relevante ou não, e logo após salva-lo em um banco relacional **(Postgres)**. Relacionando o **post** com a **pessoa** que o publicou levando em consideração sua **localização**.

Esse também é um componente que é executado via schedule.

## Componente de cadastro

Diferente dos componentes listados até então, esse componente não é executado via schedule, ele é uma **API** que disponibilizara acesso e funcionalidades para uso do frontend da aplicação.

Atividades como **criação e edição** de usuários são disponibilizadas por esse componente.

## Componente de relatório

Assim como o componente de cadastro, esse componente é uma **API** que irá disponibilizar para o frontend dados.

Porém suas funcionalidades são mais voltados para disponibilizar acesso a recursos, como **listagem de posts, listagem de pessoas, listagem de usuários**. Tudo relacionado a consultas é de responsabilidade deste componente.

## Frontend

É a interface gráfica disponibilizada para o cliente final utilizar. Foi desenvolvida utilizando **React**, junto com uma framework chamada **React Admin**.

Para executá-lá são os mesmos processos de executar uma aplicação Node convencional.

Esse componente só irá se comunicar com as APIs de cadastro e relatório listadas acima.

---

```
OBS: Para executar qualquer um desses componentes é necessário ter as variáveis de ambiente configuradas, se em algum deles não existir o arquivo .env.example basta acessar a aplicação da IBM e verificar quais variáveis estão sendo utilizadas.
```
