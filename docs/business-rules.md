# Regras de Negócio — Rede de Hotéis

Regras fornecidas como base para a elaboração do Modelo Entidade-Relacionamento (MER).

---

## Entidades e Atributos

### Funcionário
| Atributo | Tipo | Restrição |
|----------|------|-----------|
| CPF | varchar | PK |
| nome | varchar | — |
| telefone | varchar | — |
| email | varchar | — |
| login | varchar | — |
| senha | varchar | — |
| idHotel | int | FK → Hotel |

### Hotel
| Atributo | Tipo | Restrição |
|----------|------|-----------|
| idHotel | int | PK |
| nome | varchar | — |
| categoria | varchar | — |
| telefone | varchar | — |
| email | varchar | — |
| endereco | composto | rua, numero, complemento, bairro, CEP, cidade, estado |

### Quarto
| Atributo | Tipo | Restrição |
|----------|------|-----------|
| idQuarto | int | PK |
| numeroLeitos | int | — |
| tipo | enum | standard, luxo ou suíte |
| precoDiaria | decimal | — |
| status | enum | disponível, ocupado ou manutenção |
| idHotel | int | FK → Hotel |

### Hóspede
| Atributo | Tipo | Restrição |
|----------|------|-----------|
| CPF | varchar | PK |
| nome | varchar | — |
| telefone | varchar | — |
| email | varchar | — |
| endereco | composto | rua, numero, complemento, bairro, CEP, cidade, estado |

### Reserva
| Atributo | Tipo | Restrição |
|----------|------|-----------|
| idReserva | int | PK |
| dataEntrada | date | — |
| dataSaida | date | — |
| status | enum | ativa, cancelada ou concluída |
| cpfFuncionario | varchar | FK → Funcionário |
| cpfHospede | varchar | FK → Hóspede |
| idPagamento | int | FK → Pagamento |

### Pagamento
| Atributo | Tipo | Restrição |
|----------|------|-----------|
| idPagamento | int | PK |
| formaPagamento | enum | cartão, pix ou dinheiro |
| dataPagamento | date | — |
| valorTotal | decimal | — |
| status | enum | pago ou pendente |

### ReservaQuarto *(entidade associativa)*
| Atributo | Tipo | Restrição |
|----------|------|-----------|
| idReserva | int | PK + FK → Reserva |
| idQuarto | int | PK + FK → Quarto |

---

## Regras de Relacionamento

- Um hotel possui **um ou vários** quartos
- **Um ou vários** funcionários trabalham em um hotel
- Um funcionário realiza **uma ou várias** reservas
- **Um ou vários** quartos fazem parte de **uma ou várias** reservas *(N:N — resolvido via entidade associativa ReservaQuarto)*
- Um hóspede pode fazer **uma ou várias** reservas
- Uma reserva gera **um** pagamento

---

## Restrições de Modelagem

- O MER considera somente as regras de negócio fornecidas — nenhuma entidade ou atributo adicional foi criado
- Entidades associativas seguem a representação padrão (Representação 1)
- Em cardinalidade (1,1), a chave estrangeira foi posicionada na entidade com maior número de chaves estrangeiras — por isso `idPagamento` está em `Reserva`, não em `Pagamento`
