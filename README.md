# Alguns comandos úteis ao usar o sequelize para criar models


Observação: Para fins didáticos vamos evitar esse comando, pois o código dos arquivos gerados é pouco legível e segue um padrão que dificulta a escrita de testes, mas para seu conhecimento, é possível gerar um model através do seguinte comando:

```
npx sequelize model:generate --name User.model --attributes fullName:string
```

Caso seja necessário explicitar o nome da tabela, pode-se fazer isso apenas acrescentando um outro parâmetro na função do model, o tableName, como você pode ver mais https://sequelize.org/docs/v6/core-concepts/model-basics/#providing-the-table-name-directly.
