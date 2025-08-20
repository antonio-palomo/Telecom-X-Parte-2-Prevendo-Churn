# Telecom-X-Parte-2-Prevendo-Churn
Repositório para o Challenge Telecom X parte 2: Prevendo Churn

# 📊 Previsão de Evasão de Clientes (Customer Churn) - Telecom

Este repositório contém um notebook de análise de dados e modelagem preditiva para identificar clientes com maior probabilidade de evasão (churn) em uma empresa de telecomunicações.

Estrutura do repositório:
main/
│
├── README.md
├── Telecom_X_Parte_2_Prevendo_Churn.ipynb # Notebook com análise completa e modelagem preditiva
└── df_tratado.csv # Dataset tratado utilizado no notebook
---

## 📝 Objetivo

O objetivo do projeto é:

- Analisar os fatores que influenciam a evasão de clientes.
- Criar modelos preditivos capazes de identificar clientes com maior risco de churn.
- Fornecer insights para estratégias de retenção de clientes.

---

## 📂 Dataset

- Arquivo utilizado: `df_tratado.csv`  
- Fonte: [Telecom-X](https://github.com/antonio-palomo/Telecom-X-Parte-2-Prevendo-Churn)  
- Principais colunas:
  - `Churn` → indica se o cliente evadiu ou não.
  - `Genero`, `Idoso`, `Partner`, `Dependents` → informações demográficas.
  - `Tempo_Contrato_Meses`, `Faturamento_Mensal`, `Faturamento_Total` → dados financeiros.
  - `Tipo_Internet`, `Tipo_Contrato`, `Metodo_Pagamento` → serviços contratados e tipo de pagamento.
  - Serviços adicionais: `PhoneService`, `Linhas_Adicionais`, `OnlineSecurity`, `TechSupport`, etc.

---

## 🔧 Pré-processamento

- Remoção de colunas irrelevantes:
  - `customerID` → identificador único
  - `Faturamento_Diario` → redundante
- Codificação de variáveis categóricas:
  - Binárias: `Genero`, `Linhas_Adicionais`
  - One-Hot Encoding: `Tipo_Internet`, `Tipo_Contrato`, `Metodo_Pagamento`
- Aplicação de **SMOTE** para balanceamento das classes de churn.
- Normalização das variáveis numéricas para modelos sensíveis à escala.

---

## 📊 Análise Exploratória

- Correlação de variáveis com churn:
  - `Tempo_Contrato_Meses` → negativo, contratos curtos aumentam churn.
  - `Faturamento_Total` → positivo, clientes com gastos maiores têm maior risco.
  - `Tipo_Internet` (Fiber Optic) e contratos Month To Month → maior risco.
- Visualizações:
  - Boxplots de `Tempo_Contrato_Meses` e `Faturamento_Total` vs Churn.

---

## 🤖 Modelagem Preditiva

Modelos treinados:

| Modelo | Tipo | Normalização |
|--------|------|--------------|
| KNN | Baseado em distância | Sim |
| Regressão Logística | Linear | Sim |
| Decision Tree | Baseado em árvore | Não |
| Random Forest | Baseado em árvore | Não |

### Principais métricas

- **Melhor desempenho geral:** Regressão Logística (acurácia 0.80)  
- **Melhor acurácia em árvore:** Random Forest (acurácia 0.79)  
- **Recall classe minoritária:** mais alto em Regressão Logística (0.54)  

### Variáveis mais importantes

- `Tempo_Contrato_Meses`, `Faturamento_Total`, `Faturamento_Mensal`, `Tipo_Internet_Fiber Optic`, `TechSupport`, `Metodo_Pagamento_Electronic Check`, `PaperlessBilling`.

---

## 💡 Insights e Estratégias

- Contratos curtos e Month To Month aumentam risco → oferecer incentivos para contratos mais longos.
- Clientes com Fiber Optic e alto faturamento são mais propensos a churn → oferecer pacotes personalizados e suporte adicional.
- Clientes sem TechSupport ou OnlineSecurity apresentam maior risco → oferecer serviços complementares.
- Electronic Check e Paperless Billing estão associados a maior churn → incentivar métodos de pagamento automáticos.

---

## 🚀 Próximos Passos

- Ajuste de hiperparâmetros dos modelos.
- Testar modelos avançados como XGBoost.
- Implementar monitoramento contínuo de churn.
- Aplicar estratégias de retenção identificadas.

---

## 🛠️ Tecnologias e Bibliotecas Utilizadas

- Python 3  
- Pandas, NumPy, Seaborn, Matplotlib  
- Scikit-learn, Imbalanced-learn (SMOTE)  

---

## 📄 Autor

- **Antonio Palomo**
- Github: [https://github.com/antonio-palomo](https://github.com/antonio-palomo)
