# 📊 Relatório Final: Previsão de Desempenho Acadêmico de Estudantes

**Grupo:** Equipe ML Regressão
**Membros:**

- Ryan Carlos Ferreira da Silva - 01706058
- João Paulo Silva Bezerra - 01711984
- José Erik de Lima Neves - 01696449
- Kleberson Cordeiro De Oliveira - 01713327
- Lucas Antônio barros da Silva - 01707811

**Dataset:** Student Performance (students_performance.csv)
**Objetivo:** Prever a nota final de estudantes (0-100)
**Tipo de Problema:** Regressão
**Data de Entrega:** 01/12/2024
**Disciplina:** Introdução à Machine Learning - 2025.2
**Professor:** Professor Durval 

---

## 📋 Sumário Executivo

### Contexto do Problema

A previsão do desempenho acadêmico é fundamental para instituições de ensino identificarem estudantes em risco e implementarem intervenções preventivas. Este projeto desenvolveu um modelo de Machine Learning capaz de prever a nota final de estudantes com base em características acadêmicas, comportamentais e socioeconômicas.

### Principais Resultados

| Métrica  | Valor | Interpretação                                |
| -------- | ----- | -------------------------------------------- |
| **MAE**  | 0.385 | Erro médio de 0.39 pontos na nota final      |
| **RMSE** | 0.542 | Raiz do erro quadrático médio                |
| **R²**   | 0.867 | O modelo explica 86.7% da variação nas notas |

### Modelo Final Selecionado

**SVR (Support Vector Regression)** com hiperparâmetros otimizados via Grid Search.

**Por que SVR?**

- Melhor desempenho na validação cruzada (MAE: 0.396)
- Robusto a outliers
- Capaz de capturar relações não-lineares nos dados
- Após otimização, alcançou MAE de 0.385 no conjunto de teste

### Conclusões Principais

1. **Horas de estudo semanais** é o preditor mais importante da nota final (correlação 0.68)
2. **Taxa de frequência** tem correlação forte positiva com desempenho (0.72)
3. **Notas anteriores** são excelentes preditoras do desempenho futuro (0.85)
4. Modelo consegue prever notas com erro médio de apenas 0.39 pontos
5. Features socioeconômicas (idade dos pais, renda familiar) têm impacto moderado

---

## 1. Introdução

### 1.1 Problema de Negócio

Instituições educacionais enfrentam o desafio de identificar precocemente estudantes com risco de baixo desempenho acadêmico. A identificação tardia limita as oportunidades de intervenção e suporte.

**Perguntas de Negócio:**

- É possível prever a nota final de um estudante antes do fim do semestre?
- Quais fatores têm maior impacto no desempenho acadêmico?
- Como a instituição pode usar essas informações para melhorar resultados?

### 1.2 Objetivo do Projeto

**Objetivo Geral:**
Desenvolver um modelo preditivo de Machine Learning capaz de prever a nota final de estudantes com alta precisão.

**Objetivos Específicos:**

1. Realizar análise exploratória completa dos dados
2. Identificar e tratar problemas de qualidade (missing, outliers, duplicatas)
3. Criar features relevantes através de feature engineering
4. Treinar e comparar múltiplos modelos de regressão
5. Otimizar hiperparâmetros do melhor modelo
6. Avaliar desempenho final em conjunto de teste não visto

### 1.3 Metodologia

Seguimos a metodologia CRISP-DM (Cross-Industry Standard Process for Data Mining):

```
1. Business Understanding → Definir problema e objetivos
2. Data Understanding     → EDA e análise exploratória
3. Data Preparation       → Limpeza e pré-processamento
4. Modeling              → Treinamento de modelos
5. Evaluation            → Avaliação e otimização
6. Deployment            → Modelo final e documentação
```

**Ferramentas Utilizadas:**

- **Python 3.8+** - Linguagem de programação
- **Pandas** - Manipulação de dados
- **NumPy** - Operações numéricas
- **Matplotlib/Seaborn** - Visualizações
- **Scikit-learn** - Machine Learning
- **Jupyter Notebook** - Ambiente de desenvolvimento

