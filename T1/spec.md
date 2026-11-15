# Aprendizado de Máquina — INF01017

**Professora:** Mariana Recamonde Mendoza

## Trabalho prático final — Parte 1 (T1)

### Modelagem preditiva com Aprendizado de Máquina

**Caracterização do problema e spot-checking de algoritmos**

## 1. Contexto

Em Aprendizado de Máquina (AM), o *No-Free Lunch Theorem* estabelece que não há um único algoritmo com melhor desempenho universal — isto é, que seja o melhor algoritmo (e, portanto, o recomendado) para todo e qualquer problema a ser resolvido.

Assim, ao iniciar um novo projeto envolvendo o uso de algoritmos de aprendizado de máquina, recomenda-se explorar diferentes algoritmos no conjunto de dados para estabelecer um *baseline* de desempenho e escolher um subconjunto que pareça mais promissor para justificar uma investigação mais aprofundada.

A ideia de explorar rapidamente diferentes métodos de aprendizado de máquina é normalmente referida como **spot-checking algorithms** (em tradução livre, verificação pontual de algoritmos). O principal objetivo é obter um conjunto inicial de informações sobre os algoritmos que potencialmente serão melhores para o desenvolvimento de modelos preditivos para um conjunto de dados, determinando em quais deles vale a pena dedicar mais tempo à otimização de hiperparâmetros e à análise mais aprofundada dos modelos.

Portanto, o *spot-checking* difere da otimização de um único algoritmo por meio do ajuste fino de seus hiperparâmetros. Podemos pensar no *spot-checking* como uma primeira etapa na escolha de algoritmos, que irá refinar o conjunto de algoritmos a serem explorados em mais profundidade na etapa de otimização de hiperparâmetros.

Nesse processo, é sempre recomendado testar um conjunto diversificado de algoritmos, com diferentes tipos de viés indutivo, variando, por exemplo:

- o tipo de representação de hipóteses (por exemplo, árvores e instâncias);
- a estratégia de aprendizado (por exemplo, probabilística ou por otimização);
- o tipo de modelagem (por exemplo, linear ou não linear, paramétrica ou não paramétrica).

Assim, o Trabalho Prático — Parte 1 (T1) da disciplina INF01017 visa permitir que os alunos iniciem a modelagem de um problema preditivo de interesse e desenvolvam um *pipeline* para fazer um *spot-checking* de algoritmos de aprendizado supervisionado para a tarefa selecionada, seja de classificação ou de regressão.

## 2. Objetivo do trabalho

A proposta deste trabalho prático é que os alunos realizem a caracterização de um problema de modelagem preditiva (classificação ou regressão) e implementem e executem um *spot-checking* de algoritmos para a tarefa escolhida.

Organizados em grupos de 2 ou 3 pessoas, os alunos devem:

- selecionar um problema de interesse;
- coletar dados;
- realizar uma análise exploratória dos dados;
- realizar um pré-processamento inicial;
- comparar um conjunto diversificado de algoritmos de aprendizado de máquina para resolver o problema.

Essa comparação será realizada de acordo com a proposta de *spot-checking*: fornecer, de forma rápida e objetiva, um primeiro conjunto de resultados para um novo problema de modelagem preditiva.

### 2.1. Etapas gerais do spot-checking

Em linhas gerais, o processo de *spot-checking* envolve:

1. carregar os dados;
2. realizar um pré-processamento inicial dos dados (por exemplo, normalização);
3. definir os algoritmos de aprendizado a serem aplicados;
4. treinar e avaliar os modelos, utilizando valores padrão de hiperparâmetros ou variações mínimas;
5. sumarizar os resultados;
6. apontar os algoritmos mais promissores.

As seções a seguir detalham alguns aspectos do desenvolvimento do trabalho.

## 3. Desenvolvimento

### 3.1. Definição do problema e coleta de dados

Pode ser utilizado qualquer conjunto de dados de interesse do grupo que esteja relacionado a uma tarefa de classificação ou regressão. Como sugestão, alguns repositórios que podem ser consultados são:

