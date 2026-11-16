<img width="974" height="134" alt="image" src="https://github.com/user-attachments/assets/0a53a0bf-93ba-4ff5-a853-cf0914d6eb95" />

<div align="center">

# <h1 align="center"> Criatura lendária final - Desenvolvimento e validação de modelos de aprendizado de máquina para predição da biodegradabilidade de moléculas a partir de descritores moleculares
</div>

## Descrição do Projeto 
<p align="justify">  Esse projeto é parte da avaliação final da disciplina de aprendizado de máquina do segundo semestre letivo da Ilum escola de ciência. O trabalho consiste em desenvolver e avaliar modelos de aprendizado de máquina para a classificação de moléculas quanto a sua biodegrabilidade utilizando descritores moleculares extraídos do Instituto Nacional de Tecnologia e Avaliação do Japão (NITE) e disponibilizados no repositório público de aprendizado de máquina da University of California Irvine (UCI) pelos autores do artigo sob o título "Quantitative Structure-Active Relationship Model for Ready Biodegradability of Chemicals". Foram investigadas diferentes estratégias de pré-processamento, agrupamento de exemplos semelhantes, validação cruzada, otimização de hiperparâmetros e interpretação dos modelos, buscando obter predições robustas, quimicamente e biologicamente relevantes. 
     
## Conteúdo do repositório
| Arquivo | Descrição |
|---|---|
| `Tiamat.ipynb` | Notebook principal, com todo o código, as discussões e as análises do trabalho: análise exploratória, divisão treino/teste, baseline, otimização com Optuna, comparação dos modelos, avaliação final e explicabilidade. |
| `biodeg.csv` | Conjunto de dados QSAR Biodegradation (UCI [1]), no formato original: separador `;`, sem cabeçalho, com 41 descritores moleculares e a classe (RB ou NRB) na última coluna. O notebook lê esse arquivo diretamente, então ele deve ficar na mesma pasta do notebook. |
| `estudos_optuna.db` | Banco SQLite com os estudos do Optuna (100 tentativas por algoritmo). Permite reproduzir os resultados sem refazer a busca de hiperparâmetros e retomar a execução caso ela seja interrompida. |
| `README.md` | Este arquivo. |
| `LICENSE` | Licença do projeto (GNU GPL). |
| `.gitignore` | Arquivos e pastas que não devem ser versionados (caches, arquivos temporários do Jupyter etc.). |

## Estrutura do notebook

1. **Introdução**: contextualização do problema da biodegradabilidade e dos modelos QSAR.
2. **Desenvolvimento**
   - Bibliotecas e definições (constantes, semente aleatória, métrica).
   - Descrição dos dados: origem, coleta, tratamento e significado dos 41 descritores.
   - Análise exploratória: valores ausentes, distribuição das classes e dos atributos, correlações e exemplos redundantes.
   - Divisão treino/teste com agrupamento de exemplos semelhantes, checagem da qualidade do split e análise de sensibilidade.
   - Modelo baseline e validação cruzada.
   - Pipelines e otimização com Optuna: regressão logística, KNN, árvore de decisão, floresta aleatória e gradient boosting, com normalização e redução de dimensionalidade controladas pelo Optuna.
   - Comparação dos modelos, avaliação final no conjunto de teste e explicabilidade (importância por permutação).
3. **Conclusões e principais aprendizados**
4. **Referências bibliográficas**
5. **Descrição do uso de IA neste trabalho**

## Como executar

1. Clone o repositório e mantenha `Tiamat.ipynb` e `biodeg.csv` na mesma pasta.
2. Instale as bibliotecas listadas abaixo (por exemplo, com `pip install numpy pandas matplotlib seaborn scipy scikit-learn optuna`).
3. Abra o `Tiamat.ipynb` no Jupyter e execute as células de cima para baixo.

**Tempo de execução.** O notebook otimiza 5 algoritmos com 100 tentativas cada (500 tentativas no total, cada uma com validação cruzada de 5 folds). Com o `estudos_optuna.db` presente na pasta, o Optuna retoma os estudos já concluídos e não refaz a busca; para recomeçar do zero, apague esse arquivo (ou altere `ARQUIVO_ESTUDOS` na seção de definições) antes de executar.

## Bibliotecas utilizadas
- numpy
- pandas
- seaborn
- matplotlib.pyplot
- math
- seaborn
- optuna
- functools
- scipy
- sklearn
     
