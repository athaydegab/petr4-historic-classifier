# 🛢️ PETR4 Historic & Institutional Classifier

Este repositório contém um projeto em Python (Jupyter Notebook) focado em prever e classificar os melhores momentos para compra e venda das ações da Petrobras (PETR4). 

A inteligência do modelo cruza dados macroeconômicos globais com o comportamento do fluxo institucional brasileiro.

## Origem dos Dados
* **Movimentação de Carteiras:** Dados extraídos da [CVM - Composição e Diversificação das Aplicações (CDA)](https://dados.cvm.gov.br/dados/FI/DOC/CDA/DADOS/). Usados para identificar o volume de PETR4 retido por fundos de investimento mês a mês.
* **Preços Históricos:** Cotações diárias e mensais da PETR4 (Yahoo Finance/Investing).
* **Eventos Históricos:** Base de dados com marcos políticos, crises mundiais, variações do preço do barril de Brent e alterações na política de preços de combustíveis.

## Tecnologias Utilizadas

### 1. Captura e Extração de Dados
* **`yfinance`**: Coleta de dados históricos diários de preços (Abertura, Fechamento, Máxima, Mínima, Volume) de **PETR4.SA** e da commodity de referência, o petróleo **Brent (BZ=F)**.
* **`requests`**: Automatização de download dos arquivos `.zip` mensais e anuais das lâminas de carteiras institucionais no portal de dados abertos da CVM.

### 2. Manipulação de Dados e Engenharia de Recursos
* **`pandas`**: Leitura de grandes volumes de texto, agrupamento mensal de posições dos fundos e manipulação de séries temporais.
* **`numpy`**: Execução de cálculos matriciais rápidos e criação dos sinais matemáticos que alimentarão o modelo.
* **`zipfile` / `io`**: Manipulação e descompactação dos arquivos da CVM diretamente na memória para poupar espaço em disco.

### 3. Modelagem e Machine Learning (Classificação)
* **`scikit-learn`**: Utilizado para divisão temporal dos dados (`TimeSeriesSplit`), normalização e aplicação de modelos base como:
  * **Random Forest Classifier**
  * **Support Vector Machines (SVM)**
* **`xgboost` / `lightgbm`**: Algoritmos de gradiente boosting de alta performance para lidar com dados estruturados financeiros e capturar relações não-lineares agressivas.

### 4. Análise Gráfica e Visualização
* **`matplotlib` & `seaborn`**: Criação de gráficos estáticos para relatórios, matrizes de confusão, importâncias de variáveis e matrizes de correlação.
* **`plotly`**: Geração de gráficos de linha temporais interativos para aproximar o zoom nos dias exatos de anúncios e crises históricas.


## 📂 Estrutura do Repositório

```text
petr4-historic-classifier/
├── .gitignore
├── README.md
├── requirements.txt
├── data/
│   ├── raw/                 # Dados brutos compactados (CVM, Yahoo Finance)
│   ├── processed/           # Dados limpos e unificados por data
│   └── external/            # Planilhas de eventos históricos e preço do Brent
├── notebooks/
│   ├── 01_data_extraction.ipynb   # Download dos dados CVM e yfinance
│   ├── 02_data_cleaning.ipynb     # Filtros específicos de PETR4 e tratamento de nulos
│   ├── 03_feature_engineering.ipynb # Junção dos eventos, criação de lags e labels (0 ou 1)
│   └── 04_modeling.ipynb          # Treinamento, validação e métricas dos classificadores
├── src/
│   ├── __init__.py
│   ├── extract.py           # Funções e scripts para automação de download
│   ├── transform.py         # Pipeline de limpeza e cruzamento de dados (merge)
│   └── models.py            # Estrutura dos algoritmos de machine learning
└── config/
    └── settings.py          # Variáveis globais, caminhos e chaves de configuração
```

---

## 🚀 Como Executar o Projeto

1. Clone o repositório:
```bash
git clone https://github.com
```

2. Instale as dependências:
```bash
pip install -r requirements.txt
```

3. Abra o notebook principal na pasta `notebooks/` para visualizar as etapas de análise exploratória, engenharia de recursos (feature engineering) e treinamento dos algoritmos.