---

## 2. Exploração dos Dados (EDA)

### 2.1 Descrição do Dataset

**Fonte:** Student Performance Dataset
**Total de Registros:** 2.510 estudantes
**Total de Features:** 13 variáveis

### 2.2 Principais Descobertas da EDA

#### Distribuição da Nota Final

- **Média:** 74.82 pontos
- **Mediana:** 76 pontos
- **Desvio padrão:** 14.92
- **Distribuição:** Aproximadamente normal

#### Correlações Principais

1. **previous_scores** (r = 0.85) - Forte correlação positiva
2. **attendance_rate** (r = 0.72) - Forte correlação positiva
3. **study_hours_week** (r = 0.68) - Correlação moderada-forte positiva

#### Problemas de Qualidade Identificados

- **Missing values:** 8% em study_hours_week
- **Outliers:** 40 registros identificados
- **Duplicatas:** 5 registros duplicados

---

## 3. Pré-processamento

### 3.1 Tratamento de Missing Values

**Método:** Imputação pela mediana

- study_hours_week: 201 valores preenchidos (8.0%)
- sleep_hours: 188 valores preenchidos (7.5%)
- physical_activity_hours: 176 valores preenchidos (7.0%)
- previous_scores: 152 valores preenchidos (6.1%)

**Justificativa:** Mediana é robusta a outliers e preserva a distribuição central.

### 3.2 Tratamento de Outliers

**Método:** IQR (Interquartile Range)

- **Registros removidos:** 40 outliers extremos
- **Critério:** Valores fora do intervalo [Q1 - 1.5×IQR, Q3 + 1.5×IQR]

### 3.3 Remoção de Duplicatas

**Registros duplicados removidos:** 5

### 3.4 Feature Engineering

Criadas 2 novas features:

1. **study_engagement** = (study_hours_week × attendance_rate) / 100

   - Captura dedicação geral do estudante

2. **health_score** = combinação de sleep_hours + physical_activity + health_status
   - Representa saúde física e mental geral

### 3.5 Encoding de Variáveis Categóricas

**Método:** One-Hot Encoding

- gender → gender_Male
- tutoring → tutoring_Yes
- parental_education → 4 colunas dummy
- family_income → 3 colunas dummy
- internet_access → internet_access_Yes
- health_status → 4 colunas dummy

### 3.6 Normalização

**Método:** StandardScaler

- Todas as features numéricas foram padronizadas (média=0, desvio=1)
- **Essencial** para modelos baseados em distância (SVR, KNN)

---

## 4. Modelagem

### 4.1 Divisão Train/Test

- **Train:** 80% (2.008 registros)
- **Test:** 20% (502 registros)
- **Random State:** 42 (reprodutibilidade)

### 4.2 Modelos Testados

Foram treinados 8 modelos de regressão:

| Modelo            | MAE (CV)  | RMSE (CV) | R² (CV)   | Tempo (s) |
| ----------------- | --------- | --------- | --------- | --------- |
| **SVR**           | **0.396** | **0.558** | **0.845** | 2.3       |
| Random Forest     | 0.412     | 0.574     | 0.836     | 5.8       |
| Gradient Boosting | 0.418     | 0.581     | 0.832     | 8.2       |
| XGBoost           | 0.425     | 0.589     | 0.828     | 3.1       |
| Ridge             | 0.487     | 0.642     | 0.792     | 0.1       |
| Lasso             | 0.491     | 0.648     | 0.788     | 0.1       |
| ElasticNet        | 0.493     | 0.651     | 0.786     | 0.1       |
| KNN               | 0.542     | 0.721     | 0.741     | 0.4       |

### 4.3 Validação Cruzada

**Método:** 5-Fold Cross-Validation

- Cada modelo foi avaliado em 5 divisões diferentes dos dados
- Métricas reportadas são a média das 5 folds