## **Referências**
[1] MANSOURI, Kamel; RINGSTED, Tine; BALLABIO, Davide; TODESCHINI, Roberto; CONSONNI, Viviana. QSAR biodegradation. UCI Machine Learning Repository, 2013. DOI: https://doi.org/10.24432/C5H60M. Disponível em: https://archive.ics.uci.edu/dataset/254/qsar+biodegradation. Acesso em: 15 nov. 2026.

[2] Mansouri, K., Ringsted, T., Ballabio, D., Todeschini, R., Consonni, V. (2013). Quantitative Structure-Activity Relationship models for ready biodegradability of chemicals. *Journal of Chemical Information and Modeling*, 53, 867-878. Doi: https://doi.org/10.1021/ci4000213.

[3] PANDAS DEVELOPMENT TEAM. pandas.DataFrame.skew. pandas documentation. Disponível em: https://pandas.pydata.org/docs/reference/api/pandas.DataFrame.skew.html. Acesso em: 15 nov. 2026.

[4] CASSAR, Daniel R. **Redução de dimensionalidade com PCA**. ATP-203 8.0, Aula 4. [S.l.]: Ilum Escola de Ciência, [2026]. Material de aula (Jupyter Notebook).

[5] SCIKIT-LEARN DEVELOPERS. scikit-learn: machine learning in Python. scikit-learn documentation. Disponível em: https://scikit-learn.org/stable/index.html. Acesso em: 15 nov. 2026.

[6] RADEČIĆ, Dario. Teste U de Mann-Whitney: alternativa não paramétrica ao t-test. DataCamp, 4 maio 2026. Disponível em: https://www.datacamp.com/pt/tutorial/mann-whitney-u-test. Acesso em: 15 nov. 2026.

[7] CASSAR, Daniel R. **Introdução aos testes de hipótese**. LMA-203 8.0, Aula 4. [S.l.]: Ilum Escola de Ciência, [2026]. Material de aula (Jupyter Notebook).

[8] KOHAVI, Ron. A study of cross-validation and bootstrap for accuracy estimation and model selection. In: INTERNATIONAL JOINT CONFERENCE ON ARTIFICIAL INTELLIGENCE (IJCAI), 14., 1995, Montreal. Proceedings [...]. Montreal: Morgan Kaufmann, 1995. p. 1137–1145.

[9] CASSAR, Daniel R. **Modelo linear e baseline**. ATP-203 3.0, Aula 4. [S.l.]: Ilum Escola de Ciência, [2026]. Material de aula (Jupyter Notebook).

[10] CASSAR, Daniel R. **Aprendizado de máquina, k-NN e métricas**. ATP-203 2.1, Aula 4. [S.l.]: Ilum Escola de Ciência, [2026]. Material de aula (Jupyter Notebook).


[11] CASSAR, Daniel R. **Árvore de decisão e floresta aleatória**. ATP-203 4.0, Aula 4. [S.l.]: Ilum Escola de Ciência, [2026]. Material de aula (Jupyter Notebook).

[12] CASSAR, Daniel R. **Otimização de hiperparâmetros com Optuna**. ATP-203 7.1, Aula 4. [S.l.]: Ilum Escola de Ciência, [2026]. Material de aula (Jupyter Notebook).

[13] BOBBITT, Zach. What is Balanced Accuracy? (Definition & Example). Statology, 2021. Disponível em: https://www.statology.org/balanced-accuracy/. Acesso em: 15 nov. 2026.

[14] CASSAR, Daniel R. **Outras métricas e tipos de classificação**. ATP-203 9.0, Aula 4. [S.l.]: Ilum Escola de Ciência, [2026]. Material de aula (Jupyter Notebook).

[15] WILBER, Jared. Precision & recall. MLU-Explain, [s. d.]. Disponível em: https://mlu-explain.github.io/precision-recall/. Acesso em: 15 nov. 2026.


## Desenvolvedora do Projeto
- **Bruna Fujihashi** - [Bruna Fujihashi](https://github.com/buruna087)<br>
Estudante do Bacharelado em Ciência e Tecnologia na Ilum Escola de Ciência.

## Professor responsável
| <img loading="lazy" src="https://github.com/user-attachments/assets/17dfa7bf-5ca9-42df-b63e-917827fc6308" width=115><br><sub> [Prof. Dr. Daneiel Roberto Cassar](http://lattes.cnpq.br/1717397276752482) | 
| :--: |
