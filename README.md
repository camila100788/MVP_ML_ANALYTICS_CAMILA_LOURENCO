# MVP — Machine Learning & Analytics

## Segmentação de Clientes em E-commerce com K-Means

Este projeto foi desenvolvido como parte do MVP de **Machine Learning & Analytics** e tem como objetivo criar uma segmentação simples de clientes usando o algoritmo **K-Means**.

A proposta é analisar o comportamento de compra dos clientes de uma base de pedidos de e-commerce e agrupá-los em perfis semelhantes, considerando indicadores como quantidade de pedidos, valor total gasto, ticket médio e recência da última compra.

---

## Informações do projeto

**Nome:** Camila de Cássia Lourenço dos Santos  
**Matrícula:** 4052025001771  
**Data:** 05/07/2026  

**Dataset:** E-commerce Orders Dataset 2026 | SCRA  
**Fonte:** https://www.kaggle.com/datasets/mmumairkhattak/e-commerce-orders-dataset-2026-scra  
**Tipo de problema:** Clusterização

---

## Objetivo

O objetivo do projeto é identificar grupos de clientes com perfis semelhantes a partir do comportamento de compra.

Para isso, foram utilizadas variáveis como:

- quantidade de pedidos;
- valor total gasto;
- ticket médio;
- recência da última compra;
- quantidade de categorias compradas.

Como o problema é de **aprendizado não supervisionado**, não existe uma variável-alvo para prever. O foco é encontrar padrões nos dados e criar grupos de clientes com características parecidas.

---

## Hipóteses iniciais

Antes da modelagem, foram consideradas algumas hipóteses simples:

1. Clientes com maior quantidade média de pedidos tendem a ter maior valor total gasto.
2. Clientes com maior valor total médio podem representar um perfil de maior valor para o negócio.
3. Clientes com maior ticket médio podem indicar um grupo com compras de maior valor.
4. Clientes com menor recência, ou seja, que compraram há menos tempo, podem indicar maior engajamento.

Essas hipóteses foram avaliadas de forma exploratória, comparando os indicadores médios dos clusters gerados pelo modelo.

---

## Etapas do projeto

O notebook foi organizado nas seguintes etapas:

1. Instalação e importação das bibliotecas;
2. Carregamento dos dados pelo Kaggle;
3. Entendimento inicial da base;
4. Padronização dos nomes das colunas;
5. Definição das principais colunas usadas na análise;
6. Tratamento dos dados;
7. Análise exploratória dos dados;
8. Criação da base analítica por cliente;
9. Seleção e padronização das variáveis;
10. Escolha do número de clusters;
11. Treinamento do modelo K-Means;
12. Análise do perfil dos clusters;
13. Avaliação das hipóteses com base nos clusters;
14. Visualização dos clusters com PCA;
15. Nomeação dos segmentos;
16. Recomendações de negócio;
17. Exportação da base final segmentada.

---

## Dataset

A base utilizada contém registros de pedidos de e-commerce, com informações sobre clientes, produtos, datas, valores, pagamentos, entregas e comportamento de compra.

Entre os principais atributos utilizados no projeto estão:

- `customer_id`: identificação do cliente;
- `order_id`: identificação do pedido;
- `order_date`: data do pedido;
- `order_amount`: valor do pedido;
- `quantity`: quantidade comprada;
- `product_category`: categoria do produto.

A base inicial possui **30.000 registros de pedidos** e **8.683 clientes únicos**, sem valores nulos nas colunas analisadas.

---

## Preparação dos dados

Durante a preparação dos dados, foram realizadas as seguintes ações:

- remoção de possíveis duplicidades;
- conversão da data do pedido para formato de data;
- conversão dos campos numéricos utilizados na análise;
- filtragem de registros válidos;
- criação de uma base consolidada por cliente.

A base por cliente foi criada para que cada linha representasse um cliente, contendo seus principais indicadores de compra.

---

## Variáveis criadas por cliente

Para aplicar a clusterização, foram criadas as seguintes variáveis:

- `qtd_pedidos`: quantidade de pedidos realizados pelo cliente;
- `valor_total`: valor total gasto pelo cliente;
- `ticket_medio`: valor médio gasto por pedido;
- `ultima_compra`: data da última compra;
- `recencia_dias`: quantidade de dias desde a última compra;
- `qtd_categorias`: quantidade de categorias diferentes compradas.

Essas variáveis foram escolhidas por serem simples, interpretáveis e relacionadas ao comportamento de compra dos clientes.

---

## Modelo utilizado

O algoritmo escolhido foi o **K-Means**, por ser uma técnica simples, bastante utilizada em problemas de segmentação e de fácil interpretação.

Como este projeto é um MVP, o foco foi criar uma primeira versão da segmentação, comparando diferentes valores de `k` para encontrar uma quantidade adequada de grupos.

Como o problema é de clusterização, não foi utilizada uma divisão tradicional entre treino e teste. A avaliação foi feita com métricas próprias para agrupamento.

---

## Avaliação do número de clusters

Para escolher o número de clusters, foram utilizados:

- **Método do Cotovelo**, para avaliar a compactação dos grupos;
- **Silhouette Score**, para avaliar a separação entre os clusters.

Com base nos resultados, foi escolhido `k = 2`, mantendo uma segmentação simples e fácil de interpretar.

---

## Resultados

Após o treinamento do K-Means, os clientes foram divididos em dois grupos:

- **Cluster 0:** clientes com maior média de pedidos, maior valor total médio, maior ticket médio e menor recência. Esse grupo representa clientes mais ativos e com maior valor para o negócio.
- **Cluster 1:** clientes com menor valor médio gasto, menor frequência de pedidos e maior tempo desde a última compra. Esse grupo representa clientes com menor engajamento recente.

Os clusters foram nomeados como:

- **Clientes de maior valor**;
- **Clientes de menor valor**.

---

## Recomendações de negócio

Com base na segmentação, algumas ações podem ser consideradas:

- Para clientes de maior valor: criar ações de fidelização, ofertas exclusivas e benefícios para manter esses clientes ativos.
- Para clientes de menor valor: enviar campanhas de incentivo, cupons e comunicações personalizadas para estimular novas compras.

Essas ações mostram como a segmentação pode apoiar estratégias de marketing, retenção e relacionamento com clientes.

---

## Limitações

Apesar de a base estar completa e sem valores nulos nas colunas analisadas, algumas limitações devem ser consideradas:

- a análise considera apenas o histórico disponível no dataset;
- fatores externos, como campanhas de marketing e mudanças de preço, não foram considerados;
- os segmentos foram avaliados de forma exploratória;
- não foram aplicados testes estatísticos para validação das hipóteses.

---

## Próximos passos

Como próximos passos, seria possível:

- testar outros algoritmos de clusterização, como DBSCAN ou Cluster Hierárquico;
- incluir novas variáveis de comportamento dos clientes;
- comparar os segmentos com métricas de negócio;
- validar os grupos com uma análise mais detalhada;
- criar visualizações em um dashboard para acompanhar os segmentos.

---

## Conclusão

O projeto mostrou como uma técnica simples de Machine Learning pode ajudar a entender melhor o comportamento dos clientes em um cenário de e-commerce.

Com o K-Means, foi possível criar uma segmentação inicial, interpretar os grupos encontrados e sugerir possíveis ações de negócio para cada perfil de cliente.
