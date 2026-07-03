---
title: Coleta de Dados
description: Origem, licença e características do dataset Wine Quality (UCI).
---

# Coleta de Dados

## Fonte

Os dados foram coletados diretamente do [UCI Machine Learning Repository — Wine
Quality Dataset](https://archive.ics.uci.edu/dataset/186/wine+quality), um
repositório público, estável e amplamente citado na literatura de ciência de
dados.

| Item          | Detalhe                                                                  |
| ------------- | ------------------------------------------------------------------------- |
| Licença       | CC BY 4.0                                                                 |
| Vinhos tintos | `winequality-red.csv` — 1.599 registros                                  |
| Vinhos brancos| `winequality-white.csv` — 4.898 registros                                |
| Total         | **6.497 registros**, 13 colunas após o merge (11 variáveis + `quality` + `tipo`) |

```python
url_tinto = "https://archive.ics.uci.edu/ml/machine-learning-databases/wine-quality/winequality-red.csv"
url_branco = "https://archive.ics.uci.edu/ml/machine-learning-databases/wine-quality/winequality-white.csv"

df_tinto = pd.read_csv(url_tinto, sep=";")
df_branco = pd.read_csv(url_branco, sep=";")

df_tinto["tipo"] = "tinto"
df_branco["tipo"] = "branco"

df = pd.concat([df_tinto, df_branco], ignore_index=True)
```

Os dois arquivos (tinto e branco) foram unidos em um único DataFrame, com uma
coluna adicional `tipo` para distinguir a origem de cada amostra — o que permite
comparar os dois estilos de vinho ao longo de toda a análise.

## Variáveis do dataset

| Variável               | Descrição                                          |
| ------------------------ | ----------------------------------------------------- |
| `fixed acidity`          | Acidez fixa (ácidos não voláteis)                     |
| `volatile acidity`       | Acidez volátil (associada a defeitos sensoriais)      |
| `citric acid`            | Ácido cítrico                                         |
| `residual sugar`         | Açúcar residual após a fermentação                    |
| `chlorides`               | Cloretos                                              |
| `free sulfur dioxide`    | Dióxido de enxofre livre                              |
| `total sulfur dioxide`   | Dióxido de enxofre total                              |
| `density`                | Densidade                                             |
| `pH`                      | Nível de acidez/basicidade                            |
| `sulphates`               | Sulfatos                                              |
| `alcohol`                 | Teor alcoólico (% vol.)                               |
| `quality`                 | **Variável alvo** — nota sensorial de 0 a 10, atribuída por especialistas |
| `tipo`                    | Tinto ou branco (criada nesta análise)                |

## Qualidade dos dados

A checagem inicial mostrou um dataset limpo do ponto de vista de valores
ausentes, mas com registros duplicados que vale destacar:

- **Valores nulos:** nenhum, em nenhuma das 13 colunas.
- **Linhas duplicadas:** 1.177 (cerca de 18% do total). Isso é esperado neste
  dataset — como as variáveis são medições físico-químicas arredondadas, é comum
  que vinhos diferentes, avaliados por degustadores diferentes, apresentem
  exatamente a mesma combinação de valores.

!!! note "Por que os duplicados não foram removidos"
    As linhas duplicadas foram mantidas na análise. O Random Forest é robusto a
    duplicatas e a remoção não altera as conclusões do modelo. Além disso, como
    as notas de qualidade são atribuídas por degustadores diferentes, duas
    amostras com o mesmo perfil físico-químico mas notas distintas representam
    avaliações sensoriais legítimas, não erros de captura — removê-las poderia
    descartar variabilidade real de julgamento humano que interessa entender.

## Estatísticas descritivas

Resumo das principais variáveis (dataset combinado, tinto + branco):

| Estatística | álcool | qualidade | acidez volátil | sulfatos | densidade |
| ------------ | ------- | ---------- | ---------------- | --------- | ---------- |
| média        | 10,49   | 5,82       | 0,340             | 0,531     | 0,9947     |
| desvio padrão| 1,19    | 0,87       | 0,165             | 0,149     | 0,0030     |
| mínimo       | 8,00    | 3          | 0,080             | 0,220     | 0,9871     |
| máximo       | 14,90   | 9          | 1,580             | 2,000     | 1,0390     |

A nota de qualidade concentra-se majoritariamente entre 5 e 6 (vinhos
"medianos"), com poucas amostras nos extremos (notas 3, 4, 8 e 9) — um ponto
importante para a etapa de [modelagem](modelagem/index.md), já que o
desbalanceamento das classes limita o quanto qualquer modelo consegue aprender
sobre vinhos muito ruins ou excepcionais.

Próximo passo: [Modelagem →](modelagem/index.md)
