# 📉 Churn Prediction com Deep Learning (Keras)

![Status](https://img.shields.io/badge/Status-Concluído-green)
![Python](https://img.shields.io/badge/Made%20with-Python-blue)
![Keras](https://img.shields.io/badge/Framework-Keras%20%7C%20TensorFlow-orange)

## 📋 Sobre o Projeto

Este projeto consiste na implementação de uma **Rede Neural Artificial** para prever a rotatividade de clientes (**Churn Rate**) em uma instituição financeira.

O objetivo é utilizar dados históricos de clientes (como pontuação de crédito, país, gênero, saldo, etc.) para classificar se um cliente irá encerrar sua conta ou não.

## 🛠️ Tecnologias Utilizadas

* **Linguagem:** Python
* **Manipulação de Dados:** Pandas, Numpy
* **Pré-processamento:** Scikit-Learn (StandardScaler, LabelEncoder)
* **Deep Learning:** Keras (TensorFlow backend)

## 🧠 Arquitetura da Rede Neural

O modelo foi construído utilizando a API `Sequential` do Keras, com uma estrutura de "funil" para condensar as informações progressivamente:

| Tipo de Camada | Neurônios / Taxa | Função de Ativação | Descrição |
| :--- | :--- | :--- | :--- |
| **Input** | 10 (features) | - | Entrada dos dados normalizados |
| **Dense** | 64 | ReLU | Primeira camada oculta |
| **Dropout** | 0.3 | - | Prevenção de Overfitting |
| **Dense** | 32 | ReLU | Segunda camada oculta |
| **Dropout** | 0.3 | - | Prevenção de Overfitting |
| **Dense** | 16 | ReLU | Terceira camada (Funil) |
| **Dropout** | 0.3 | - | Prevenção de Overfitting |
| **Output** | 1 | Sigmoid | Saída binária (0 ou 1) |

## ⚙️ Estratégias de Treinamento

Para garantir um modelo robusto e evitar *overfitting*, foram aplicadas as seguintes técnicas:

1.  **Pré-processamento:** Padronização de variáveis numéricas (`StandardScaler`) e codificação de categóricas (`LabelEncoder`).
2.  **Early Stopping:** O treinamento monitora a perda na validação (`val_loss`) e interrompe o processo automaticamente se o modelo parar de evoluir por 10 épocas consecutivas.
3.  **Dropout:** Desativação aleatória de 30% dos neurônios durante o treino para forçar a rede a aprender caminhos redundantes.

## 📊 Métricas Avaliadas

O desempenho do modelo é avaliado através de:
* **Acurácia:** Taxa global de acertos.
* **F1-Score:** Média harmônica entre precisão e recall (importante para dados desbalanceados).
* **Matriz de Confusão:** Para visualizar Falsos Positivos e Falsos Negativos.

## 🚀 Como Executar

```bash
# Clone o repositório
git clone [https://github.com/SEU-USUARIO/NOME-DO-REPO.git](https://github.com/SEU-USUARIO/NOME-DO-REPO.git)

# Instale as dependências
pip install pandas numpy scikit-learn tensorflow keras

# Execute o script
python main.py
