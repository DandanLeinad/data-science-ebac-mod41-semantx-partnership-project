---
title: Modelagem
description: Visão geral do pipeline de modelagem aplicado ao dataset Wine Quality.
---

# Modelagem

Com os dados coletados e validados, o projeto seguiu um pipeline de cinco
etapas, cada uma respondendo a uma pergunta específica sobre os vinhos:

1. **[Análise Exploratória](eda.md)** — Como os dados estão distribuídos? Quais
   variáveis parecem se relacionar com a qualidade?
2. **[Probabilidade e Inferência](inferencia.md)** — As relações observadas são
   estatisticamente significativas ou podem ser fruto do acaso?
3. **[PCA](pca.md)** — É possível resumir as 11 variáveis físico-químicas em
   menos dimensões, sem perder informação relevante?
4. **[K-Means](kmeans.md)** — Existem perfis (segmentos) naturais de vinho
   escondidos nos dados?
5. **[Regressão e Comparação de Modelos](regressao.md)** — Qual algoritmo
   prevê melhor a nota de qualidade a partir das propriedades físico-químicas?

```python
import pandas as pd
import numpy as np
import matplotlib.pyplot as plt
import seaborn as sns
from scipy import stats
from sklearn.cluster import KMeans
from sklearn.preprocessing import StandardScaler
from sklearn.decomposition import PCA
from sklearn.model_selection import train_test_split
from sklearn.linear_model import LinearRegression
from sklearn.ensemble import RandomForestRegressor
from sklearn.metrics import mean_squared_error, r2_score
```

Todas as etapas foram implementadas em Python com `pandas`, `numpy`,
`matplotlib`, `seaborn`, `scipy` e `scikit-learn`, no notebook
`semantx-partnership-project.ipynb`.

Comece pela [Análise Exploratória →](eda.md)
