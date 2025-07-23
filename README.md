# Case Técnico Datarisk - Previsão de Inadimplência

## Descrição do Projeto

Este repositório contém a solução para o case técnico de Cientista de Dados Júnior da Datarisk. O objetivo foi construir um modelo de machine learning para prever a probabilidade de inadimplência de clientes com base em dados cadastrais, financeiros e de pagamento.

O processo incluiu uma análise exploratória detalhada, engenharia de variáveis (com destaque para a criação de features de histórico de inadimplência), treinamento e avaliação de múltiplos modelos, e a interpretação do modelo final com SHAP.

## Arquivos na Submissão

* `Datarisk.ipynb`: O notebook Jupyter com todo o processo de análise e modelagem.
* `requirements.txt`: As dependências de bibliotecas Python necessárias.
* `README.md`: Este arquivo de instruções.
* `submissao_case.csv`: O arquivo final com as previsões geradas para a base de teste.

## Requisitos e Como Executar

### 1. Versão da Linguagem
* Este projeto foi desenvolvido e testado com **Python 3.12.6**

### 2. Instalação das Dependências
* Recomenda-se fortemente a criação de um ambiente virtual para evitar conflitos de versão.
    ```bash
    # Exemplo de como criar o ambiente
    python -m venv venv
    source venv/bin/activate  # No macOS/Linux
    .\venv\Scripts\activate   # No Windows
    ```
* Com o ambiente virtual ativado, instale todas as bibliotecas necessárias com o seguinte comando no terminal:
    ```bash
    pip install -r requirements.txt
    ```

### 3. Executando a Solução
* Abra o notebook `Datarisk.ipynb` em um ambiente Jupyter (como VS Code, Jupyter Lab ou Google Colab).
* Para garantir 100% de reprodutibilidade, use a opção **"Kernel > Reiniciar e Executar Todas as Células"** (ou similar).
* Ao final da execução completa do notebook, o arquivo `submissao_case.csv` será gerado no mesmo diretório.
