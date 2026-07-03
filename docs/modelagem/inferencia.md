---
title: Probabilidade e Inferência
description: Testes estatísticos sobre álcool x qualidade e tinto x branco.
---

# Probabilidade e Inferência Estatística

A análise exploratória levantou duas hipóteses de negócio. Esta etapa testa
cada uma delas formalmente, com um nível de significância de 5% (α = 0,05).

## O teor alcoólico influencia a qualidade?

Foi calculada a correlação de Pearson entre `alcohol` e `quality`, junto com o
p-valor do teste de significância:

```python
corr_coef, p_value = stats.pearsonr(df["alcohol"], df["quality"])
```

| Métrica                 | Valor      |
| ------------------------ | ----------- |
| Correlação de Pearson (r) | **0,444**  |
| p-valor                  | < 0,00001   |
| Conclusão                | Estatisticamente significativo |

!!! success "Resultado"
    Existe uma correlação positiva e estatisticamente significativa entre teor
    alcoólico e qualidade (r = 0,44; p < 0,001). Quanto maior o álcool, maior a
    tendência de nota mais alta — essa não é uma relação aleatória.

Uma correlação de 0,44 é moderada: importante, mas está longe de explicar a
qualidade sozinha, o que reforça a necessidade de um modelo multivariado (ver
[Regressão](regressao.md)).

## Vinhos tintos e brancos têm qualidade diferente?

Foi aplicado um teste t de Student para amostras independentes, comparando a
nota média de qualidade entre tintos e brancos:

```python
t_stat, p_value_t = stats.ttest_ind(
    qualidade_tinto, qualidade_branco, equal_var=False
)
```

| Métrica       | Valor        |
| -------------- | ------------- |
| Estatística t  | **-10,149**   |
| p-valor        | < 0,00001     |
| Conclusão      | Diferença estatisticamente significativa |

!!! success "Resultado"
    A diferença de qualidade média entre tintos e brancos é estatisticamente
    significativa (p < 0,001). O sinal negativo da estatística t indica que, em
    média, os vinhos **brancos** têm nota de qualidade mais alta que os
    **tintos** nesta amostra.

Este resultado justifica manter a coluna `tipo` como parte do contexto de
negócio — embora, como será visto na modelagem, não seja necessariamente a
variável mais relevante para prever a nota de um vinho específico.

Próximo passo: [PCA →](pca.md)
