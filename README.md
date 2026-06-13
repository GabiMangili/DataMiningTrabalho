# Pipeline de Inteligência Esportiva para Apoio à Convocação

Projeto prático de **Mineração de Dados** aplicado ao contexto da Copa do Mundo FIFA 2026. O objetivo é integrar dados esportivos do **FBref** com valores de mercado do **Transfermarkt**, explorar padrões de desempenho, identificar perfis de jogadores e treinar modelos para apoiar decisões de convocação.

## Visão Geral

A análise simula o trabalho da startup fictícia **Pitch Intelligence**, contratada para apoiar uma federação nacional na montagem de um elenco competitivo. O projeto percorre as principais etapas de um pipeline de mineração de dados:

1. construção e integração da base;
2. pré-processamento e análise exploratória;
3. clusterização de perfis de jogadores;
4. classificação de jogadores em nível competitivo;
5. recomendação estratégica para convocação.

## Estrutura do Projeto

```text
.
|-- relatorio_final.pdf           # Relatório técnico final
|-- pipeline/
|   `-- datamining.ipynb          # Notebook principal com todo o pipeline
`-- dados/
    |-- dataset_final.csv         # Base final integrada e tratada
    |-- fbref_big5_brasileirao_2526.csv
    `-- transfermarkt.csv         # Dados raspados do Transfermarkt
```

> Observação: embora o enunciado sugira uma pasta `pipeline/` com arquivos separados por etapa, neste projeto o pipeline foi mantido em um único notebook dentro de `pipeline/datamining.ipynb`. As etapas estão divididas em **seções claramente identificadas no notebook**, com células de texto explicando o processo de cada fase.

## Organização do Notebook

O notebook está estruturado da seguinte forma:

- **Etapa 1 - Construção da Base:** carrega FBref e Transfermarkt, trata duplicidades, normaliza nomes e realiza o merge.
- **Etapa 2 - Pré-processamento e EDA:** ajusta tipos, simplifica posições, trata ausentes e gera visualizações exploratórias.
- **Etapa 3 - Clusterização:** aplica K-Means, avalia K com Cotovelo e Silhouette, usa PCA 2D e caracteriza os clusters.
- **Etapa 4 - Classificação:** cria o target por mediana de minutos, evita data leakage e compara Regressão Logística e Random Forest.
- **Etapa 5 - Recomendação Estratégica:** integra os achados para sugerir perfis de elenco e jogadores para observação.

## Principais Resultados

- Base final com **2.925 jogadores**.
- Merge com Transfermarkt cobrindo **196 jogadores**, equivalente a **6,70%** da base final.
- Clusterização com **K-Means (K=4)**, identificando perfis de atacantes, defensores, goleiros e jogadores de apoio/equilibrados.
- Classificação com **Regressão Logística** e **Random Forest**, com F1-Score próximo de **0,94**.
- Discussão estratégica sobre falso positivo, falso negativo, custo-benefício e limitações dos dados.

## Como Executar

1. Abra o arquivo `pipeline/datamining.ipynb`.
2. Execute as células em ordem.
3. Certifique-se de que os arquivos `dados/transfermarkt.csv` e `dados/fbref_big5_brasileirao_2526.csv` estejam disponíveis.

O notebook foi ajustado para carregar os dados tanto em ambiente local quanto em ambiente tipo Google Colab.

## Relatório Final

O arquivo [`relatorio_final.pdf`](relatorio_final.pdf) contém a versão final formatada do trabalho, com metodologia, gráficos, resultados, interpretação de negócio, recomendação estratégica e checklist de aderência ao enunciado.

## Tecnologias Utilizadas

- Python
- Pandas e NumPy
- Matplotlib e Seaborn
- BeautifulSoup e Requests
- Scikit-learn
- Jupyter Notebook
