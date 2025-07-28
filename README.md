# Case de Risco de Crédito - Previsão de Inadimplência

Este projeto é uma solução completa para um case de ciência de dados focado em risco de crédito, proposto pela **Datarisk**. O objetivo principal é desenvolver um modelo de machine learning capaz de prever a probabilidade de um cliente se tornar inadimplente em suas obrigações financeiras.

## 📝 Descrição do Problema de Negócio

O desafio simula um cenário real de uma consultoria de inteligência de crédito. O objetivo é construir um sistema que, ao receber dados mensais de clientes, possa identificar com antecedência aqueles com maior probabilidade de atrasar um pagamento em **5 dias ou mais**. Essa previsão permite que a empresa tome ações proativas de cobrança, otimizando recursos e reduzindo perdas financeiras. 

## 🛠️ Stack de Tecnologias Utilizadas

* **Linguagem de Programação:** Python 3.10 
* **Bibliotecas de Análise de Dados:** Pandas, NumPy
* **Bibliotecas de Visualização:** Matplotlib, Seaborn
* **Modelagem de Machine Learning:** Scikit-learn, XGBoost
* **Interpretabilidade de Modelos:** SHAP
* **Ambiente:** Jupyter Notebook (rodado via VS Code)

## 📂 Estrutura do Projeto

* `Case_Ciencia_de_Dados.ipynb`: Notebook Jupyter contendo todo o processo, desde a análise exploratória até a modelagem e interpretação dos resultados.
* `requirements.txt`: Arquivo com as dependências de bibliotecas Python para garantir a reprodutibilidade do projeto. 
* `base_cadastral.csv`: informações cadastrais dos clientes, como porte, segmento industrial, CEP, e-mail e data de cadastro.
* `base_info.csv`: dados atualizados mensalmente com informações como renda do mês anterior e número de funcionários.
* `base_pagamentos_desenvolvimento.csv`: histórico de transações anteriores dos clientes, incluindo data de vencimento, valor a pagar, taxa e data de pagamento (quando disponível).
* `base_pagamentos_teste.csv`: transações recentes para as quais você deverá prever a probabilidade de inadimplência.
* `README.md`: Este arquivo com a documentação do projeto.

## 📈 Metodologia

O projeto foi estruturado em um pipeline de ponta a ponta, seguindo as melhores práticas de mercado:

1.  **Análise Exploratória de Dados (EDA):** Uma investigação profunda foi realizada em todas as quatro bases de dados fornecidas (`base_cadastral`, `base_info`, `base_pagamentos_desenvolvimento` e `base_pagamentos_teste`). Foram analisadas as distribuições das variáveis, a presença de valores nulos e as correlações entre elas para gerar insights iniciais.

2.  **Engenharia de Variáveis:** Esta foi uma etapa crucial para enriquecer os dados. As principais features criadas foram:
    * **Variável Alvo (`INADIMPLENTE`):** Criada a partir da regra de negócio de 5 dias de atraso no pagamento. 
    * **Features de Tempo:** `TEMPO_CLIENTE_DIAS` (senioridade do cliente) e `PRAZO_PAGAMENTO_DIAS`, extraídas a partir das colunas de data.
    * **Features de Histórico Comportamental:** Foram criadas as variáveis `QTD_INADIMPLENCIAS_ANTERIORES` e `JA_FOI_INADIMPLENTE`, que capturam o histórico de inadimplência de cada cliente de forma cronológica, tomando o cuidado de evitar vazamento de dados (data leakage).

3.  **Pré-processamento:**
    * **Tratamento de Nulos:** Estratégias de imputação com a mediana (para variáveis numéricas assimétricas) e a moda (para categóricas) foram aplicadas.
    * **Transformações:** Variáveis com distribuição muito assimétrica, como `VALOR_A_PAGAR` e `RENDA_MES_ANTERIOR`, foram normalizadas com transformação logarítmica (`log1p`).
    * **Codificação Categórica:** Variáveis ordinais (`PORTE`) foram tratadas com mapeamento e as nominais (`DDD`, `SEGMENTO_INDUSTRIAL`, etc.) com One-Hot Encoding.

4.  **Modelagem e Avaliação:**
    * Foi estabelecido um modelo de **baseline** (Regressão Logística) para definir uma performance mínima.
    * Modelos mais avançados de ensemble foram treinados, com destaque para o **Random Forest** e o **XGBoost**.
    * Os modelos foram avaliados usando a métrica **AUC (Area Under the Curve)** em um conjunto de validação, por ser mais robusta a classes desbalanceadas. O XGBoost foi selecionado como o modelo final devido à sua performance superior.

## 📊 Resultados e Interpretabilidade

O modelo final (XGBoost) alcançou uma performance robusta no conjunto de validação. Para entender *por que* o modelo toma suas decisões, foi utilizada a biblioteca **SHAP (SHapley Additive exPlanations)**.

**Principais Descobertas:**
* A análise com SHAP revelou que a **TAXA** de juros é a variável de maior impacto na previsão, seguida pelo **histórico de inadimplência do cliente** e pelo **prazo de pagamento**.
* Conforme esperado, clientes com **renda maior** e **mais funcionários** apresentaram um risco menor.
* O modelo aprendeu relações não lineares complexas, confirmando que o comportamento passado é um forte indicador do comportamento futuro.

## 🚀 Como Executar o Projeto

1.  **Clone este repositório:**
    ```bash
    git clone [https://github.com/R1chardJr/Case_Ciencia_de_Dados.git](https://github.com/R1chardJr/Case_Ciencia_de_Dados.git)
    cd Case_Ciencia_de_Dados
    ```

2.  **Crie e ative um ambiente virtual:**
    ```bash
    python -m venv venv
    # No Windows
    .\venv\Scripts\activate
    # No macOS/Linux
    source venv/bin/activate
    ```

3.  **Instale as dependências:**
    ```bash
    pip install -r requirements.txt
    ```

4.  **Execute o Notebook:**
    * Abra o arquivo `Case_Ciencia_de_Dados.ipynb` no Jupyter Lab, Jupyter Notebook ou VS Code.
    * Para garantir a reprodutibilidade, execute todas as células em ordem ("Kernel" > "Restart & Run All").

---
_Este projeto foi desenvolvido como uma solução para um case técnico e serve como uma demonstração de habilidades em análise de dados, engenharia de variáveis e modelagem de machine learning._
