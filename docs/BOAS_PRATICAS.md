# Guia de Boas Práticas - Projeto ML

## 📋 Índice
1. [Organização de Código](#organização-de-código)
2. [Controle de Versão (Git)](#controle-de-versão)
3. [Notebooks Jupyter](#notebooks-jupyter)
4. [Documentação](#documentação)
5. [Trabalho em Equipe](#trabalho-em-equipe)
6. [Machine Learning](#machine-learning)

---

## 🗂️ Organização de Código

### Estrutura de Diretórios
```
projeto/
├── data/
│   ├── raw/           # Dados originais (nunca modificar)
│   ├── processed/     # Dados processados
│   └── external/      # Dados de fontes externas
├── notebooks/         # Jupyter notebooks
├── src/              # Código Python reutilizável
├── models/           # Modelos treinados
├── reports/          # Relatórios e figuras
│   └── figures/
├── scripts/          # Scripts executáveis
└── tests/            # Testes (opcional)
```

### Nomeação de Arquivos
✅ **BOM:**
- `etapa1_eda.ipynb`
- `preprocessing_utils.py`
- `model_random_forest_v2.pkl`

❌ **RUIM:**
- `Untitled1.ipynb`
- `teste.py`
- `final_final_v3_agora_vai.pkl`

### Estilo de Código Python (PEP 8)

```python
# ✅ BOM
import pandas as pd
import numpy as np

def calculate_mean_score(scores):
    """Calcula a média dos scores.

    Args:
        scores (list): Lista de scores

    Returns:
        float: Média dos scores
    """
    return np.mean(scores)

# Nome de variável descritivo
student_mean_grade = calculate_mean_score([85, 90, 78])

# ❌ RUIM
import pandas as pd,numpy as np

def calc(s):
    return np.mean(s)

x=calc([85,90,78])
```

---

## 🔄 Controle de Versão (Git)

### Commits

#### Mensagens de Commit
✅ **BOM:**
```bash
git commit -m "feat: adiciona análise de correlação no EDA"
git commit -m "fix: corrige tratamento de valores faltantes"
git commit -m "docs: atualiza README com instruções de instalação"
```

❌ **RUIM:**
```bash
git commit -m "mudanças"
git commit -m "atualizando"
git commit -m "asdfasdf"
```

#### Prefixos Recomendados
- `feat:` - Nova funcionalidade
- `fix:` - Correção de bug
- `docs:` - Documentação
- `style:` - Formatação de código
- `refactor:` - Refatoração
- `test:` - Testes
- `chore:` - Tarefas de manutenção

### Workflow Git

```bash
# 1. Criar branch para feature
git checkout -b feat/data-preprocessing

# 2. Fazer mudanças e commits
git add src/preprocessing.py
git commit -m "feat: adiciona função de normalização"

# 3. Push para remoto
git push origin feat/data-preprocessing

# 4. Abrir Pull Request no GitHub

# 5. Após aprovação, merge na main
```

### .gitignore Essencial

```gitignore
# Python
__pycache__/
*.py[cod]
.Python
venv/
env/

# Jupyter
.ipynb_checkpoints/

# Data (se grande)
data/raw/*.csv
!data/raw/sample.csv  # Exceto sample

# Models (se grande)
models/*.pkl

# IDE
.vscode/
.idea/

# OS
.DS_Store
```

---

## 📓 Notebooks Jupyter

### Estrutura de Notebook

```markdown
# Título do Notebook - Etapa X

**Autor:** [Nome]
**Data:** [DD/MM/YYYY]
**Versão:** 1.0

## Índice
1. [Importações](#imports)
2. [Carregamento de Dados](#load-data)
3. [Análise Exploratória](#eda)
4. [Conclusões](#conclusions)
```

### Células de Código

```python
# ✅ BOM: Célula organizada com comentários
# Carregar e inspecionar dataset
df = pd.read_csv('data/raw/students.csv')
print(f"Shape: {df.shape}")
print(f"Colunas: {df.columns.tolist()}")
df.head()
```

```python
# ❌ RUIM: Célula desorganizada
df=pd.read_csv('data/raw/students.csv')
df.head()
df.shape
df.columns
df.info()
df.describe()
# ... muitas operações em uma célula
```

### Cells Markdown

Use markdown para explicar:
- **O que** você está fazendo
- **Por que** está fazendo
- **O que** você descobriu

```markdown
## Análise de Correlação

Vamos investigar a correlação entre horas de estudo e nota final.
Esperamos uma correlação positiva, pois mais estudo geralmente
leva a melhores resultados.
```

### Visualizações

```python
# ✅ BOM: Visualização completa
plt.figure(figsize=(10, 6))
plt.scatter(df['study_hours'], df['final_grade'], alpha=0.5)
plt.xlabel('Horas de Estudo por Semana')
plt.ylabel('Nota Final')
plt.title('Relação entre Horas de Estudo e Nota Final')
plt.grid(True, alpha=0.3)
plt.tight_layout()
plt.savefig('reports/figures/study_vs_grade.png', dpi=300)
plt.show()
```

### Antes de Fazer Commit

```bash
# 1. Limpar outputs (para reduzir tamanho)
# No Jupyter: Cell > All Output > Clear

# 2. Restart & Run All
# Garantir que notebook executa do início ao fim

# 3. Salvar
# File > Save and Checkpoint
```

---

## 📚 Documentação

### Docstrings

```python
def preprocess_data(df, strategy='mean'):
    """
    Pré-processa o dataset de estudantes.

    Aplica as seguintes transformações:
    - Tratamento de valores faltantes
    - Codificação de variáveis categóricas
    - Normalização de features numéricas

    Parameters
    ----------
    df : pd.DataFrame
        Dataset bruto
    strategy : str, optional
        Estratégia de imputação ('mean', 'median', 'mode')
        Default: 'mean'

    Returns
    -------
    pd.DataFrame
        Dataset processado

    Examples
    --------
    >>> df_clean = preprocess_data(df, strategy='median')
    >>> df_clean.shape
    (2000, 15)
    """
    # Implementação
    pass
```

### README.md

```markdown
# Nome do Projeto

## Descrição
[Breve descrição]

## Instalação
\`\`\`bash
pip install -r requirements.txt
\`\`\`

## Uso
\`\`\`python
python scripts/predict.py --input data.csv
\`\`\`

## Estrutura
[Explicar estrutura de diretórios]

## Contribuidores
- [Nome 1]
- [Nome 2]
```

---

## 👥 Trabalho em Equipe

### Divisão de Tarefas

| Membro | Responsabilidade Principal | Backup |
|--------|---------------------------|---------|
| Alice | EDA e Visualizações | Feature Engineering |
| Bob | Pré-processamento | Modelagem |
| Carol | Modelagem e Otimização | Documentação |
| Dave | Documentação e Deploy | Pré-processamento |

### Comunicação

- **Daily Standup:** Reunião rápida diária (15 min)
  - O que fiz ontem?
  - O que farei hoje?
  - Há bloqueios?

- **Code Review:** Sempre revisar PRs dos colegas
  - Verificar lógica
  - Sugerir melhorias
  - Aprovar ou solicitar mudanças

- **Issues no GitHub:**
  ```markdown
  **Título:** Implementar validação cruzada

  **Descrição:**
  Precisamos implementar K-Fold CV nos top 3 modelos.

  **Tarefas:**
  - [ ] Implementar CV para Random Forest
  - [ ] Implementar CV para XGBoost
  - [ ] Implementar CV para LightGBM
  - [ ] Visualizar resultados

  **Responsável:** @bob
  **Prazo:** 15/02/2025
  ```

### Pull Requests

```markdown
## Descrição
Adiciona análise de importância de features usando SHAP values.

## Mudanças
- Instala biblioteca shap
- Cria notebook com análise SHAP
- Adiciona visualizações de importância

## Checklist
- [x] Código testado
- [x] Documentação atualizada
- [x] Notebook executa
- [ ] Aprovado por revisor

## Screenshots
[Incluir imagem da visualização SHAP]
```

---

## 🤖 Machine Learning

### Data Leakage - CUIDADO!

❌ **NUNCA FAÇA ISSO:**
```python
# ERRADO: Normalizar antes de dividir
scaler = StandardScaler()
X_scaled = scaler.fit_transform(X)  # Usou TODOS os dados!
X_train, X_test = train_test_split(X_scaled, ...)
```

✅ **CORRETO:**
```python
# Primeiro dividir, depois normalizar
X_train, X_test = train_test_split(X, ...)

scaler = StandardScaler()
X_train_scaled = scaler.fit_transform(X_train)  # Fit só no treino
X_test_scaled = scaler.transform(X_test)        # Transform no teste
```

### Reprodutibilidade

```python
# Sempre use random_state para reprodutibilidade
import numpy as np
import random

# Seeds
SEED = 42
np.random.seed(SEED)
random.seed(SEED)

# Em train_test_split
X_train, X_test = train_test_split(X, y, random_state=SEED)

# Em modelos
model = RandomForestRegressor(random_state=SEED)
```

### Salvando Modelos

```python
import joblib

# Salvar modelo e scaler
joblib.dump(model, 'models/random_forest_v1.pkl')
joblib.dump(scaler, 'models/scaler_v1.pkl')

# Carregar
model = joblib.load('models/random_forest_v1.pkl')
scaler = joblib.load('models/scaler_v1.pkl')
```

### Validação

```python
# ✅ BOM: Sempre validar em dados separados
from sklearn.model_selection import cross_val_score

# Treino/Validação/Teste
X_temp, X_test, y_temp, y_test = train_test_split(X, y, test_size=0.2)
X_train, X_val, y_train, y_val = train_test_split(X_temp, y_temp, test_size=0.25)

# Cross-validation no treino
scores = cross_val_score(model, X_train, y_train, cv=5)

# Avaliar no teste APENAS no final
y_pred = model.predict(X_test)
```

---

## 📊 Visualizações

### Configuração Padrão

```python
import matplotlib.pyplot as plt
import seaborn as sns

# Configuração global
plt.style.use('seaborn-v0_8-darkgrid')
sns.set_palette("husl")
plt.rcParams['figure.figsize'] = (10, 6)
plt.rcParams['font.size'] = 12
```

### Template de Gráfico

```python
def plot_distribution(data, column, title=None):
    """Plota distribuição de uma variável."""
    fig, axes = plt.subplots(1, 2, figsize=(14, 5))

    # Histograma
    axes[0].hist(data[column], bins=30, edgecolor='black')
    axes[0].set_xlabel(column)
    axes[0].set_ylabel('Frequência')
    axes[0].set_title(f'Distribuição de {column}')

    # Boxplot
    axes[1].boxplot(data[column].dropna())
    axes[1].set_ylabel(column)
    axes[1].set_title(f'Boxplot de {column}')

    plt.tight_layout()

    if title:
        plt.savefig(f'reports/figures/{title}.png', dpi=300, bbox_inches='tight')

    plt.show()
```

---

## ✅ Checklist Antes de Entregar

### Código
- [ ] Notebook executa do início ao fim
- [ ] Sem células com erros
- [ ] Código comentado
- [ ] Segue PEP 8

### Git
- [ ] Commits descritivos
- [ ] .gitignore configurado
- [ ] README atualizado
- [ ] Tag de versão criada

### Documentação
- [ ] Relatório completo
- [ ] Docstrings nas funções
- [ ] Visualizações salvas
- [ ] Resultados documentados

### Machine Learning
- [ ] Sem data leakage
- [ ] Seeds definidos
- [ ] Modelos salvos
- [ ] Métricas documentadas

---

## 📚 Recursos Adicionais

### Livros
- "Python for Data Analysis" - Wes McKinney
- "Hands-On Machine Learning" - Aurélien Géron

### Cursos Online
- [Kaggle Learn](https://www.kaggle.com/learn)
- [Fast.ai](https://www.fast.ai/)

### Ferramentas
- [GitHub Desktop](https://desktop.github.com/)
- [VS Code](https://code.visualstudio.com/)
- [JupyterLab](https://jupyter.org/)

---

**Última atualização:** Janeiro 2025
