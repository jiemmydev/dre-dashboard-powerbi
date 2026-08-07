# 📊 Financial DRE & Variance Analytics Dashboard | Power BI

![Power BI](https://img.shields.io/badge/Power_BI-F2C811?style=for-the-badge&logo=powerbi&logoColor=black)
![DAX](https://img.shields.io/badge/DAX-0078D4?style=for-the-badge&logo=microsoft&logoColor=white)
![Data Modeling](https://img.shields.io/badge/Data_Modeling-Star_Schema-blue?style=for-the-badge)

## 📌 Sobre o Projeto

Este projeto consiste no desenvolvimento de um **Dashboard de DRE (Demonstração do Resultado do Exercício)** focado em inteligência financeira e **Análise de Variância (Orçado vs. Realizado)**. 

A solução foi projetada com layout executivo em tema escuro (*Dark Theme*), permitindo que gestores e diretores identifiquem rapidamente desvios de orçamento, analisem a Receita Bruta real e explorem a causa-raiz dos estouros de custos por categoria de produto e conta contábil.

---

## 🎯 Principais Indicadores (KPIs)

- **Receita Bruta Realizada:** R$ 240,75 Mi *(calculado via DAX para filtrar apenas a linha do DRE contábil)*.
- **Valor Orçado Total:** R$ 146,26 Mi.
- **Valor Realizado Total:** R$ 143,60 Mi.
- **Desvio Absoluto:** -R$ 2,66 Mi.
- **Desvio Percentual (%):** -1,82%.

---

## 🛠️ Funcionalidades & Análises Visuais

1. **Matriz DRE Estruturada:**
   - Exibição das contas na ordem contábil padrão: `Receita Bruta` $\rightarrow$ `Deduções` $\rightarrow$ `Custos` $\rightarrow$ `Despesas` $\rightarrow$ `Impostos`.
   - Comparativo direto entre Orçado, Realizado e Desvio por grupo.

2. **Acompanhamento Temporal (Mês a Mês):**
   - Evolução da curva do **Valor Orçado vs. Valor Realizado** ao longo dos meses de 2019.

3. **Análise Causa-Raiz (Top Desvios):**
   - **Desvio por Conta:** Identificação dos produtos/contas com maior desvio negativo (ex: *Venda de TV LED 32'*, *Galaxy J8*).
   - **Desvio por Nível 2:** Mapeamento das categorias com maior estouro orçamentário (ex: *Outras Receitas*, *Despesas Administrativas*).

---

## 📐 Arquitetura & DAX

- **Modelagem de Dados:** Esquema em Estrela (*Star Schema*) conectando a tabela fato de lançamentos com as dimensões `Plano de Contas`, `Formato DRE` e `Calendário`.
- **Exemplo de Medida DAX (Filtragem de Receita Bruta):**

```dax
Receita Bruta Realizada = 
CALCULATE(
    SUM('Analise_DRE'[Valor Realizado]),
    'Plano de Contas'[Nível 1] = "(+) RECEITA BRUTA"
)
