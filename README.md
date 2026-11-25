# Oscar com MongoDB 🏆

Quantas vezes Natalie Portman foi indicada ao Oscar? Em quais anos os filmes de *Toy Story* ganharam prêmios? Nesta atividade do PROA, usei essas perguntas para praticar consultas, agregações e limpeza de dados no MongoDB.

O arquivo [OscarDb](./OscarDb) reúne os enunciados, minhas respostas e os comandos usados na coleção `OSCAR`. Na contagem inicial registrada na atividade, a coleção tinha **10.889 documentos** e **115 categorias distintas**.

## O que pratiquei

| Nível | Tema | O que explorei |
| --- | --- | --- |
| 1 | Primeiros passos | Contar documentos, listar categorias e identificar os anos das cerimônias. |
| 2 | Categorias | Agrupar indicações por categoria e comparar categorias de diferentes anos. |
| 3 | Atores e atrizes | Filtrar por nome para distinguir indicações de vitórias. |
| 4 | Vencedores históricos | Ordenar registros por ano para encontrar os primeiros vencedores. |
| 5 | Análise de indicações | Agrupar registros por indicado e identificar nomes recorrentes. |
| 6 | Análise de filmes | Cruzar título, ano e resultado para investigar filmes e franquias. |
| 7 | Atualização e limpeza | Converter textos em booleanos, padronizar títulos e remover registros sem título. |

## Como reproduzir uma consulta

1. Conecte o MongoDB Shell (`mongosh`) a uma instância local ou ao seu cluster no MongoDB Atlas.
2. Selecione o banco da atividade com `use nome_do_banco`, substituindo `nome_do_banco` pelo nome escolhido. Importe a base de indicações usada no exercício para uma coleção chamada `OSCAR`.
3. Abra [OscarDb](./OscarDb) e copie o comando da questão que deseja testar. O arquivo intercala explicações, resultados e código, então execute uma consulta por vez.

Por exemplo, para ver **em quais anos e por quais filmes Natalie Portman foi indicada**, filtre pelo nome, selecione os campos da resposta e ordene pelo ano da cerimônia:

```javascript
db.OSCAR.find(
  { nome_do_indicado: "Natalie Portman" },
  { _id: 0, ano_cerimonia: 1, nome_do_filme: 1 }
).sort({ ano_cerimonia: 1 })
```

Na questão 2.1, use `db.OSCAR.aggregate(...)` para executar o agrupamento por categoria. Na questão 1.6, preencha o `insertMany` com os documentos das indicações de 2025 e 2026 antes de executá-lo. Para praticar o nível 7, use uma cópia da coleção, pois `updateMany` e `deleteMany` alteram os dados usados nas consultas anteriores.
