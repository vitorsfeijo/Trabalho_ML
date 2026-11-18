# Trabalho_ML

## Integrantes: Gabriel Pieruccini Knopp, Vítor Santana Feijó.

Link do dataset: https://www.kaggle.com/datasets/nareshbhat/health-care-data-set-on-heart-attack-possibility

## Organização do repositório

```
dados/                  bases usadas nos dois trabalhos
  heart.csv               versão do Kaggle
  processed.cleveland.data  base Cleveland original da UCI (para conferir a codificação do Kaggle)
T1/                     Parte 1: caracterização do problema e spot-checking
  T1 - Enunciado.pdf, spec.md, T1_Template_Spot-Check_Summary.docx.pdf
  Notebook - Detector de Ataques Cardíacos.ipynb
  Relatório (.md, .tex, .docx e .pdf), figuras/, images/
T2/                     Parte 2: otimização, avaliação e interpretação
  Notebook T2 - Otimização e Interpretação (validação).ipynb
  Model_Card_T2.tex e .pdf (Model Card de 2 páginas, títulos das seções em inglês)
  Model_Card_T2_PT.tex e .pdf (mesmo Model Card, com todos os títulos em português)
  T2_Template_ModelCards.docx (template da professora, usado como base para as respostas)
  figuras/              tabelas e figuras de resultados do T2
disciplina/             material da disciplina (diretrizes de IA e notebooks das aulas)
```

Os notebooks leem os dados de `../dados/` quando executados localmente e do GitHub quando executados no Google Colab.
