# 🩺 NY Health Data Pipeline (Databricks – Silver Table)

<br>

## Visão Geral

Este projeto implementa um pipeline em PySpark no **Databricks** para consumir, transformar e armazenar dados públicos de saúde do estado de Nova York. Os dados são inicialmente obtidos em formato JSON bruto por meio da API:

> 🔗 https://health.data.ny.gov/api/views/jxy9-yhdk/rows.json

---

<br>

## Etapas do Processo

### 1. Coleta de Dados
- Os dados são coletados com a biblioteca `requests`, consumindo diretamente o endpoint da API pública.
- A resposta vem como JSON aninhado, contendo os dados reais sob a chave `"data"` e os nomes das colunas sob `"meta.view.columns"`.

<br>

### 2. Limpeza e Transformação
- Os nomes das colunas são extraídos e associados às linhas de dados.

<br>

### 3. Conversão de Campos Temporais
- A coluna `created_at`, fornecida como um inteiro (Unix timestamp em segundos), é convertida para `timestamp` com `from_unixtime()` e `to_date()`.

<br>

### 4. Armazenamento em Tabela Silver
- O DataFrame final é salvo como uma tabela, respeitando os princípios da camada *Silver*: dados limpos, estruturados e prontos para consumo analítico.

📁 Tabela criada: `health_silver.ny_health_data`
