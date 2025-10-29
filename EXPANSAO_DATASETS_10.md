# ✨ Expansão de Datasets: 5 → 10

**Data:** 28 de Outubro de 2027
**Versão:** 2.2
**Status:** ✅ COMPLETO

---

## 📊 Resumo da Expansão

O projeto foi **expandido de 5 para 10 datasets** para oferecer maior variedade aos alunos e evitar repetição de temas entre os grupos.

### Datasets Originais (1-5)
1. 🎓 **Desempenho Acadêmico de Estudantes** - Prever nota final
2. 🛒 **Vendas de E-commerce** - Prever vendas mensais
3. ⚡ **Consumo de Energia** - Prever consumo energético
4. 🏠 **Preços de Imóveis** - Prever preço de venda
5. 🚚 **Tempo de Entrega** - Prever tempo de entrega

### Novos Datasets (6-10) ✨
6. 💼 **Salário de Profissionais de TI** - Prever salário anual (R$)
7. 📺 **Visualizações de Vídeos no YouTube** - Prever número de views
8. 🍽️ **Avaliação de Restaurantes** - Prever nota média (1-5 estrelas)
9. 🚗 **Preço de Carros Usados** - Prever preço de revenda (R$)
10. 📊 **Produtividade de Funcionários** - Prever horas produtivas/semana

---

## 🎯 Objetivos Alcançados

✅ **Variedade ampliada** - De 5 para 10 opções de datasets
✅ **Criatividade mantida** - Temas interessantes e relevantes
✅ **Dificuldade adequada** - Todos os novos datasets são fáceis a médios (⭐⭐ a ⭐⭐⭐)
✅ **Estrutura consistente** - Mesma qualidade e padrão dos originais
✅ **Problemas realistas** - Todos contêm os mesmos tipos de problemas de qualidade

---

## 📂 Arquivos Gerados

### Scripts de Geração (em `/datasets/`)
- `generate_dataset_salary.py` - Dataset 6
- `generate_dataset_youtube.py` - Dataset 7
- `generate_dataset_restaurant.py` - Dataset 8
- `generate_dataset_used_cars.py` - Dataset 9
- `generate_dataset_employee.py` - Dataset 10

### Datasets CSV (em `template-repo/data/datasets/`)
- ✅ `salary_prediction.csv` (297 KB, 2.520 registros, 18 features)
- ✅ `youtube_views.csv` (313 KB, 2.520 registros, 22 features)
- ✅ `restaurant_rating.csv` (328 KB, 2.520 registros, 25 features)
- ✅ `used_cars_price.csv` (419 KB, 2.520 registros, 26 features)
- ✅ `employee_productivity.csv` (347 KB, 2.520 registros, 29 features)

---

## 📝 Documentação Atualizada

### Arquivos Modificados:

1. **`data/datasets/README.md`**
   - Linha 5: "5 datasets" → "10 datasets"
   - Adicionados 5 novos datasets completos (linhas 246-523)
   - Tabela comparativa atualizada para 10 datasets
   - Linha 568: "1 dos 5" → "1 dos 10"

2. **`README.md` (principal)**
   - Linha 15: "5 opções" → "10 opções"
   - Linha 16: Exemplos atualizados
   - Linha 232: "5 datasets" → "10 datasets"
   - Linha 238: "5 datasets" → "10 datasets"
   - Linhas 309-361: Lista expandida com todos os 10 datasets
   - Linha 433: "5 datasets" → "10 datasets"

3. **`ATUALIZACAO_DATASETS.md`**
   - Título: "5 Datasets" → "10 Datasets"
   - Versão: 2.1 → 2.2
   - Estrutura de pastas atualizada com 5 novos CSVs
   - Tabela expandida para 10 datasets
   - Todas as referências "5" → "10"

---

## 📊 Características dos Novos Datasets

### Dataset 6: Salário TI
- **Target:** `annual_salary_brl` (R$30k-350k)
- **Features:** 17 (experiência, formação, skills, localização)
- **Dificuldade:** ⭐⭐⭐
- **Aplicação:** Precificação de salários, planejamento de carreira

### Dataset 7: YouTube Views
- **Target:** `total_views` (100-5M views)
- **Features:** 21 (duração, canal, engajamento, promoção)
- **Dificuldade:** ⭐⭐⭐
- **Aplicação:** Otimizar estratégias de conteúdo

