# Bank Transactions Analysis

Projeto de análise de transações bancárias utilizando Python, SQL, SQLite e Power BI.

## Objetivo

O objetivo deste projeto é analisar uma base de transações bancárias, entender o comportamento transacional dos clientes e identificar possíveis operações suspeitas com base em regras simples de negócio.

## Ferramentas Utilizadas

- Python
- Pandas
- SQLite
- SQL
- Power BI
- DAX
- Jupyter Notebook
- Git e GitHub

## Arquitetura do Projeto

```text
bank_transactions_analysis/
│
├── data/
│   ├── raw/
│   │   └── bank_transactions.csv
│   └── processed/
│       └── bank_transactions_clean.csv
│
├── database/
│   └── bank_transactions.db
│
├── notebooks/
│   └── 01_analise_exploratoria.ipynb
│
├── dashboard/
│   ├── bank_transactions_dashboard.pbix
│   ├── dashboard_preview.png
│   └── medidas_dax.md
│
├── src/
├── requirements.txt
├── .gitignore
└── README.md
```

## Etapas do Projeto

1. Organização da base de dados
2. Tratamento dos dados com Python
3. Criação de colunas auxiliares de tempo
4. Criação de banco de dados SQLite
5. Consultas SQL para análise
6. Criação de medidas DAX
7. Desenvolvimento de dashboard no Power BI
8. Publicação no GitHub

## Tratamento dos Dados

Durante o tratamento da base foram realizadas as seguintes etapas:

- Leitura do arquivo CSV
- Verificação de dados nulos
- Verificação de dados duplicados
- Conversão da coluna de data
- Criação das colunas de ano, mês, dia, hora e dia da semana
- Exportação da base tratada

## Banco de Dados

A base tratada foi carregada em um banco SQLite, em uma tabela chamada `transactions`.

Foram realizadas consultas SQL para analisar:

- Total de transações
- Valor total movimentado
- Ticket médio
- Transações por canal
- Transações por tipo
- Valor movimentado por cidade
- Saldo médio por ocupação

## Dashboard

O dashboard foi criado no Power BI com foco em indicadores de transações bancárias e identificação de possíveis operações suspeitas.

### Indicadores principais

- Total de transações
- Valor total movimentado
- Ticket médio
- Total de contas
- Percentual de transações suspeitas

### Visualizações

- Transações por canal
- Transações por tipo
- Transações normais x suspeitas
- Top 10 cidades por valor movimentado
- Evolução de transações por mês

## Preview do Dashboard

![Dashboard Preview](dashboard/dashboard_preview.png)

## Regra de Transação Suspeita

Foi criada uma regra simples para classificar transações como suspeitas:

```DAX
Status Transação = 
IF(
    bank_transactions_clean[LoginAttempts] >= 3 
        || bank_transactions_clean[TransactionAmount] > 1000;
    "Suspeita";
    "Normal"
)
```

Essa regra considera como suspeitas transações com muitas tentativas de login ou valores acima de 1000.

## Medidas DAX

As principais medidas criadas no Power BI estão documentadas no arquivo:

```text
dashboard/medidas_dax.md
```

## Como Rodar o Projeto

### 1. Clone o repositório

```bash
git clone https://github.com/seu-usuario/bank_transactions_analysis.git
```

### 2. Acesse a pasta do projeto

```bash
cd bank_transactions_analysis
```

### 3. Crie o ambiente virtual

```bash
py -m venv venv
```

### 4. Ative o ambiente virtual

```bash
venv\Scripts\activate
```

### 5. Instale as dependências

```bash
py -m pip install -r requirements.txt
```

### 6. Abra o Jupyter Notebook

```bash
jupyter notebook
```

### 7. Execute o notebook

Abra o arquivo:

```text
notebooks/01_analise_exploratoria.ipynb
```

## Principais Insights

- O dashboard permite acompanhar o volume total de transações.
- É possível identificar os canais mais utilizados pelos clientes.
- Algumas cidades concentram maior valor movimentado.
- A regra de suspeita ajuda a destacar transações com comportamento fora do padrão.
- O projeto demonstra um fluxo completo de análise de dados, desde o tratamento até a visualização.

## Conclusão

Este projeto simula um processo completo de análise de transações bancárias, utilizando Python para tratamento dos dados, SQL para análise, SQLite como banco de dados e Power BI para visualização.

O resultado final é um dashboard que auxilia na análise de comportamento transacional e na identificação inicial de possíveis operações suspeitas.