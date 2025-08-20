# 📊 Desafio TelecomX – Parte 2: Modelagem Preditiva de Churn

## 🧠 Contexto

Após a conclusão da Parte 1, onde realizamos uma análise exploratória dos dados de evasão de clientes da Telecom X, fomos promovidos à equipe de Machine Learning. Nossa missão agora é desenvolver modelos preditivos capazes de antecipar quais clientes têm maior probabilidade de cancelar seus serviços.

---

## 🎯 Objetivo

- Construir modelos de classificação para prever o churn de clientes.
- Avaliar o desempenho dos modelos com métricas apropriadas.
- Interpretar os fatores mais relevantes para a evasão.
- Propor estratégias de retenção baseadas nos resultados obtidos.

---

## 🧱 Etapas Realizadas

### 1. Separação dos Dados

Dividimos os dados em treino e teste (80% / 20%), garantindo que o balanceamento e a normalização fossem aplicados **somente no conjunto de treino** para evitar vazamento de dados.

### 2. Normalização

Aplicamos **Min-Max Scaling** nas variáveis contínuas, preservando as variáveis binárias. Isso garantiu que todas as features numéricas estivessem na mesma escala para o treino dos modelos.

### 3. Balanceamento

Como o conjunto era **moderadamente desbalanceado** (73% stay, 27% churn), utilizamos **SMOTE (Synthetic Minority Oversampling Technique)** para equilibrar as classes apenas no treino.

### 4. Treinamento de Modelos

Testamos os seguintes modelos de classificação:

- **Logistic Regression**
- **Decision Tree**
- **Random Forest**
- **K-Nearest Neighbors**
- **XGBoost**
- **LightGBM**

Cada modelo foi avaliado **antes e depois do balanceamento com SMOTE**, considerando:

- **F1-Score (principal métrica)**
- **Recall (foco na classe churn)**
- **Matriz de Confusão**

---

## 🛠️ Ajuste de Hiperparâmetros

Aplicamos `GridSearchCV` com validação cruzada estratificada para encontrar os melhores hiperparâmetros da Regressão Logística, que foi o modelo com melhor desempenho geral.

A métrica de otimização foi o **F1-Score da classe minoritária**.

---

## 🔎 Análise de Importância das Variáveis

Com base na Regressão Logística, identificamos as variáveis que mais influenciam a evasão:

| Variável               | Interpretação                                                                 |
|------------------------|------------------------------------------------------------------------------|
| `tenure`               | Clientes com menos tempo têm maior chance de churn                          |
| `Contract_Two year`    | Contratos mais longos reduzem a chance de churn                             |
| `PaymentMethod_Electronic check` | Pagamentos por boleto eletrônico aumentam a evasão            |
| `MonthlyCharges`       | Clientes com cobranças mensais maiores tendem a evadir                      |
| `InternetService_Fiber optic` | Usuários de fibra óptica têm maior probabilidade de churn           |

---

## 📈 Resultados

- **Modelo final**: Regressão Logística com SMOTE e ajuste de hiperparâmetros
- **F1-Score final no teste**: `~0.60` (valores exatos estão no notebook)
- **Recall (classe churn)**: Atingido bom nível de identificação de clientes propensos à evasão
- **Overfitting**: Ausência significativa, confirmada por comparação entre validação e teste

---

## 💡 Estratégias de Retenção Propostas

1. **Fidelização por contrato**: Incentivar planos de 1 ou 2 anos com descontos.
2. **Intervenção proativa**: Acompanhar novos clientes nos primeiros meses (`tenure` baixo).
3. **Revisão de cobrança**: Oferecer alternativas para clientes com alta mensalidade.
4. **Campanhas específicas**: Focar em usuários de fibra óptica e pagamentos eletrônicos.

---

## 📁 Arquivos Disponíveis

- `TelecomX_BR_Parte2.ipynb`: Notebook completo com todo o pipeline de modelagem.
- `dataset.csv`: Base de dados original (opcional).
- Imagens: Matriz de confusão, gráficos de importância, etc.

---

## 🚀 Próximos Passos

- Implantar o modelo em produção.
- Criar sistema de alerta para equipe de retenção.
- Avaliar novos modelos com explainability (SHAP, LIME).
- Monitorar performance ao longo do tempo.

---

👨‍💻 Desenvolvido por: **Rodrigo Cavalcanti**  
📅 Projeto concluído: **Agosto de 2025**
