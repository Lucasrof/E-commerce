# Refinando um Projeto Conceitual de Banco de Dados – E-COMMERCE

**Bootcamp:** Suzano - Análise de Dados com Power BI  
**Instrutora:** Juliana Mascarenhas

## Descrição do Desafio

Modelamos juntos um contexto reduzido de e-commerce. Agora é a sua vez de refinar o modelo. Você pode escolher a ferramenta de modelagem para realizar o desafio. No entanto, se optar por uma variação do modelo entidade-relacionamento (como MySQL Workbench ou DBDesigner), será necessário especificar corretamente as chaves primárias (PK) e chaves estrangeiras (FK). Apesar desse conceito não ser utilizado na modelagem conceitual, exploramos brevemente suas definições. 

### Entregável:
O entregável será o esquema conceitual refinado para o cenário de E-commerce.

## Objetivos e Regras

Refine o modelo apresentado anteriormente acrescentando os seguintes pontos:

1. **Cliente PJ e PF**: Uma conta pode ser PJ (Pessoa Jurídica) ou PF (Pessoa Física), mas não pode conter ambas as informações.
2. **Pagamento**: O cliente pode cadastrar mais de uma forma de pagamento para o pedido.
3. **Entrega**: O pedido deve possuir status e código de rastreio para acompanhamento.

## Ferramentas Utilizadas

- MySQL Workbench

## Solução do Modelo EER

![E-Commerce](https://github.com/user-attachments/assets/c29ad9cf-d9ec-4664-be73-475f9b98d4bc)

### Refinamentos Propostos

### Desafio 1: Cliente PJ e PF
- Criadas duas novas entidades: **PessoaFísica** e **PessoaJurídica**.

**Tabela PessoaFísica:**
- `IdPessoaFísica` INT
- `Nome` VARCHAR(45)
- `DataNascimento` DATE
- `CPF` VARCHAR(45)

**Tabela PessoaJurídica:**
- `IdPessoaJurídica` INT
- `RazãoSocial` VARCHAR(45)
- `DataCadastroPJ` DATETIME
- `CNPJ` VARCHAR(45)

### Desafio 2: Pagamento
- Criada a tabela **Pagamento**, relacionada com a tabela de **Pedido** (1,1), permitindo o cadastro de múltiplas formas de pagamento.

**Tabela Pagamento:**
- `IdPagamento` INT
- `FormaPagamento` VARCHAR(45)
- `FK Pedido_IdPedido` INT
- `FK Pedido_Cliente_IdCliente` INT

**Tabela Cartão:**
- `IdCartão` INT
- `TipoCartão` TINYINT
- `NumeroCartão` VARCHAR(45)
- `Valor` FLOAT
- `FK Pagamento_IdPagamento` INT

**Tabela Boleto:**
- `IdBoleto` INT
- `Parcelas` INT
- `DataVencimento` DATE
- `Valor` FLOAT
- `FK Pagamento_IdPagamento` INT

### Desafio 3: Entrega
- Criada a tabela **Entrega**, relacionada com a tabela de **Pedido** (1,1), contendo informações sobre status e código de rastreio.

**Tabela Entrega:**
- `IdEntrega` INT
- `DataPedido` DATE
- `DataEnvio` DATE
- `DataEntregue` DATE
- `EnderecoEntrega` VARCHAR(45)
- `Recebido` TINYINT
- `FK Pedido_IdPedido` INT
- `FK Pedido_Cliente_IdCliente` INT

---

Sinta-se à vontade para fazer melhorias e ajustes no modelo, utilizando as boas práticas de modelagem e atendendo aos requisitos do cenário de e-commerce.
