# Análise exploratória dos dados (EDA, de Exploratory Data Analysis)
Os dados se referem à características de pacientes visando detectar possibvilidade de ataque cardíaco. Nós temos 303 instâncias, com 14 atributos cada. A distribuição do atributo alvo varia entre 0 e 1, por ser um problema de classificação. Especialmente para modelos usando KNN, precisaremos normalizar os dados númericos.

KNN
Árvors de Decisão
Regressão Logística
Rede Neural
Random Forest
Gradient Boosting

F1 score (ou accuracy?) - pedir pro clovis
(nested?) cross-validation

Aparanetemente o dataset do Kaggle se inspira de um outro database original, com 76 atributos e um "dicionário" levemente diferente. Tivemos que realizar algumas correções, tanto no target (que aparentava estar invertido), quanto nos atributos ca e thal (que possuíam valores inconsistentes/fora do domínio).