- [PMLB](https://epistasislab.github.io/pmlb/);
- [Kaggle](https://www.kaggle.com/);
- [UCI Machine Learning Repository](https://archive.ics.uci.edu/ml/datasets.php).

Solicita-se que, de preferência, os alunos utilizem conjuntos de dados que não tenham sido explorados ao longo da disciplina (por exemplo, em atividades práticas).

A tarefa a ser abordada deve estar claramente descrita no relatório. Espera-se uma definição clara do objetivo do trabalho desenvolvido, ou seja, dos dados utilizados para treinamento dos modelos e da pergunta de pesquisa que o grupo visou investigar com algoritmos de AM.

Por exemplo:

> Nosso trabalho tem como objetivo desenvolver um modelo baseado em AM para prever o tipo de vinho (tinto ou branco) a partir de um conjunto de características físico-químicas. Para tanto, utilizamos o conjunto de dados `<breve descrição>`, disponível em `<link para download>`.

Para os trabalhos que envolverem dados publicamente disponíveis, os grupos devem incluir o link para download no relatório.

### 3.2. Análise exploratória dos dados (EDA)

Realize uma análise exploratória dos dados coletados. O objetivo é entender melhor e sumarizar as características dos dados, analisando:

- a quantidade e os tipos de atributos;
- a distribuição do atributo-alvo;
- padrões e anomalias;
- atributos que pareçam irrelevantes ou problemáticos.

Utilize gráficos e sumarizações estatísticas para a EDA. Verifique potenciais problemas nos dados, como:

- a necessidade de normalizar os atributos;
- o balanceamento das classes;
- a necessidade de remover instâncias ou atributos por inconsistências nos dados.

Inclua no relatório os resultados dessa análise e uma síntese dos eventuais problemas identificados.

### 3.3. Pré-processamento dos dados

Aplique técnicas de pré-processamento nos dados a fim de melhorar sua qualidade, eliminando ou minimizando problemas identificados na etapa anterior.

A avaliação deste trabalho não exigirá um pré-processamento aprofundado, por ser um tópico ainda pouco discutido na disciplina. Entretanto, espera-se que os grupos lidem com aspectos como:

- remoção de atributos ou instâncias problemáticas, por exemplo, por conterem muitos valores faltantes ou não parecerem informativas para o problema;
- normalização de atributos;
- balanceamento de classes;
- transformação de atributos categóricos em numéricos, caso necessário.

As características dos dados utilizados, bem como as etapas envolvidas no pré-processamento, devem ser bem discutidas no relatório. Caso não haja necessidade de pré-processar os dados, os grupos devem mencionar e justificar essa decisão no texto.

### 3.4. Definição da abordagem, dos algoritmos e da estratégia de avaliação

Defina a abordagem de aprendizado de máquina que será utilizada, isto é, se o problema é de classificação ou regressão. Justifique a escolha com base na natureza do problema e nos dados disponíveis.

Selecione os algoritmos de aprendizado supervisionado a serem aplicados. Essa definição é de livre escolha do grupo, mas solicita-se que inclua algoritmos presentes no conteúdo programático da disciplina, podendo incluir adicionalmente outros algoritmos não abordados em aula.

Sugere-se selecionar um conjunto diversificado de algoritmos quanto ao viés indutivo, com o propósito de realizar o *spot-checking*. Neste trabalho prático, os algoritmos podem ser aplicados com valores padrão de hiperparâmetros ou, se for da vontade do grupo, com variações mínimas — por exemplo, uma árvore de decisão sem poda e outra com poda não muito drástica.

> Os grupos devem comparar **ao menos 5 algoritmos distintos**.

Selecione as métricas de desempenho que serão utilizadas para avaliar os modelos, considerando a definição da modelagem e a interpretação do problema abordado. Recomenda-se utilizar mais de uma métrica para avaliação e comparação dos modelos, mas selecionar uma métrica como critério principal de seleção — ou seja, aquela que o grupo tentará otimizar na análise de desempenho dos algoritmos.

Escolha também a estratégia para realizar a divisão dos dados para treinamento e avaliação, como *holdout* ou *cross-validation*.

No relatório, descreva as decisões a respeito da abordagem, dos algoritmos e das métricas de avaliação adotadas.

### 3.5. Spot-checking de algoritmos

Execute a verificação rápida dos algoritmos por meio do treinamento e da avaliação dos modelos, de acordo com as definições do item anterior. Testar uma variedade de algoritmos permite identificar quais modelos apresentam o melhor desempenho inicial com os dados disponíveis, economizando tempo e esforço ao focar em algoritmos que têm potencial para a tarefa em questão.

Recomenda-se realizar múltiplas repetições do treinamento e da avaliação com cada algoritmo selecionado, utilizando estratégias vistas em aula. É importante garantir a consistência dos resultados, utilizando as mesmas divisões de dados em uma determinada iteração para todos os algoritmos.

Também é recomendado utilizar a definição manual de *seeds* em processos aleatórios (parâmetro `random_state`, no scikit-learn), para fins de reprodutibilidade dos experimentos.

Neste trabalho prático, não estamos interessados em realizar a otimização de hiperparâmetros ou a análise aprofundada dos modelos, como a interpretabilidade.

Descreva no relatório a estratégia de *spot-checking*, incluindo detalhes sobre:

- como foi feita a divisão dos dados;
- se foram executadas repetições dos processos de treinamento e avaliação dos modelos.

### 3.6. Sumarização dos resultados

Faça a síntese dos resultados da avaliação dos modelos. O objetivo é identificar quais algoritmos se saíram melhor e merecem seguir para uma investigação mais detalhada, permitindo uma escolha informada de algoritmos para a otimização de modelos.

> A investigação mais detalhada está fora do escopo do T1.

Para esta etapa, sugere-se o uso de:

- média e desvio padrão do desempenho;
- gráficos do tipo *box plot*, *violin plot*, *joy plot* ou similares, para visualizar a distribuição de desempenho por modelo ao longo de `n` execuções.

O uso de gráficos é importante, pois viabiliza uma análise visual dos resultados.

Os grupos devem analisar os resultados, discutir de forma comparativa o desempenho dos modelos e apontar as **3 estratégias mais promissoras** para o problema em questão. Inclua no relatório essa discussão, com suporte em dados, tabelas e gráficos.

## 4. Ferramentas

Python é a linguagem recomendada por oferecer bibliotecas importantes, como o scikit-learn.

Solicita-se o uso do [Google Colab](https://colab.research.google.com/) para fins de melhor reprodutibilidade do trabalho.

## 5. Entrega

Os grupos deverão enviar um relatório em PDF pelo Moodle, seguindo obrigatoriamente o formato a ser disponibilizado pela professora. O relatório deve conter:

- identificação do grupo;
- um título significativo para o projeto, de acordo com o problema abordado;
- link para o Notebook Google Colab, incluindo todas as etapas envolvidas no desenvolvimento do T1, do carregamento dos dados aos resultados do *spot-checking* e à seleção de modelos para o T2;
- relato, na estrutura definida no template disponibilizado, das principais etapas do projeto:
  - preparação dos dados;
  - definição do protocolo de avaliação;
  - execução do *spot-checking*;
  - resultados, com tabela e gráfico comparativo;
  - interpretação dos resultados;
  - seleção dos modelos para o T2.

O trabalho prático deverá ser apresentado oralmente pelo grupo durante o período de aula, em data a ser determinada pela professora. Essa apresentação será realizada ao final do semestre, após a realização e a entrega do T2. A nota da apresentação será incorporada à avaliação do T2.

### Prazo e forma de entrega

- **Prazo:** 25/10/2026, às 23h59, via Moodle;
- **Envio:** deve ser feita uma entrega por grupo.

## 6. Critérios de avaliação

- pontualidade na entrega do trabalho;
- completude do trabalho e atendimento aos requisitos definidos neste enunciado;
- qualidade e correção da metodologia para desenvolvimento e verificação rápida dos modelos, incluindo todas as etapas previstas neste enunciado;
- qualidade do relatório final, da apresentação e da discussão dos resultados, bem como abrangência em relação aos requisitos de relato definidos neste enunciado.

> **Atenção:** atrasos na entrega do trabalho serão penalizados proporcionalmente ao tempo de atraso, sendo descontado 1 ponto por dia de atraso. O T1, como um todo, vale 10 pontos.

## 7. Dúvidas

Em caso de dúvidas sobre a realização do trabalho, incluindo a definição do tema de pesquisa, entre em contato com a professora pelo e-mail [mrmendoza@inf.ufrgs.br](mailto:mrmendoza@inf.ufrgs.br).

Para dúvidas técnicas, sinta-se à vontade para utilizar o Fórum de Dúvidas no Moodle da disciplina.

## 8. Uso de Inteligência Artificial Generativa

O uso de ferramentas de Inteligência Artificial (IA) Generativa é permitido e incentivado como recurso complementar ao desenvolvimento do trabalho. A IA pode ser utilizada, por exemplo, para:

- apoiar a compreensão de conceitos;
- explorar alternativas metodológicas;
- revisar código;
- auxiliar na interpretação de resultados;
- aprimorar a redação.

Entretanto, a IA não deve substituir o processo de análise, tomada de decisão ou elaboração do trabalho pelos alunos. Todas as decisões metodológicas, escolhas de modelos, configurações experimentais, procedimentos de pré-processamento, métricas, interpretações e conclusões devem ser compreendidas e justificadas pelos integrantes do grupo.

Os alunos devem ser capazes de explicar e defender integralmente o trabalho realizado, inclusive o código produzido ou modificado com auxílio de IA. O uso de IA não exime os alunos da responsabilidade pela correção, validade e reprodutibilidade dos resultados apresentados.

Recomenda-se, ainda, que seu uso seja realizado de forma crítica, verificando as informações e os códigos gerados antes de incorporá-los ao trabalho.
