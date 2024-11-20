# Construindo um Esquema Conceitual para Banco De dados - Oficina

**Bootcamp:** Suzano - Análise de Dados com Power BI  
**Instrutora:** Juliana Mascarenhas

## Descrição do Desafio

Agora você irá criar um esquema conceitual do zero. A partir da narrativa fornecida você será capaz de criar todas as entidades, relacionamentos e atributos.

### Entregável:
"Crie o esquema conceitual para o contexto de oficina com base na narrativa fornecida"

## Objetivos e Regras

Construa o modelo solicitado de acordo com as regras de negócio e implementando os seguintes pontos:

**Narrativa:**
1. **Sistema:** Sistema de controle e gerenciamento de execução de ordens de serviço em uma oficina mecânica;
2. **Clientes:** Clientes levam veículos à oficina mecânica para serem consertados ou para passarem por revisões  periódicas;
3. **Veículo:** Cada veículo é designado a uma equipe de mecânicos que identifica os serviços a serem executados e preenche uma OS com data de entrega;
4. **OS:** A partir da OS, calcula-se o valor de cada serviço, consultando-se uma tabela de referência de mão-de-obra;
6. **Peças:** O valor de cada peça também irá compor a OSO cliente autoriza a execução dos serviços;
7. **Equipe:** A mesma equipe avalia e executa os serviços;
8. **Mecânicos:** Os mecânicos possuem código, nome, endereço e especialidade;
9. **OS:** Cada OS possui: n°, data de emissão, um valor, status e uma data para conclusão dos trabalhos.

## Ferramentas Utilizadas

- MySQL Workbench

## Solução do Modelo EER




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
