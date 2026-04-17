# Entidade Associativa (Associative Entity)

## O que é

Uma entidade associativa — também chamada de entidade intermediária ou tabela de junção — é uma entidade criada para resolver relacionamentos do tipo **N:N** (muitos para muitos) entre duas entidades.

Relacionamentos N:N não podem ser representados diretamente em bancos de dados relacionais, porque não há uma coluna única onde se possa armazenar "vários valores de uma vez". A solução é criar uma terceira entidade que contém as chaves primárias das duas entidades relacionadas, formando uma chave composta. Essa entidade pode ainda carregar atributos próprios do relacionamento — informações que só fazem sentido quando as duas entidades estão juntas.

## Como é usado neste projeto

O relacionamento entre `Reserva` e `Quarto` é N:N: uma reserva pode incluir vários quartos, e um mesmo quarto pode aparecer em reservas diferentes em períodos distintos.

Para resolver isso, foi criada a entidade associativa `ReservaQuarto`, cuja chave primária é composta pelos dois identificadores:

```
ReservaQuarto
  idReserva  (PK + FK → Reserva)
  idQuarto   (PK + FK → Quarto)
```

Isso transforma o relacionamento N:N em dois relacionamentos 1:N:
- `Reserva` 1:N `ReservaQuarto`
- `Quarto` 1:N `ReservaQuarto`

## Exemplo do projeto

```
Reserva 1 inclui os quartos 101 e 205:
  ReservaQuarto: (idReserva=1, idQuarto=101)
  ReservaQuarto: (idReserva=1, idQuarto=205)

Quarto 101 aparece em reservas distintas:
  ReservaQuarto: (idReserva=1, idQuarto=101)
  ReservaQuarto: (idReserva=7, idQuarto=101)
```

## Recursos para aprofundamento

- [Vertabelo — Associative Entities in ER Diagrams](https://vertabelo.com/blog/association-tables/) — explicação com diagramas e exemplos reais