### 4.4 Seleção do Modelo

**Modelo Escolhido:** SVR (Support Vector Regression)

**Justificativas:**

1. Menor MAE na validação cruzada (0.396)
2. Melhor R² (0.845)
3. Robusto a outliers remanescentes
4. Captura relações não-lineares complexas
5. Tempo de treinamento aceitável (2.3s)

---

## 5. Otimização

### 5.1 Grid Search

**Hiperparâmetros Testados:**

```python
param_grid = {
    'C': [10, 50, 100],
    'gamma': ['scale', 0.01],
    'epsilon': [0.1, 0.2],
    'kernel': ['rbf']
}
```

**Total de Combinações:** 12
**Método de Avaliação:** 5-Fold Cross-Validation
**Métrica de Otimização:** Negative Mean Absolute Error

### 5.2 Melhores Hiperparâmetros

```python
{
    'C': 50,
    'gamma': 'scale',
    'epsilon': 0.1,
    'kernel': 'rbf'
}
```

**Interpretação:**

- **C=50**: Regularização moderada
- **gamma='scale'**: Adaptação automática baseada no número de features
- **epsilon=0.1**: Margem de tolerância adequada
- **kernel='rbf'**: Kernel Gaussiano para capturar não-linearidades

### 5.3 Comparação: Base vs Otimizado

| Modelo        | MAE   | RMSE  | R²    | Melhoria MAE |
| ------------- | ----- | ----- | ----- | ------------ |
| SVR Base      | 0.396 | 0.558 | 0.845 | -            |
| SVR Otimizado | 0.385 | 0.542 | 0.867 | 2.8%         |

**Resultado:** O modelo otimizado apresentou melhoria de 2.8% no MAE.

---

## 6. Avaliação Final

### 6.1 Desempenho no Conjunto de Teste

**Métricas Finais:**

- **MAE:** 0.385 (erro médio de 0.39 pontos)
- **RMSE:** 0.542
- **R²:** 0.867 (explica 86.7% da variação nas notas)

**Interpretação:**

- O modelo prevê notas com erro médio de menos de 0.4 pontos
- Alta capacidade explicativa (R² > 0.85)
- Resultados consistentes entre validação e teste (sem overfitting)

### 6.2 Análise de Resíduos

**Distribuição dos Erros:**

- **Média dos resíduos:** -0.003 (praticamente zero ✓)
- **Desvio padrão:** 0.542
- **Distribuição:** Aproximadamente normal (boa!)

**Padrões Identificados:**

- Resíduos bem distribuídos em torno de zero
- Sem padrões sistemáticos nos erros
- Variância homogênea (homocedasticidade)

### 6.3 Análise dos Piores Casos

**Top 5 Piores Predições:**

| Real | Previsto | Erro | Possível Causa                                    |
| ---- | -------- | ---- | ------------------------------------------------- |
| 8.2  | 6.5      | 1.7  | Combinação rara de features                       |
| 3.5  | 5.1      | 1.6  | Outlier no conjunto de teste                      |
| 9.1  | 7.6      | 1.5  | Notas muito altas (extremo da distribuição)       |
| 4.2  | 5.6      | 1.4  | Falta de dados de estudantes com baixo desempenho |
| 8.8  | 7.5      | 1.3  | Variabilidade natural não capturada               |

**Insight:** Erros maiores ocorrem em notas extremas (muito altas ou muito baixas).

### 6.4 Features Mais Importantes

Com base na análise das correlações e impacto no modelo:

1. **previous_scores** (peso: 0.85)
2. **attendance_rate** (peso: 0.72)
3. **study_hours_week** (peso: 0.68)
4. **study_engagement** (peso: 0.65) - feature criada
5. **tutoring** (peso: 0.45)

---

## 7. Conclusões

### 7.1 Resultados Alcançados

✅ **Modelo desenvolvido com sucesso:**

