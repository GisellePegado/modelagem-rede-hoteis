# Atributos Compostos (Composite Attributes)

## O que é

Um atributo composto é um atributo que pode ser subdividido em partes menores, cada uma com significado próprio. Em vez de armazenar um valor único como uma string genérica, o atributo composto é decomposto em sub-atributos que podem ser consultados, filtrados e ordenados individualmente.

O exemplo clássico é o endereço: "Rua das Flores, 123, Bairro Centro, São Paulo - SP, CEP 01000-000" parece um campo único, mas é composto por rua, número, bairro, cidade, estado e CEP — cada um com uso independente. Se o endereço for armazenado como uma string única, consultas como "todos os hóspedes do estado de SP" se tornam complexas. Decomposto, o filtro é simplesmente `WHERE estado = 'SP'`.

No MER, atributos compostos são representados por uma elipse conectada a outras elipses menores (os sub-atributos).

## Como é usado neste projeto

Duas entidades do MER possuem o atributo composto `endereco`: `Hotel` e `Hóspede`. Em ambas, o endereço é decomposto em:

```
endereco
  ├── rua
  ├── numero
  ├── complemento
  ├── bairro
  ├── CEP
  ├── cidade
  └── estado
```

Essa decomposição permite, por exemplo, agrupar hotéis por cidade ou filtrar hóspedes por estado — consultas comuns em sistemas de redes hoteleiras.

## Exemplo do projeto

```
Hóspede
  CPF (PK)
  nome
  telefone
  email
  endereco ← atributo composto
    rua, numero, complemento, bairro, CEP, cidade, estado
```

## Recursos para aprofundamento

- [GeeksForGeeks — Types of Attributes in ER Model](https://www.geeksforgeeks.org/types-of-attributes-in-er-model/) — explicação de todos os tipos de atributos com exemplos
