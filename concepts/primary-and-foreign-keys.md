# Chaves Primárias e Estrangeiras (Primary and Foreign Keys)

## O que é

**Chave primária (Primary Key / PK)** é o atributo — ou conjunto de atributos — que identifica de forma única cada registro de uma entidade. Nenhum valor de PK pode se repetir ou ser nulo. É o "endereço" de um registro dentro da tabela.

**Chave estrangeira (Foreign Key / FK)** é um atributo em uma entidade que referencia a chave primária de outra entidade. É o mecanismo que cria o relacionamento físico entre tabelas, garantindo que um registro não aponte para algo que não existe — propriedade chamada de **integridade referencial**.

Juntas, PKs e FKs formam a espinha dorsal de qualquer banco de dados relacional: a PK garante unicidade dentro da tabela; a FK garante consistência entre tabelas.

## Como é usado neste projeto

Cada entidade do MER tem sua chave primária definida:

| Entidade | Chave Primária | Tipo |
|----------|---------------|------|
| Hotel | `idHotel` | Inteiro autogerado |
| Funcionário | `CPF` | Identificador natural (CPF único) |
| Quarto | `idQuarto` | Inteiro autogerado |
| Hóspede | `CPF` | Identificador natural (CPF único) |
| Reserva | `idReserva` | Inteiro autogerado |
| Pagamento | `idPagamento` | Inteiro autogerado |
| ReservaQuarto | `idReserva` + `idQuarto` | Chave composta (ambas FKs) |

As chaves estrangeiras seguem a regra da cardinalidade: em relacionamentos 1:1, a FK vai para a entidade com mais FKs. Por isso `idPagamento` fica em `Reserva` (que já carrega `cpfFuncionario` e `cpfHospede`), e não em `Pagamento`.

## Exemplo do projeto

```
Reserva
  idReserva    (PK)
  cpfFuncionario (FK → Funcionário.CPF)
  cpfHospede     (FK → Hóspede.CPF)
  idPagamento    (FK → Pagamento.idPagamento)  ← 1:1, fica em Reserva pois já tem mais FKs
```

## Recursos para aprofundamento

- [W3Schools — SQL Primary Key](https://www.w3schools.com/sql/sql_primarykey.asp) — sintaxe e exemplos práticos
- [W3Schools — SQL Foreign Key](https://www.w3schools.com/sql/sql_foreignkey.asp) — integridade referencial na prática
