# 🛢️ PETR4 Historic & Institutional Classifier

Este repositório contém um projeto em Python (Jupyter Notebook) focado em prever e classificar os melhores momentos para compra e venda das ações da Petrobras (PETR4). 

A inteligência do modelo cruza dados macroeconômicos globais com o comportamento do fluxo institucional brasileiro.

## Origem dos Dados
* **Movimentação de Carteiras:** Dados extraídos da [CVM - Composição e Diversificação das Aplicações (CDA)](https://dados.cvm.gov.br/dados/FI/DOC/CDA/DADOS/). Usados para identificar o volume de PETR4 retido por fundos de investimento mês a mês.
* **Preços Históricos:** Cotações diárias e mensais da PETR4 (Yahoo Finance/Investing).
* **Eventos Históricos:** Base de dados com marcos políticos, crises mundiais, variações do preço do barril de Brent e alterações na política de preços de combustíveis.

## Tecnologias Utilizadas
* Python 3
* Pandas & NumPy (Tratamento de dados)
* Scikit-Learn (Modelos de classificação como Random Forest / SVM)
* Matplotlib & Seaborn (Visualização e correlações)

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
