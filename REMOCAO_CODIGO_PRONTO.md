# 🚫 Remoção de Código Pronto - Filosofia Pedagógica

**Data:** 28 de Outubro de 2027
**Motivo:** Alunos devem PESQUISAR e APRENDER, não copiar código pronto

---

## ⚠️ PROBLEMA IDENTIFICADO

O template continha **código pronto** que resolvia exatamente o que era pedido nas atividades. Isso viola a filosofia pedagógica do projeto:

**❌ NÃO PODE:** Dar código pronto que resolve as questões
**✅ PODE:** Dar orientações, conceitos, links para documentação

---

## 🔧 Correções Realizadas

### 1. `data/datasets/README.md`

**ANTES (ERRADO):**
```python
# Exemplo: Dataset de Estudantes
df = pd.read_csv('datasets/students_performance.csv')

# Visualizar primeiras linhas
print(df.head())

# Informações sobre o dataset
print(df.info())

# Estatísticas descritivas
print(df.describe())

# Verificar valores faltantes
print(df.isnull().sum())
```

**DEPOIS (CORRETO):**
```markdown
### 3. Consulte a Documentação do Pandas
Você precisará aprender a usar pandas para trabalhar com os dados.

**Recursos oficiais:**
- [Pandas Documentation](https://pandas.pydata.org/docs/)
- [10 Minutes to Pandas](...)
- [Pandas Cheat Sheet](...)

**O que você vai precisar aprender:**
- Como carregar arquivos CSV
- Como visualizar dados (primeiras linhas, informações gerais)
- Como calcular estatísticas descritivas
- Como detectar valores faltantes

**Não há atalhos!** Você deve pesquisar e aprender.
```

---

### 2. `etapas/etapa2/README.md` - Pré-processamento

**ANTES (ERRADO):**
```python
from sklearn.impute import SimpleImputer

imputer = SimpleImputer(strategy='median')
df[numeric_cols] = imputer.fit_transform(df[numeric_cols])
```

**DEPOIS (CORRETO):**
```markdown
**Pesquise:**
- Documentação do `sklearn.impute`
- Diferentes estratégias de imputação
- Quando usar cada uma
- Como justificar sua escolha tecnicamente
```

**Repetido para:**
- Encoding de categóricas
- Normalização
- Divisão de dados

---

### 3. `etapas/etapa3/README.md` - Modelagem

**ANTES (ERRADO):**
```python
from sklearn.linear_model import LinearRegression

baseline = LinearRegression()
baseline.fit(X_train, y_train)
```

```python
models = {
    'Linear Regression': LinearRegression(),
    'Random Forest': RandomForestRegressor(random_state=42),
    'XGBoost': XGBRegressor(random_state=42),
}
```

**DEPOIS (CORRETO):**
```markdown
Pesquise como implementar regressão linear usando scikit-learn.

**Recursos:**
- Documentação: `sklearn.linear_model.LinearRegression`
- Tutorial de regressão linear

**Pesquise:**
- Como instalar e importar cada biblioteca
- Diferenças entre cada modelo
- Como criar um dicionário de modelos para treinar em loop
```

**Repetido para:**
- Métricas (MAE, RMSE, R²)
- Validação cruzada
- Visualizações (barras, scatter, resíduos)
- Feature importance

---

### 4. `etapas/etapa4/README.md` - Otimização

**ANTES (ERRADO):**
```python
from sklearn.model_selection import GridSearchCV

param_grid = {
    'n_estimators': [100, 200, 300],
    'max_depth': [10, 20, 30, None],
    ...
}

grid_search = GridSearchCV(
    estimator=RandomForestRegressor(random_state=42),
    param_grid=param_grid,
    cv=5,
    scoring='neg_mean_absolute_error',
    n_jobs=-1,
    verbose=2
)
```

**DEPOIS (CORRETO):**
```markdown
**Pesquise:**
- Documentação do `sklearn.model_selection.GridSearchCV`
- Como definir um grid de hiperparâmetros
- Quais hiperparâmetros são importantes para seu modelo
- Como usar cross-validation durante o tuning
```

**Repetido para:**
- Random Search
- Análise de resultados
- Treinamento modelo final
- Salvamento do modelo

---

## 📊 Estatísticas

### Blocos de Código Removidos:

| Arquivo | Blocos Removidos | Linhas Removidas |
|---------|:----------------:|:----------------:|
| `data/datasets/README.md` | 2 | ~30 |
| `etapas/etapa2/README.md` | 3 | ~45 |
| `etapas/etapa3/README.md` | 8 | ~120 |
| `etapas/etapa4/README.md` | 7 | ~110 |
| **TOTAL** | **20** | **~305** |

