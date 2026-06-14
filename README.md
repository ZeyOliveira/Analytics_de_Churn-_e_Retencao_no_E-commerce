
# Analytics de Churn & Retenção no E-commerce 🛒📊

[![GCP](https://img.shields.io/badge/Google_Cloud-4285F4?style=flat-square&logo=google-cloud&logoColor=white)](https://cloud.google.com/)
[![BigQuery](https://img.shields.io/badge/BigQuery-669DF6?style=flat-square&logo=google-cloud&logoColor=white)](https://cloud.google.com/bigquery)
[![Python](https://img.shields.io/badge/Python-3776AB?style=flat-square&logo=python&logoColor=white)](https://www.python.org/)
[![Power BI](https://img.shields.io/badge/Power_BI-F2C811?style=flat-square&logo=powerbi&logoColor=black)](https://powerbi.microsoft.com/)

Pipeline de dados ponta a ponta envolvendo engenharia analítica em nuvem (GCP/BigQuery), tratamento e Análise Exploratória de Dados (Python) e desenvolvimento de um ecossistema de dashboards para contenção preditiva de evasão de clientes.

🔗 **[Clique aqui para acessar o Portfólio Interativo e Visão de Negócio Completa](([https://sites.google.com/view/portifliopowerbizey/in%C3%ADcio))**

---

## 📌 Contexto e Problema de Negócio

Um grande marketplace de e-commerce enfrentava perda significativa de clientes ativos. O objetivo deste projeto foi centralizar os dados da operação, realizar o diagnóstico técnico dos fatores de atrito (logística, suporte e comportamento) e construir uma infraestrutura analítica para que o time de negócios possa agir de forma preditiva antes que o churn aconteça.

---

## 🏗️ Arquitetura da Solução e Dataflow

O projeto foi estruturado simulando um ambiente de produção real, garantindo governança, performance e isolamento de etapas:

1. **Ingestão & Centralização:** Carga do dataset bruto em um lago de dados no **Google Cloud Platform (GCP)** dentro do **BigQuery**.
2. **Pipeline de Dados & EDA (Python):** Conexão via API segura à GCP. Realização de análise estatística, tratamento de dados inconsistentes/nulos e *Feature Engineering*.
3. **Data Warehouse (Camada Refinada):** Exportação dos dados limpos e modelados de volta para o BigQuery para consumo otimizado.
4. **BI & Visualização:** Conexão direta do **Power BI** ao BigQuery utilizando modelagem dimensional (Star Schema) para atualização eficiente.

---

## 🐍 Engenharia de Dados & Análise Exploratória (EDA)

O coração técnico do projeto está documentado no notebook `notebooks/eda_churn_analysis.ipynb`. As principais etapas desenvolvidas no pipeline Python foram:

*   **Autenticação Segura:** Integração com o BigQuery via Service Account (`google-cloud-bigquery`).
*   **Limpeza e Consistência:** Identificação e tratamento de valores ausentes em variáveis críticas (como tempo de cadastro e score de satisfação).
*   **Feature Engineering (Criação de Variáveis):**
    *   Criação de faixas de inatividade para isolar o comportamento do cliente.
    *   Agrupamento de categorias de produtos para reduzir a cardinalidade nos modelos visuais.
*   **Descobertas Estatísticas Chave da EDA:**
    *   *Inatividade:* Clientes sem interações há mais de 30 dias atingem **50,00% de probabilidade de churn**.
    *   *Atrito no Onboarding:* **32,42% dos novos clientes** abandonam a plataforma nos primeiros 6 meses.
    *   *Alerta de Suporte:* O registro de uma única reclamação formal no SAC **triplica o risco de perda**, elevando o churn para 31,67%.

---

## 📐 Modelagem Dimensional & Dashboard (Power BI)

A modelagem no Power BI foi desenhada seguindo as melhores práticas de Engenharia de Analytics para garantir performance e clareza:

*   **Arquitetura Star Schema:** Separação clara entre tabelas Fato (Histórico de transações/churn) e Tabelas Dimensão (Clientes, Localização, Produtos, Tempo) para evitar redundância e otimizar cálculos em DAX.
*   **Métricas e Indicadores:** Estabeleceu-se a linha de base com a **Taxa de Churn geral em 16,84%** sobre uma base ativa de **4.682 clientes**.
*   **Estrutura de Telas Desenvolvida:**
    1.  *Overview (Saúde da Base):* KPIs macro da operação e quebras por categoria.
    2.  *Perfil Demográfico:* Isolação de variáveis (Clientes solteiros lideram o churn com 26,73%).
    3.  *Análise de Comportamento:* Foco em ciclo de vida e engajamento temporal.
    4.  *Experiência e Atritos:* Cruzamento de reclamações do SAC, notas de satisfação e programas de incentivo (Cashback reduz o churn para 10,97%).

---

## 📁 Estrutura do Repositório

```text
├── imagens/               # Imagens usadas como plano de fundo   
├── notebooks/             # Notebooks Jupyter contendo a EDA e tratamentos em Python
│   └── 01_analise_exploratoria.ipynb
├── insights/               # Apresentação executiva em pdf
├── .gitignore/             # Arquivos sensiveis ignorados
├── requirements.txt        # Bibliotecas/Frameworks usados
└── README.md              # Documentação principal do projeto

