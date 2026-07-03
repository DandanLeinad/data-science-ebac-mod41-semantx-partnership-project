# 🍷 Previsão e Segmentação da Qualidade de Vinhos

**Projeto Módulo 41 — Parceria EBAC × Semantix**

Pipeline completo de ciência de dados aplicado ao dataset [UCI Wine Quality](https://archive.ics.uci.edu/dataset/186/wine+quality) (CC BY 4.0) para prever a nota sensorial de vinhos a partir de propriedades físico-químicas e identificar perfis naturais de vinho.

---

## 🎯 Objetivo

- Prever a qualidade (nota 3–9) sem depender de painel de degustadores
- Segmentar vinhos em perfis químicos distintos (baixa/média/alta qualidade)
- Aplicar: **PCA, K-Means, Inferência Estatística, Regressão Linear, Random Forest**

---

## 📊 Principais Resultados

| Pergunta | Resposta |
|----------|----------|
| O teor alcoólico influencia a qualidade? | **Sim** — Pearson r = 0,44 (p < 0,001) |
| Tinto vs branco têm qualidade diferente? | **Sim** — teste t, p < 0,001 (brancos > tintos) |
| Quantos perfis de vinho existem? | **3 clusters** (K-Means, k=3) |
| Melhor modelo preditivo? | **Random Forest** (R² = 0,50, CV 5-fold = 0,49 ± 0,02) |

**Variáveis mais importantes:** `alcohol`, `sulphates`, `volatile acidity`, `density`

---

## 🛠️ Stack

`Python` · `pandas` · `numpy` · `matplotlib` · `seaborn` · `scipy` · `scikit-learn`

---

## 📁 Estrutura

```
├── semantx-partnership-project.ipynb   # Notebook completo (código + outputs)
├── docs/                               # Documentação Zensical (Markdown)
│   ├── index.md                        # Início
│   ├── coleta-de-dados.md              # Fonte, variáveis, qualidade dos dados
│   ├── modelagem/                      # EDA, Inferência, PCA, K-Means, Regressão
│   └── conclusoes.md                   # Achados, aplicação prática, limitações
├── docs/assets/images/                 # 7 gráficos gerados
└── zensical.toml                       # Configuração do site de docs
```

---

## 🚀 Como rodar

```bash
# 1. Clone o repo
git clone https://github.com/DandanLeinad/data-science-ebac-mod42-semantx-partnership-project.git
cd data-science-ebac-mod42-semantx-partnership-project

# 2. Crie o ambiente
python -m venv .venv
source .venv/bin/activate  # Windows: .venv\Scripts\activate
pip install -r requirements.txt  # ou instale manualmente: pandas numpy matplotlib seaborn scipy scikit-learn

# 3. Abra o notebook
jupyter lab semantx-partnership-project.ipynb
```

---

## 📚 Documentação Online

A documentação completa (com narrativas, gráficos e código) está publicada via **Zensical + GitHub Pages**:

🔗 **[https://DandanLeinad.github.io/data-science-ebac-mod42-semantx-partnership-project/](https://DandanLeinad.github.io/data-science-ebac-mod42-semantx-partnership-project/)**

> Para rebuildar localmente: `pip install zensical && zensical build`

---

## 💡 Aplicação Prática para Vinícolas

1. **Controle de qualidade automatizado** — prever nota sensorial a partir de análises laboratoriais rápidas
2. **Ajuste de processo** — monitorar `volatile acidity` e `sulphates` para evitar perfil de baixa qualidade
3. **Segmentação de portfólio** — posicionar vinhos (entrada/intermediário/premium) com base em clusters