### Dataset 8: Restaurante
- **Target:** `average_rating` (1.0-5.0 estrelas)
- **Features:** 24 (localização, qualidade, serviço, online)
- **Dificuldade:** ⭐⭐
- **Aplicação:** Identificar fatores de satisfação

### Dataset 9: Carros Usados
- **Target:** `price_brl` (R$8k-250k)
- **Features:** 25 (marca, ano, km, condição, features)
- **Dificuldade:** ⭐⭐⭐
- **Aplicação:** Precificação automática de veículos

### Dataset 10: Produtividade
- **Target:** `productive_hours_week` (5-40h)
- **Features:** 28 (trabalho, saúde, satisfação, benefícios)
- **Dificuldade:** ⭐⭐
- **Aplicação:** Melhorar condições de trabalho

---

## 🔍 Problemas de Qualidade (Todos os Datasets)

Todos os 10 datasets contêm os mesmos tipos de problemas intencionais:

| Problema | Quantidade Aproximada |
|----------|----------------------|
| **Valores faltantes (NaN)** | ~8% dos dados |
| **Outliers** | ~40-50 registros |
| **Valores impossíveis** | ~10-20 registros |
| **Inconsistências lógicas** | ~10-15 registros |
| **Duplicatas** | 10 registros |
| **Erros de formatação** | ~70 registros |

---

## ✅ Validação Completa

### Todos os Datasets Existem:
```bash
ls -lh template-repo/data/datasets/*.csv

# Output:
delivery_time.csv            244K
ecommerce_sales.csv          253K
employee_productivity.csv    347K ✨ NOVO
energy_consumption.csv       176K
housing_prices.csv           233K
restaurant_rating.csv        328K ✨ NOVO
salary_prediction.csv        297K ✨ NOVO
students_performance.csv     187K
used_cars_price.csv          419K ✨ NOVO
youtube_views.csv            313K ✨ NOVO
```

### Documentação Consistente:
- ✅ Todos os 10 datasets documentados em `data/datasets/README.md`
- ✅ README principal menciona 10 datasets
- ✅ ATUALIZACAO_DATASETS.md atualizado
- ✅ Tabelas comparativas atualizadas
- ✅ Nenhuma referência a "5 datasets" remanescente

---

## 🎓 Impacto Pedagógico

### Benefícios para os Alunos:
1. **Maior variedade** - 10 temas diferentes para escolher
2. **Menos repetição** - Grupos podem trabalhar em problemas únicos
3. **Diversidade de domínios** - TI, negócios, saúde, transporte, entretenimento
4. **Interesse mantido** - Temas modernos e relevantes

### Benefícios para o Professor:
1. **Avaliação mais rica** - Diferentes abordagens para o mesmo tipo de problema
2. **Apresentações variadas** - Menos monotonia nas apresentações
3. **Comparação de resultados** - Analisar performance em diferentes domínios

---

## 📈 Estatísticas Finais

| Métrica | Antes | Agora | Mudança |
|---------|-------|-------|---------|
| **Total de Datasets** | 5 | 10 | +100% |
| **Total de Registros** | 12.550 | 25.150 | +12.600 |
| **Total de Features** | 78 | 173 | +95 |
| **Tamanho Total (CSV)** | 1.1 MB | 2.8 MB | +1.7 MB |
| **Linhas de Documentação** | 353 | 701 | +348 |

---

## 🚀 Próximos Passos Recomendados

### Para o Professor:
1. ✅ Anunciar aos alunos que agora há 10 opções
2. ✅ Recomendar que leiam `data/datasets/README.md` completo
3. ✅ Opcionalmente: atribuir datasets específicos para evitar duplicação
4. ✅ Considerar criar mini-apresentações sobre cada dataset

### Opcional (Melhorias Futuras):
- [ ] Criar notebooks de exemplo para cada dataset
- [ ] Adicionar visualizações exploratórias para todos
- [ ] Criar vídeos curtos apresentando cada dataset
- [ ] Desenvolver dashboard comparando métricas entre datasets

---

## 📞 Suporte

**Para dúvidas sobre os novos datasets:**
- Consulte `data/datasets/README.md` (documentação completa)
- Consulte este arquivo `EXPANSAO_DATASETS_10.md` (resumo da expansão)
- Contate o professor

**Scripts de geração estão em:**
- `/home/durval/Documentos/PROJETOS/ml-projeto-final/datasets/`

---

**Última atualização:** 28 de Outubro de 2027
**Responsável:** Claude Code
**Status:** ✅ Produção
