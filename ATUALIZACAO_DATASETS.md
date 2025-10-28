# 📊 Atualização: Suporte a 5 Datasets

**Data:** 28 de Outubro de 2027
**Versão:** 2.1

---

## ✅ Mudanças Realizadas

### 1. Estrutura de Pastas Atualizada

**Antes:**
```
data/
├── raw/
│   ├── students_performance.csv
│   └── README.md (apenas 1 dataset)
└── processed/
```

**Agora:**
```
data/
├── datasets/
│   ├── students_performance.csv      (Dataset 1)
│   ├── ecommerce_sales.csv           (Dataset 2)
│   ├── energy_consumption.csv        (Dataset 3)
│   ├── housing_prices.csv            (Dataset 4)
│   ├── delivery_time.csv             (Dataset 5)
│   └── README.md                     (⭐ Documentação completa dos 5)
└── processed/
```

### 2. Arquivo Removido

❌ **Removido:** `data/README.md`
- Motivo: Redundante, descrevia apenas 1 dataset
- Substituído por: `data/datasets/README.md` (descreve todos os 5)

### 3. README.md Principal Atualizado

Todas as menções foram atualizadas:

**Mudanças:**
- ✅ Seção "Objetivo do Projeto" agora menciona 5 datasets
- ✅ Nova seção "SOBRE OS DATASETS" lista os 5 com dificuldade
- ✅ Estrutura de pastas atualizada para `data/datasets/`
- ✅ Links atualizados para `data/datasets/README.md`
- ✅ Instruções de "Como Começar" mencionam escolher 1 dos 5

---

## 📊 Datasets Disponíveis

| # | Nome | Prever | Registros | Features | Dificuldade |
|:-:|------|--------|-----------|----------|-------------|
| 1 | 🎓 Desempenho Acadêmico | Nota final (0-100) | 2.510 | 13 | ⭐⭐ |
| 2 | 🛒 Vendas E-commerce | Vendas (R$) | 2.510 | 16 | ⭐⭐⭐ |
| 3 | ⚡ Consumo de Energia | Consumo (kWh) | 2.510 | 16 | ⭐⭐⭐ |
| 4 | 🏠 Preços de Imóveis | Preço (R$) | 2.510 | 17 | ⭐⭐⭐⭐ |
| 5 | 🚚 Tempo de Entrega | Tempo (horas) | 2.510 | 16 | ⭐⭐⭐ |

---

## 📖 Documentação dos Datasets

### Arquivo: `data/datasets/README.md`

Este arquivo contém para CADA um dos 5 datasets:

✅ **Objetivo do problema**
✅ **Características (registros, features)**
✅ **Lista completa de variáveis**
✅ **Aplicação prática**
✅ **Problemas de qualidade dos dados**
✅ **Comparação entre datasets**
✅ **Exemplos de código**

**Total:** 358 linhas de documentação completa!

---

## 🎯 Como os Alunos Escolhem o Dataset

### Passo 1: Ler Documentação
Abrir `data/datasets/README.md` e ver descrição de cada um

### Passo 2: Discutir em Grupo
- Qual tema é mais interessante?
- Qual tem mais relevância prática?
- Qual a dificuldade adequada ao grupo?

### Passo 3: Informar o Professor
Comunicar qual dataset foi escolhido na primeira semana

### Passo 4: Trabalhar com Apenas 1
Usar o mesmo dataset em todas as 5 etapas do projeto

---

## 🔍 Onde Está Cada Informação

### Para Alunos:
1. **Visão geral dos 5 datasets:** `README.md` principal (seção "SOBRE OS DATASETS")
2. **Documentação completa:** `data/datasets/README.md`
3. **Arquivos CSV:** `data/datasets/*.csv`

### Para Professor:
1. **Scripts de geração:** `/datasets/generate_dataset_*.py` (na raiz do projeto)
2. **Validação:** Este arquivo (ATUALIZACAO_DATASETS.md)

---

## ✅ Validação

### Arquivos Verificados:
- [x] `data/datasets/students_performance.csv` existe (187 KB)
- [x] `data/datasets/ecommerce_sales.csv` existe (258 KB)
- [x] `data/datasets/energy_consumption.csv` existe (180 KB)
- [x] `data/datasets/housing_prices.csv` existe (237 KB)
- [x] `data/datasets/delivery_time.csv` existe (249 KB)
- [x] `data/datasets/README.md` existe (11 KB, 358 linhas)

### README.md Principal:
- [x] Objetivo menciona 5 datasets
- [x] Seção "SOBRE OS DATASETS" lista os 5
- [x] Estrutura de pastas atualizada
- [x] Links atualizados para `data/datasets/README.md`

### Arquivos Removidos:
- [x] `data/README.md` removido (redundante)

---

## 💡 Benefícios da Atualização

### Para os Alunos:
✅ **Mais opções** - 5 datasets em vez de 1
✅ **Diferentes dificuldades** - De iniciante (⭐⭐) a avançado (⭐⭐⭐⭐)
✅ **Temas variados** - Educação, negócios, energia, imóveis, logística
✅ **Aprendizado diversificado** - Grupos trabalham com problemas diferentes

### Para o Professor:
✅ **Flexibilidade** - Adaptar a diferentes níveis de turma
✅ **Evitar plágio** - Grupos com datasets diferentes
✅ **Reutilização** - Mesmo material serve múltiplas turmas
✅ **Variedade** - Apresentações finais mais interessantes

---

## 🚀 Próximos Passos

### Para Distribuir aos Alunos:
1. Anunciar que há 5 datasets disponíveis
2. Instruir para lerem `data/datasets/README.md`
3. Definir prazo para escolha (ex: fim da Semana 1)
4. Opcionalmente: distribuir datasets por grupos para evitar repetição

### Para Futuras Turmas:
- Considerar adicionar mais datasets (6º, 7º, etc.)
- Coletar feedback sobre qual dataset foi mais útil
- Ajustar dificuldades com base no desempenho

---

## 📞 Suporte

**Dúvidas sobre os datasets:**
- Consulte `data/datasets/README.md`
- Contate o professor

**Problemas técnicos:**
- Verificar se todos os 5 CSVs estão na pasta `data/datasets/`
- Confirmar que `data/datasets/README.md` existe

---

**✅ Atualização Completa - Template Pronto!**

*Criado em: 28 de Outubro de 2027*
*Versão: 2.1 - Suporte Multi-Dataset*
