# Cardinalidade (Cardinality)

## O que é

Cardinalidade define **quantas instâncias** de uma entidade podem se relacionar com quantas instâncias de outra entidade. É expressa como um par de valores mínimo e máximo — por exemplo, `(1,1)` significa "no mínimo um, no máximo um", e `(1,n)` significa "no mínimo um, sem limite máximo".

Os três tipos principais de cardinalidade são:

- **1:1** — um registro de A se relaciona com exatamente um registro de B (e vice-versa)
- **1:N** — um registro de A se relaciona com vários de B, mas cada B pertence a apenas um A
- **N:N** — vários registros de A se relacionam com vários de B

A cardinalidade é uma das decisões mais importantes na modelagem porque impacta diretamente como as chaves estrangeiras serão distribuídas entre as tabelas — e, consequentemente, como as consultas SQL serão escritas.

## Como é usado neste projeto

O projeto usa os três tipos de cardinalidade:

| Relacionamento | Cardinalidade | Interpretação |
|----------------|:---:|---------------|
| Hotel → Quarto | 1:N | Um hotel tem vários quartos; cada quarto pertence a um hotel |
| Funcionário → Hotel | N:1 | Vários funcionários trabalham num hotel; cada funcionário trabalha num hotel |
| Hóspede → Reserva | 1:N | Um hóspede pode ter várias reservas; cada reserva pertence a um hóspede |
| Reserva → Pagamento | 1:1 | Cada reserva gera exatamente um pagamento |
| Reserva ↔ Quarto | N:N | Uma reserva pode incluir vários quartos; um quarto pode aparecer em várias reservas |

A cardinalidade 1:1 entre `Reserva` e `Pagamento` determinou que a chave estrangeira `idPagamento` ficou em `Reserva` — a entidade com mais chaves estrangeiras, seguindo a regra do MER.

## Exemplo do projeto

```
Reserva (1,n) ←→ (n,1) Quarto

Uma mesma reserva pode incluir múltiplos quartos (suíte + quarto standard).
Um mesmo quarto pode estar em reservas diferentes em períodos distintos.
→ Cardinalidade N:N → resolvida com entidade associativa ReservaQuarto.
```

## Recursos para aprofundamento

- [Database Design — Cardinality](https://opentextbc.ca/dbdesign01/chapter/chapter-8-entity-relationship-model/) — capítulo completo sobre MER e cardinalidade
