---
title: Início
description: Previsão e segmentação da qualidade de vinhos com PCA, K-Means, regressão e inferência estatística.
---

# Previsão e Segmentação da Qualidade de Vinhos

**Projeto Módulo 41 — Parceria EBAC x Semantix**

Este projeto aplica um pipeline completo de ciência de dados — inferência estatística,
redução de dimensionalidade (PCA), segmentação (K-Means) e modelos preditivos
(Regressão Linear e Random Forest) — para responder a uma pergunta prática de negócio:
**é possível prever a nota de qualidade de um vinho a partir apenas de suas
propriedades físico-químicas, sem depender de um painel de degustadores?**

## Contexto de negócio

Avaliar a qualidade de um vinho hoje depende, em grande parte, de degustadores
humanos: um processo caro, lento e sujeito a variação subjetiva. Uma vinícola que
consiga estimar a nota sensorial a partir de medições físico-químicas rápidas
(acidez, teor alcoólico, densidade, sulfatos etc.) ganha um instrumento de
**controle de qualidade** mais barato e mais rápido, além de um mapa dos
**perfis de vinho** que compõem seu portfólio.

## Objetivo

!!! abstract "Objetivo do projeto"
    Prever a qualidade de vinhos a partir de suas propriedades físico-químicas e
    identificar perfis (clusters) de vinhos, aplicando PCA, K-Means, inferência
    estatística, regressão e combinação de modelos.

## O que você vai encontrar aqui

<div class="grid cards" markdown>

- :material-database:{ .lg .middle } **Coleta de Dados**

    ---

    Origem, licença e características do dataset utilizado.

    [:octicons-arrow-right-24: Ver página](coleta-de-dados.md)

- :material-chart-scatter-plot:{ .lg .middle } **Modelagem**

    ---

    Análise exploratória, inferência estatística, PCA, K-Means, regressão e
    comparação de modelos — com todos os gráficos gerados na análise.

    [:octicons-arrow-right-24: Ver página](modelagem/index.md)

- :material-flag-checkered:{ .lg .middle } **Conclusões**

    ---

    Principais achados e aplicações práticas para uma vinícola.

    [:octicons-arrow-right-24: Ver página](conclusoes.md)

</div>

## Resumo dos principais resultados

| Pergunta                              | Resposta                                                              |
| -------------------------------------- | ----------------------------------------------------------------------- |
| O teor alcoólico influencia a qualidade? | Sim — correlação de Pearson de 0,44 (p < 0,001)                        |
| Tinto e branco têm qualidade diferente? | Sim, diferença estatisticamente significativa (teste t, p < 0,001)     |
| Quantos perfis de vinho existem?       | 3 clusters (baixa, média e alta qualidade), identificados via K-Means  |
| Qual o melhor modelo preditivo?        | Random Forest (R² = 0,50), superando a Regressão Linear (R² = 0,26)    |

Os detalhes de cada etapa, com os gráficos gerados na análise, estão nas páginas
de [Modelagem](modelagem/index.md). Os principais aprendizados e recomendações de
negócio estão reunidos em [Conclusões](conclusoes.md).

## Fonte dos dados

Os dados utilizados são públicos, vêm do [UCI Machine Learning Repository — Wine
Quality](https://archive.ics.uci.edu/dataset/186/wine+quality) e estão sob
licença **CC BY 4.0**. Mais detalhes na página [Coleta de Dados](coleta-de-dados.md).

## Ferramentas utilizadas

`pandas` · `numpy` · `matplotlib` · `seaborn` · `scipy` · `scikit-learn`

A documentação que você está lendo é gerada com [Zensical](https://zensical.org)
e publicada automaticamente via GitHub Pages a cada push na branch `main`.
