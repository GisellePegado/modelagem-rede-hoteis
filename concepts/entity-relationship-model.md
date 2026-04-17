# Modelo Entidade-Relacionamento (Entity-Relationship Model)

## O que é

O Modelo Entidade-Relacionamento (MER) é uma representação visual e abstrata da estrutura de dados de um sistema. Criado por Peter Chen em 1976, ele descreve o domínio de um problema usando três elementos principais: **entidades** (as "coisas" do mundo real que queremos armazenar), **atributos** (as características dessas coisas) e **relacionamentos** (como as entidades se conectam entre si).

O MER é chamado de modelo **conceitual** porque existe no nível das ideias — independente de qualquer banco de dados específico. É a primeira etapa da modelagem: antes de pensar em tabelas, colunas ou SQL, define-se o que existe e como se relaciona.

## Como é usado neste projeto

O MER deste projeto representa o domínio de uma rede de hotéis com seis entidades principais: `Funcionário`, `Hotel`, `Quarto`, `Hóspede`, `Reserva` e `Pagamento`. Cada entidade foi identificada a partir das regras de negócio fornecidas.

O diagrama usa a notação clássica de Chen: retângulos para entidades, elipses para atributos, losangos para relacionamentos e linhas com cardinalidades nas extremidades.

## Exemplo do projeto

```
Entidade:      Hóspede
Atributos:     CPF (PK), nome, telefone, email, endereco (composto)
Relacionamento: Faz → Reserva  (cardinalidade 1:N)
```

## Recursos para aprofundamento

- [IBM — Entity-Relationship Diagrams](https://www.ibm.com/topics/entity-relationship-diagram) — introdução ao conceito com exemplos visuais
- [Lucidchart — ER Diagram Tutorial](https://www.lucidchart.com/pages/er-diagrams) — guia prático com notações diferentes
