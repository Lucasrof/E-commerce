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
4. **Serviço:** A partir da OS, calcula-se o valor de cada serviço, consultando-se uma tabela de referência de mão-de-obra;
5. **Peças:** O valor de cada peça também irá compor a OSO cliente autoriza a execução dos serviços;
6. **Equipe:** A mesma equipe avalia e executa os serviços;
7. **Mecânicos:** Os mecânicos possuem código, nome, endereço e especialidade;
8. **OS:** Cada OS possui: n°, data de emissão, um valor, status e uma data para conclusão dos trabalhos.

## Ferramentas Utilizadas

- MySQL Workbench

## Solução do Modelo EER

![Oficina EER](https://github.com/user-attachments/assets/a2bf0ad7-520e-4904-a553-436bf10ad2de)



### Desafios Propostos

### Desafio 1: Cliente PJ e PF
- Criadas duas novas entidades: **PessoaFísica** e **PessoaJurídica**.

**Tabela PessoaFísica:**
- `IdPessoaFísica` INT
- `CPF` VARCHAR(45)
- `Nome` VARCHAR(45)
- `Sobrenoome` VARCHAR(45)
- `Contatos` VARCHAR(45)

**Tabela PessoaJurídica:**
- `IdPessoaJurídica` INT
- `CNPJ` VARCHAR(45)
- `RazãoSocial` VARCHAR(45)
- `Telefone` VARCHAR(45)
- `Endereço` VARCHAR(45)


### Desafio 2: Clientes
- Criada a tabela **Clientes**, relacionada com as tabelas de **PessoaFisica**, **PessoaJurídica** (1,1).

**Tabela Clientes:**
- `IdClientes` INT
- `Data do Cadastrp` DATE
- `FK idPessoaFísica` INT
- `FK idPessoaJurídica` INT

### Desafio 3: Veículos
- Criada a tabela **Veículas**, relacionada com a tabela de **Clientes** e **Ordem de Serviço** (1,N), contendo informações sobre o Veículo e herdando as informações do cliente.

**Tabela Veículo:**
- `idVeículo` INT
- `PlacaVeículo` VARCHAR(45)
- `Modelo` VARCHAR(45)
- `Cor` VARCHAR(45)
- `FK idClientes` INT

### Desafio 4: Serviço
- Criada a tabela **Serviço**, relacionada com a tabela de **Custo Mão de Obra**, **Conserto**, **Revisão** (1,1), contendo as informações referentes ao serviço a ser realizado e herdando a tabela cliente.

**Tabela Serviço:**
- `idServiço` INT
- `FK idConserto` INT
- `FK idRevisão` INT
- `FK idClientes` VARCHAR(45)
- `FK idCusto Mão de Obra` INT

### Desafio 5: Peças
- Criada a tabela **Peça**, relacionada com a tabela de **Estoque** em 1,N, e com a tabela **Ordem de Serviço** em N,M.

**Tabela Peças:**
- `idPeça` INT
- `FK idEstoque` INT
**Relacionamento N,M com tabela "Ordem de Serviço":**
- `FK Id Ordem de Serviço` INT
- `FK idPeça` INT
- `FK idEstoque` INT

### Desafio 6 e 7: Mecânicos e Equipe Mecânicos
- Criada a tabela **Mecânicos** e **Equipe Mecânicos**, relacionadas em N,1. E a tabela **Equipe Mecânicos** em relacionamento 1,N com tabela **Ordem de Serviço**.

**Tabela Mecânicos:**
- `idMecânicos` INT
- `Código MAtrícula` VARCHAR(45)
- `Nome` VARCHAR(45)
- `Endereço` VARCHAR(45)
- `Especialidade` VARCHAR(45)
- `FK idEquipe Mecânicos` INT

**Tabela Equipe Mecânicos:**
- `idEquipe Mecânicos` INT
- `Especialidade da Equipe` VARCHAR(45)
- `Nome da Equipe` VARCHAR(45)


### Desafio 8: Ordem de Serviço
- Criada a tabela **Ordem de Serviço**, com a estrutura solicitada no desafio e herdando de veículos, equipe mecânica e clientes.

**Tabela Ordem de Serviço:**
- `idOrdem de Serviço` INT
- `Numero da OS` VARCHAR(45)
- `Data de Emissão` DATE
- `Valor da OS` FLOAT
- `Status` TINYINT
- `Data de Conclusão da OS` DATE
- `FK idEquipe Mecânicos` INT
- `FK idVeículos` INT
- `FK idClientes` INT
---

Sinta-se à vontade para fazer melhorias e ajustes no modelo, utilizando as boas práticas de modelagem e atendendo aos requisitos do cenário de e-commerce.
