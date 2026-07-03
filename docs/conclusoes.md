---
title: Conclusões
description: Principais achados e aplicações práticas para uma vinícola.
---

# Conclusões

## Principais variáveis que influenciam a qualidade

- **Álcool** — correlação de Pearson de 0,44 (p < 0,001): maior teor alcoólico
  tende a significar maior qualidade.
- **Sulfatos** — correlação ≈ 0,25: compostos sulfurados associados a melhor
  qualidade.
- **Acidez volátil** — correlação ≈ -0,39: maior acidez volátil tende a
  significar menor qualidade (é um defeito sensorial reconhecido).
- A importância de variáveis do Random Forest confirma o mesmo conjunto:
  `alcohol`, `sulphates`, `volatile acidity` e `density` são os principais
  fatores preditivos.

## Perfis de vinho identificados (K-Means, k = 3)

- **Cluster 0 — baixa qualidade:** menor teor alcoólico (~9,5%), maior acidez
  volátil, menores sulfatos.
- **Cluster 1 — qualidade média:** perfil intermediário, nota predominante 5–6.
- **Cluster 2 — alta qualidade:** maior teor alcoólico (~11–12%), menor acidez
  volátil, maiores sulfatos.

A escolha de k = 3 se apoiou tanto no método do cotovelo (inflexão clara nesse
ponto) quanto na interpretabilidade de negócio: os três clusters mapeiam
diretamente para as faixas de qualidade baixa, média e alta.

## Melhor modelo preditivo

O **Random Forest** (R² = 0,50; RMSE = 0,61) superou a **Regressão Linear**
(R² = 0,26; RMSE = 0,74). O modelo de ensemble captura não linearidades e
interações entre variáveis — como o efeito do álcool variando conforme o nível
de acidez volátil — que o modelo linear ignora.

A **validação cruzada (5-fold)** confirmou a robustez do modelo: R² médio de
**0,49 (±0,02)**, indicando baixa variância e boa generalização.

## Aplicação prática para uma vinícola

1. **Controle de qualidade automatizado** — prever a nota sensorial a partir de
   análises físico-químicas rápidas reduz custo e tempo, sem depender
   exclusivamente de um painel de degustadores.
2. **Ajuste de processo produtivo** — monitorar `volatile acidity` e
   `sulphates` durante a fermentação ajuda a evitar que o vinho caia no perfil
   do Cluster 0 (baixa qualidade).
3. **Segmentação de portfólio** — usar os três clusters para posicionar vinhos
   (entrada, intermediário, premium) de forma orientada a dados.

## Limitações e próximos passos

- O dataset tem poucas amostras nas notas extremas (3, 4, 8, 9), o que limita a
  capacidade de qualquer modelo de acertar exatamente esses casos — um
  desbalanceamento discutido na [Análise Exploratória](modelagem/eda.md).
- R² = 0,50 indica que o Random Forest explica metade da variância da
  qualidade; a outra metade provavelmente envolve fatores não capturados pelas
  variáveis físico-químicas disponíveis (como uva, terroir, processo de
  vinificação e, claro, a subjetividade do próprio julgamento sensorial).
- **Quality como variável contínua**: a nota (3–9) foi tratada como contínua
  para regressão. Abordagem alternativa — classificação ordinal (ex.: Ordered
  Logit, XGBoost ordinal) — não foi explorada aqui, mas é viável para produção.
- Próximos passos possíveis: testar outros ensembles (Gradient Boosting,
  XGBoost), tratar o desbalanceamento das notas extremas, e validar o modelo
  com dados de uma vinícola real.

---

Voltar para o [início](index.md) · Revisar a [modelagem completa](modelagem/index.md)
