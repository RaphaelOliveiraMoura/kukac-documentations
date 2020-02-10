# Recomendações

Nesta documentação estará listada algumas boas práticas que devem ser levadas em consideração no desenvolvimento das nossas aplicações.

## Variáveis de ambiente

Qualquer dado sensível / credenciais de serviços nunca devem ficar hard code na aplicação, todos devem ser configurados para o ambiente que a aplicação estiver executando.

Em nossas aplicações geralmente utilizamos uma lib chamada **dotenv**, que pega os valores do arquivo .env e seta dinamicamente como variável de ambiente da aplicação.

OBS: O arquivo .env NUNCA deve estar presente no repositório online. Sempre lembre de adiciona-lo ao **.gitignore**.

## Utilizar algum linting

O JavaScript é uma linguagem que deixa muito aberto a forma de escrever código, e por ser uma linguagem interpretada conseguimos sempre rodar a aplicação mesmo ela tendo algum erro (só iremos encontrar o erro quando o código executar naquela parte). Por isso e outros fatores de padronização, é aconselhado utilizar alguma ferramenta de linting para te alertar de possíveis erros e desvio de padronização que nós desenvolvedores cometemos frequentemente.

Recomendo utilizar ESLint + Prettier + EditorConfig para fazer uma base sólida com suas próprias configurações de estilos da sua aplicação. Assim você mantem uma padronização de código entre toda sua equipe.

## Configurar migrations e seeders

Para qualquer projeto que utilize um banco de dados, é bom deixarmos configurados migrations (que geram a estrutura do banco) e seeders (que criam dados iniciais padrões dentro do banco de dados). Isso para que qualquer novo desenvolvedor consiga replicar o banco facilmente em sua máquina para realizar testes sem afetar qualquer ambiente externo.
