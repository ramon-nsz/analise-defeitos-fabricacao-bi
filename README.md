# 📊 Análise de Defeitos de Fabricação — Power BI

> Dashboard interativo para análise de qualidade industrial desenvolvido na disciplina de **Inteligência de Negócios** — Faculdade Impacta

Print 1 - Dashboard Geral: https://prnt.sc/lQ0iUfGy47cK
Print 2 - Custos: https://prnt.sc/Jdi89F6JEiy2
---

## 🎯 Objetivo do Projeto

Transformar um dataset de defeitos de fabricação industriais em **insights acionáveis** para suportar decisões de controle de qualidade. O dashboard cobre três dimensões principais:

- **Volume** — distribuição de defeitos por tipo e severidade
- **Financeiro** — impacto de custo por categoria e ao longo do tempo
- **Temporal** — padrões sazonais e tendências no semestre

---

## 🖥️ Demonstração

> 📥 Faça o download do arquivo `Trabalho BI.pbix` e abra no Power BI Desktop para explorar o dashboard interativo.

### Página 1 — Dashboard Geral
Visão panorâmica da operação com KPIs, evolução de custos e distribuição de defeitos por tipo e severidade.

### Página 2 — Análise de Custos
Drill-down financeiro com sazonalidade mensal, custo por severidade e comparativos de custo médio.

---

## 🔍 Principais Insights Encontrados

| Insight | Detalhe |
|---|---|
| 📉 Redução de 20% no custo total | De $87k (janeiro) para $70k (junho de 2024) |
| ⚡ Queda mais abrupta do período | $85k → $68k entre março e abril — variação de $17k em um mês |
| 🔄 Padrão oscilatório identificado | Ciclos regulares sugerem sazonalidade no processo fabril |
| 📊 Média do semestre: $77k | Últimos 2 meses abaixo da média — tendência de queda sustentada |

---

## 🗂️ Dataset

Fonte: [Manufacturing Defects — Kaggle](https://www.kaggle.com/datasets/fahmidachowdhury/manufacturing-defects)

| Coluna | Tipo | Descrição |
|---|---|---|
| `defect_id` | ID | Identificador único do defeito |
| `product_id` | ID | Identificador do produto |
| `defect_type` | Categórico | Tipo do defeito (cosmético, funcional, estrutural) |
| `defect_description` | Texto | Descrição detalhada do defeito |
| `defect_date` | Data | Data de detecção |
| `defect_location` | Categórico | Localização no produto (superfície, componente) |
| `severity` | Categórico | Nível de severidade (menor, moderado, crítico) |
| `inspect_method` | Categórico | Método de inspeção (visual, automatizado) |
| `repair_action` | Texto | Ação corretiva tomada |
| `repair_cost` | Numérico | Custo de reparo em moeda local |

---

## 🏗️ Arquitetura do Modelo de Dados

O modelo utiliza uma **tabela fato única** (`defects_data`) com medidas DAX calculadas:

```dax
[Custo Total]    = SUM(defects_data[repair_cost])
[Total Defeitos] = COUNTROWS(defects_data)
[Custo Médio]    = DIVIDE([Custo Total], [Total Defeitos])
```

**Hierarquia de data utilizada:** Ano → Mês → Dia

---

## 🛠️ Tecnologias e Ferramentas

| Ferramenta | Versão | Uso |
|---|---|---|
| Power BI Desktop | Mais recente | Desenvolvimento e publicação do dashboard |
| DAX | — | Medidas calculadas (KPIs, agregações) |
| Power Query (M) | — | ETL: limpeza e transformação dos dados |
| Excel / CSV | — | Dataset fonte |

---

## 📁 Estrutura do Repositório

```
📦 analise-defeitos-fabricacao-bi/
 ┣ 📊 Trabalho BI.pbix              # Dashboard Power BI (abrir no Power BI Desktop)
 ┣ 📄 defects_data.csv              # Dataset original em CSV
 ┣ 📄 defects_data.xlsx             # Dataset original em Excel
 ┣ 📄 Defeitos de fabricação.pdf    # Documentação do dataset
 ┗ 📖 README.md
```

---

## ▶️ Como Executar

1. Faça o clone ou download deste repositório
2. Instale o [Power BI Desktop](https://powerbi.microsoft.com/pt-br/desktop/) (gratuito)
3. Abra o arquivo `Trabalho BI.pbix`
4. Explore as duas páginas do dashboard interativo

> **Requisito:** Power BI Desktop (Windows). Não é necessário conta Power BI para visualização local.

---

## 👥 Equipe

Projeto desenvolvido em grupo para a disciplina de **Inteligência de Negócios**:

- Fernando Stievano
- Marcello Raitz Debortoli
- Gabriel Araújo Lima

---

## 📚 Referências

- Dataset: [Manufacturing Defects — Kaggle (Fahmida Chowdhury)](https://www.kaggle.com/datasets/fahmidachowdhury/manufacturing-defects)
- Ferramenta: [Microsoft Power BI](https://powerbi.microsoft.com)
- Documentação DAX: [Microsoft Learn — DAX Reference](https://learn.microsoft.com/pt-br/dax/)

---

*Desenvolvido para fins acadêmicos e educacionais — Faculdade Impacta, curso de Sistemas de Informação*