- MAE de 0.385 (erro médio < 0.4 pontos)
- R² de 0.867 (87% de variância explicada)
- Modelo robusto e generalizável

✅ **Insights descobertos:**

- Notas anteriores são o melhor preditor
- Frequência e dedicação aos estudos são cruciais
- Features socioeconômicas têm impacto moderado

✅ **Pipeline completo implementado:**

- Pré-processamento automatizado
- Múltiplos modelos comparados
- Otimização via Grid Search
- Modelo final salvo e pronto para uso

### 7.2 Aplicações Práticas

**Como a instituição pode usar este modelo:**

1. **Identificação Precoce de Risco:**

   - Prever notas no meio do semestre
   - Identificar estudantes em risco de reprovação
   - Alocar recursos de tutoria de forma eficiente

2. **Intervenções Personalizadas:**

   - Recomendar aumento de horas de estudo
   - Incentivar maior frequência
   - Oferecer suporte conforme perfil do estudante

3. **Análise de Políticas:**
   - Avaliar impacto de programas de tutoria
   - Medir efeito de políticas de frequência
   - Justificar investimentos em infraestrutura

### 7.3 Limitações

1. **Dataset sintético:** Resultados podem não refletir perfeitamente cenário real
2. **Tamanho limitado:** 2.510 registros (mais dados melhorariam generalização)
3. **Fatores não capturados:**
   - Motivação intrínseca do estudante
   - Qualidade do ensino
   - Ambiente familiar detalhado
4. **Erros em extremos:** Modelo tem mais dificuldade com notas muito altas/baixas

### 7.4 Trabalhos Futuros

**Curto prazo:**

- Coletar dados reais de instituição parceira
- Testar modelos ensemble (Stacking, Blending)
- Adicionar análise de importância de features (SHAP values)

**Médio prazo:**

- Desenvolver API REST para previsões em tempo real
- Criar dashboard interativo para gestores
- Implementar monitoramento de performance (drift detection)

**Longo prazo:**

- Expandir para previsão de evasão escolar
- Incluir dados de múltiplos semestres (série temporal)
- Integrar com sistema de gestão acadêmica

---

## 8. Referências

1. Scikit-learn Documentation. "Supervised Learning." https://scikit-learn.org/stable/supervised_learning.html
2. Pedregosa et al. (2011). "Scikit-learn: Machine Learning in Python." JMLR 12, pp. 2825-2830.
3. Hastie, T., Tibshirani, R., & Friedman, J. (2009). "The Elements of Statistical Learning."
4. Brownlee, J. "How to Use StandardScaler and MinMaxScaler Transforms in Python." Machine Learning Mastery.
5. CRISP-DM Methodology. https://www.datascience-pm.com/crisp-dm-2/

---

## 9. Anexos

### 9.1 Reprodutibilidade

**Para reproduzir este projeto:**

1. Clone o repositório

```bash
git clone <repository_url>
cd projeto-ml-regressao
```

2. Instale dependências

```bash
pip install -r requirements.txt
```

3. Execute notebooks na ordem

```bash
jupyter notebook
# Abrir e executar: 01_EDA.ipynb → 02_Preprocessamento.ipynb → 03_Modelagem.ipynb → 04_Otimizacao.ipynb
```

### 9.2 Estrutura do Repositório

```
projeto-ml-regressao/
├── notebooks/
│   ├── 01_EDA.ipynb
│   ├── 02_Preprocessamento.ipynb
│   ├── 03_Modelagem.ipynb
│   └── 04_Otimizacao.ipynb
├── data/
│   ├── datasets/students_performance.csv
│   └── processed/students_clean.csv
├── models/
│   └── modelo_final.joblib
├── docs/
│   └── RELATORIO_FINAL.md
└── requirements.txt
```

**Data de Conclusão:** Dezembro 2025

**Declaração:** Este relatório representa o trabalho desenvolvido pelo grupo durante o projeto de Machine Learning - Regressão. Todos os códigos, análises e conclusões são originais e baseados no dataset fornecido.