---

## ✅ O Que Foi Mantido

### Etapa 1 - CORRETO
✅ Já estava certo! Não tinha código pronto, apenas orientações:
```markdown
Pesquise quais bibliotecas são necessárias...
Utilize pandas para carregar o dataset...
Descubra como visualizar as primeiras linhas...
```

### Etapa 5 - CORRETO
✅ Código de demonstração (demo) é OK porque não faz parte da avaliação:
```python
# demo_predicao.py
import joblib
model = joblib.load('models/modelo_final.joblib')
```
Este código é apenas para MOSTRAR o modelo funcionando na apresentação final.

---

## 🎯 Filosofia Pedagógica Aplicada

### ❌ O Que NÃO Fazer
- Dar código que resolve exatamente a questão
- Mostrar implementação completa
- Dar todas as respostas prontas

### ✅ O Que Fazer
- Indicar ONDE pesquisar (documentação, tutoriais)
- Explicar O QUE fazer (objetivos, conceitos)
- Listar TÓPICOS para pesquisar
- Dar orientações genéricas

---

## 📖 Exemplos de Orientações Corretas

### Exemplo 1: Carregamento de Dados
**❌ ERRADO:**
```python
df = pd.read_csv('students_performance.csv')
```

**✅ CORRETO:**
```markdown
**Pesquise:**
- Como carregar arquivos CSV com pandas
- Documentação do `pd.read_csv`
```

### Exemplo 2: Imputação
**❌ ERRADO:**
```python
imputer = SimpleImputer(strategy='median')
df[cols] = imputer.fit_transform(df[cols])
```

**✅ CORRETO:**
```markdown
**Pesquise:**
- Documentação do `sklearn.impute.SimpleImputer`
- Diferentes estratégias (mean, median, most_frequent)
- Como aplicar transformação
```

### Exemplo 3: Grid Search
**❌ ERRADO:**
```python
grid_search = GridSearchCV(
    estimator=model,
    param_grid={'n_estimators': [100, 200]},
    cv=5
)
```

**✅ CORRETO:**
```markdown
**Pesquise:**
- Documentação do `GridSearchCV`
- Como definir grid de parâmetros
- Como usar cross-validation
```

---

## 🔍 Validação Final

### Checklist de Verificação:
- [x] Nenhum bloco de código resolve diretamente as questões
- [x] Todas as orientações apontam para pesquisa
- [x] Links para documentação oficial incluídos
- [x] Conceitos explicados sem dar a solução
- [x] Alunos devem pesquisar e implementar por conta própria

### Arquivos Validados:
- [x] `data/datasets/README.md` - Apenas orientações
- [x] `etapas/etapa1/README.md` - Já estava correto
- [x] `etapas/etapa2/README.md` - Corrigido
- [x] `etapas/etapa3/README.md` - Corrigido
- [x] `etapas/etapa4/README.md` - Corrigido
- [x] `etapas/etapa5/README.md` - Demo OK (não é avaliado)

---

## 💡 Benefícios da Mudança

### Para os Alunos:
✅ **Aprendizado real** - Pesquisam e entendem de verdade
✅ **Desenvolvimento de autonomia** - Aprendem a buscar informação
✅ **Habilidades de pesquisa** - Essencial para carreira
✅ **Compreensão profunda** - Não apenas copiam código

### Para o Professor:
✅ **Avaliação justa** - Não há cola fácil
✅ **Identificação de dificuldades** - Vê onde travam
✅ **Trabalhos originais** - Cada grupo faz diferente
✅ **Ensino efetivo** - Alunos aprendem de verdade

---

## 📞 Como Usar o Template Agora

### Para Alunos:
1. Ler as instruções da etapa
2. Ver O QUE fazer (objetivos)
3. Pesquisar COMO fazer (documentação)
4. Implementar e testar
5. Pedir ajuda ao professor quando travar

### Para Professor:
1. Orientar onde pesquisar
2. Explicar conceitos quando pedirem
3. Revisar implementações
4. Dar feedback construtivo
5. NÃO dar código pronto!

---

## 🎓 Mensagem Final

> **"O objetivo é APRENDER, não apenas entregar!"**
>
> Código pronto não ensina. Pesquisa, tentativa, erro e acerto sim!

---

**✅ Template Validado - Sem Código Pronto!**

*Criado em: 28 de Outubro de 2027*
*Filosofia: Aprendizado Ativo*
