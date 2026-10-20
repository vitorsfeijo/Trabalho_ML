# **Identificação do grupo**

| Nome | Cartão UFRGS |
| :---- | :---- |
| Gabriel Pieruccini Knopp | 00594975 |
| Vitor Santana Feijó | 00588403 |
|  |  |

**Link para o notebook do Google Colab (ou google drive com arquivos do T1):**  
\<digite aqui o link\> 

# **1\. Definição do problema**

**Título do trabalho:** Detector de Ataques Cardíacos

**Dataset:**  [Health Care Dataset on Heart Attack Possibility](https://www.kaggle.com/datasets/nareshbhat/health-care-data-set-on-heart-attack-possibility)

**Variável alvo/problema a ser resolvido:**  Tendência de Ataque Cardíaco

**Caracterização dos dados**: 303 instâncias no arquivo original (302 após a remoção de 1 instância duplicada) e 13 atributos preditivos, todos utilizados: 5 numéricos (age, trestbps, chol, thalach, oldpeak), 3 binários (sex, fbs, exang), 4 categóricos nominais (cp, restecg, slope, thal) e 1 discreto ordinal (ca). O alvo (target) é binário, com 164 instâncias da classe 1 – sem doença cardíaca (54,3%) e 138 da classe 0 – com doença cardíaca (45,7%).

# **2\. Preparação dos dados**

Descreva as decisões de preparação que foram necessárias para o dataset escolhido, incluindo:

* Atributos disponíveis e utilizados.  
* Tratamento de valores ausentes e inconsistências, quando aplicável.  
* Codificação e/ou transformação das variáveis.  
* Normalização ou padronização, quando aplicável.  
* Tratamento de desbalanceamento de classes, quando aplicável.  
* Outras decisões de pré-processamento que possam afetar a comparação entre modelos.

Resumo das decisões:

**Atributos:** os 13 atributos preditivos foram mantidos. fbs apresentou baixa relevância individual (informação mútua e correlação com o alvo), mas, como a base tem poucos atributos e essas medidas não capturam interações, nenhum atributo foi removido no spot-checking. Também não há redundância forte (maior |r| = 0,61, entre oldpeak e slope).

**Valores ausentes e inconsistências:** não há valores NaN explícitos, mas a comparação registro a registro com a base Cleveland original da UCI mostrou que ca = 4 (4 instâncias) e thal = 0 (2 instâncias) correspondem a valores ausentes ("?") e que a descrição de thal no Kaggle está incorreta (na prática, 1 = defeito fixo, 2 = normal, 3 = defeito reversível). Esses códigos foram convertidos em valores ausentes, imputados pela moda calculada apenas no treino. Foi removida 1 instância duplicada, artefato da versão do Kaggle. A mesma comparação revelou que target = 1 corresponde aos pacientes sem doença (num = 0 na UCI), ao contrário da descrição do Kaggle; isso não altera a modelagem, apenas a interpretação. Os outliers (trestbps, chol e oldpeak) foram mantidos por serem clinicamente plausíveis.

**Codificação:** cp, restecg, slope e thal são categorias nominais armazenadas como inteiros e sem relação monotônica com o alvo; por isso recebem one-hot encoding (13 → 22 colunas), com handle_unknown="ignore" devido a categorias raras (ex.: restecg = 2, com 4 instâncias no treino). Os atributos binários e ca permanecem numéricos.

**Normalização:** as escalas são muito heterogêneas (a amplitude de chol é cerca de 46 vezes a de oldpeak); os atributos numéricos são padronizados (z-score, StandardScaler), o que é essencial para os modelos baseados em distância, margem ou gradiente.

**Desbalanceamento:** as classes estão quase balanceadas (54% × 46%, razão ≈ 1,2); não se aplica reamostragem, apenas estratificação nas divisões.

**Outras decisões:** a remoção da duplicata e a marcação dos códigos de ausência (regras determinísticas) são feitas antes da divisão treino/teste; todas as etapas que aprendem parâmetros (imputação, codificação e padronização) são encapsuladas em um Pipeline e ajustadas somente nos dados de treino de cada fold.

# **3\. Protocolo de avaliação**

Descreva como os modelos serão comparados, preenchendo a tabela abaixo. Adicione observações adicionais necessárias em um parágrafo após a tabela.

| Tarefa | Classificação binária: o alvo (target) possui duas classes (0 = com doença cardíaca; 1 = sem doença cardíaca). |
| :---- | :---- |
| **Métrica principal** | \[Preencher. Por que essa métrica é adequada ao problema?\] |
| **Métricas avaliadas** | \[Preencher\] |
| **Particionamento dos dados** | Holdout estratificado pelo alvo: 80% para treino (241 instâncias) e 20% para teste (61 instâncias), com random_state = 42. O spot-checking usa apenas o conjunto de treino; o teste fica reservado para a avaliação final no T2. |
| **Estratégia de validação** | \[Preencher. Especifique número de repetições de forma clara.  Ex.: validação cruzada estratificada k-fold\] |
| **Tratamento do desbalanceamento de classes** | Não se aplica: classes quase balanceadas (54,4% × 45,6% no treino; razão ≈ 1,2). Todas as divisões são estratificadas para preservar essa proporção. |
| **Critério de comparação** | \[Como os modelos serão comparados\] |
| **Estratégias contra data leakage** | Remoção da duplicata antes da divisão (evita a mesma instância em treino e teste); divisão treino/teste antes de qualquer análise que embase o pré-processamento; imputação, one-hot encoding e padronização encapsuladas em um Pipeline do scikit-learn, ajustado apenas nos dados de treino de cada fold; conjunto de teste não utilizado no T1. |

# **4\. Execução do Spot-Checking**

Liste os algoritmos avaliados e registre, de forma sucinta, as configurações dos hiperparâmetros utilizadas. O objetivo desta etapa é identificar modelos promissores para investigação mais aprofundada no T2.

| Modelo | Configuração utilizada | Motivo da inclusão | Observações |
| :---- | :---- | :---- | :---- |
| \[Modelo 1\] | \[Hiperparâmetros\] | \[Justificativa\] | \[Observações\] |
| \[Modelo 2\] | \[Hiperparâmetros\] | \[Justificativa\] | \[Observações\] |

Adicione linhas conforme necessário. Não é necessário apresentar aqui todo o código de execução; ele deve estar disponível no notebook.

# **5\. Resultados**

## **5.1 Tabela comparativa**

Apresente os resultados obtidos para os modelos analisados em tabela, com a média e o desvio padrão das métricas analisadas.

*\[Inserir tabela comparativa aqui\]*

## **5.2 Gráfico comparativo**

Insira um gráfico que permita comparar visualmente o desempenho dos modelos segundo a(s) métrica(s) definida(s) no protocolo.

*\[Inserir gráfico comparativo aqui\]*

# **6\. Interpretação dos resultados**

Interprete os resultados com foco na comparação entre os modelos e nas evidências que justificam as decisões para o T2. Evite apenas repetir os valores apresentados na tabela.

* **Quais modelos apresentaram resultados mais promissores segundo o protocolo definido?**

*\[Resposta curta\]*

* **Quais padrões, diferenças ou comportamentos relevantes foram observados entre os modelos?**

*\[Resposta curta\]*

* **O que os resultados sugerem sobre o problema e/ou sobre os dados?**

*\[Resposta curta\]*

# **7\. Seleção dos modelos para o T2**

Relate sobre os modelos selecionados para o T2 e justifique a escolha com base nos resultados do Spot-Checking. A seleção não precisa considerar apenas a maior métrica: aspectos como comportamento observado, características do problema e possibilidade de aprofundamento também podem ser considerados, desde que explicitados.

# **Uso de IA Generativa**

Ferramentas de Inteligência Artificial Generativa podem ser utilizadas como recurso complementar durante a realização do trabalho, por exemplo, para esclarecer conceitos, sugerir alternativas, auxiliar na identificação de erros ou apoiar a organização do código e do texto. Entretanto, seu uso não substitui a análise e a tomada de decisão pelos estudantes. Todas as decisões metodológicas, implementações, resultados e interpretações apresentadas no trabalho devem ser compreendidas pelos autores, que devem ser capazes de explicar e justificar as escolhas realizadas e os resultados obtidos. **Quando o uso de IA Generativa tiver contribuído de forma relevante para o desenvolvimento do trabalho, isso deve ser informado neste relatório, conforme as orientações da disciplina.**

# **Referências utilizadas**

Cite as referências utilizadas no desenvolvimento do trabalho.

