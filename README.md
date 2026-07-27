# Dataset de Vendas para Portfólio

## Ficheiro principal

`vendas_loja.csv`

- Linhas: 1428
- Pedidos distintos planeados: 760
- Período: janeiro de 2024 a dezembro de 2025
- Moeda dos preços: euro (€)
- Separador do CSV: vírgula
- Decimal: ponto

## Objetivo

Este dataset sintético foi criado para praticar:

- carregamento de CSV com Pandas;
- inspeção e limpeza de dados;
- tratamento de valores ausentes;
- remoção de duplicados;
- conversão de datas e números;
- agrupamentos com `groupby`;
- cálculo de faturamento e ticket médio;
- análise por produto, mês, categoria e região;
- criação de gráficos e dashboard.

## Dicionário de dados

| Coluna | Descrição |
|---|---|
| `id_linha` | Identificador da linha do pedido |
| `id_pedido` | Identificador do pedido; um pedido pode ter várias linhas |
| `data_venda` | Data do pedido |
| `cliente_id` | Identificador do cliente |
| `produto` | Nome do produto |
| `categoria` | Categoria do produto |
| `quantidade` | Quantidade comprada na linha |
| `preco_unitario` | Preço unitário antes do desconto |
| `desconto_percentual` | Percentagem de desconto |
| `forma_pagamento` | Meio de pagamento |
| `cidade` | Cidade da venda |
| `regiao` | Região da venda |
| `status_pedido` | Concluído, Cancelado ou Devolvido |

## Atenção

O dataset contém intencionalmente alguns:

- valores ausentes;
- registos duplicados;
- datas inválidas;
- quantidades iguais a zero ou negativas;
- pedidos cancelados e devolvidos.

Esses problemas fazem parte do exercício. Não remova dados automaticamente sem antes decidir e documentar a regra de negócio.

## Fórmulas sugeridas

Receita bruta da linha:

```python
df["receita_bruta"] = df["quantidade"] * df["preco_unitario"]
```

Receita líquida após desconto:

```python
df["receita_liquida"] = (
    df["quantidade"]
    * df["preco_unitario"]
    * (1 - df["desconto_percentual"] / 100)
)
```

Para analisar vendas efetivamente realizadas, uma regra inicial possível é utilizar apenas pedidos com status `Concluído`.

## Primeiras perguntas

1. Quantas linhas e colunas existem?/
2. Quais colunas possuem valores ausentes?/
3. Quantos registos estão duplicados?
4. Qual foi o faturamento líquido dos pedidos concluídos?
5. Qual foi o ticket médio por pedido?
6. Quais produtos geraram mais receita?
7. Quais meses tiveram maior faturamento?
8. Quais regiões ficaram abaixo da média?
9. Qual categoria apresentou maior crescimento de 2024 para 2025?
