# Alguns comandos úteis ao usar o sequelize para criar models


Observação: Para fins didáticos vamos evitar esse comando, pois o código dos arquivos gerados é pouco legível e segue um padrão que dificulta a escrita de testes, mas para seu conhecimento, é possível gerar um model através do seguinte comando:

```
npx sequelize model:generate --name User.model --attributes fullName:string
```

Caso seja necessário explicitar o nome da tabela, pode-se fazer isso apenas acrescentando um outro parâmetro na função do model, o tableName, como você pode ver mais https://sequelize.org/docs/v6/core-concepts/model-basics/#providing-the-table-name-directly.


# 😨 Chega de explicações! Vamos ver em código como fazemos uma migration!

➡️ Agora vamos gerar um novo arquivo, com apenas o “esqueleto” de uma migration, usando o seguinte comando no terminal:
```
npx sequelize migration:generate --name create-user
```

* ➡️ Com a migration criada, basta executarmos o seguinte comando pelo CLI:

```
npx sequelize db:migrate
```

* ➡️ Caso queira reverter uma migration use o seguinte comando:
```
npx sequelize db:migrate:undo
```

# Criando uma nova migration para alterar uma tabela já existente

* Então qual seria a forma correta de adicionar uma nova coluna em uma tabela já existente?

✔️ A resposta certa é: criar uma nova migration que permita alterar a tabela. Para isso, o objeto queryInterface possui funções específicas, que permitem criar uma nova coluna, remover uma coluna ou mesmo mudar o tipo de uma coluna que já existe. Nesse caso, o queryInterface abstrai o que a função ALTER TABLE faz no SQL. Deseja saber mais sobre ALTER TABLE e está com sua gestão de tempo em dia? Consulte o conteúdo adicional sobre o assunto.

Lembre-se que a tabela Users tem que estar criada para que os passos a seguir sejam executados com sucesso, portanto, se você reverteu a migration que a criava, refaça-a com o comando npx sequelize db:migrate.

➡️ Para criar uma outra migration para adicionar a coluna phoneNum na sua tabela Users, você deve criar um novo arquivo com o seguinte comando:

```
npx sequelize migration:generate --name add-column-phone-table-users
```

conteúdo adicional https://app.betrybe.com/learn/course/5e938f69-6e32-43b3-9685-c936530fd326/module/f04cdb21-382e-4588-8950-3b1a29afd2dd/section/49fbc95c-1115-4c96-aded-1cba096dc9ed/lesson/815abac9-1bdf-46f5-a0ec-7813141e560b


👀 De olho na dica: além de adicionar ou remover colunas, o objeto queryInterface também permite que você altere a estrutura de uma coluna, como seu tipo, valor default, entre outros detalhes, assim como o ALTER TABLE também permite. Você pode consultar esse link da documentação do Sequelize.
https://sequelize.org/docs/v6/other-topics/query-interface/

# Seeders
## ⭐ Agora chegou o momento de aprender a popular nosso banco de dados utilizando o Seeders.

Já aprendemos um jeito seguro de criar e recriar um banco de dados, e de acrescentar/excluir tabelas e colunas. Agora nós entraremos numa outra etapa!

Lembre-se que toda vez que executamos as migrations, nosso banco de dados é criado do zero, ou seja, sem dados dentro das tabelas.

* 📝Recapitulando: um seeder é usado para, basicamente, alimentar o banco de dados com informações necessárias para o funcionamento mínimo da aplicação.

As seeds seguem a mesma linha das migrations, portanto primeiramente vamos precisar executar a criação de uma nova seed pelo CLI:

```
npx sequelize seed:generate --name users
```

Para executar a seed, basta rodarmos o comando abaixo:

```
npx sequelize db:seed:all
```
Para reverter o seed, use o seguinte comando:

```
npx sequelize db:seed:undo:all
```
