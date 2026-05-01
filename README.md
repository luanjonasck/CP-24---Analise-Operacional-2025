# 🚗 Revenue Management & Inteligência Operacional para Estacionamentos

## 🎯 Visão Executiva
Este projeto aplica engenharia de dados e estatística descritiva para transicionar a gestão de ativos imobiliários (estacionamentos) de um modelo puramente reativo para uma estratégia avançada de **Revenue Management**. 

A tese principal deste repositório comprova que a sustentabilidade financeira do negócio não reside na métrica de "ocupação física", mas sim na otimização do **RevPAH (Revenue Per Available Hour)**. Através da análise de mais de 10 mil acessos (gerando uma receita analisada de R$192k), foi possível mapear o comportamento do consumidor, modelar a inelasticidade da demanda e projetar um incremento de **+15% na receita**.

## 🛠️ Stack Tecnológico e Arquitetura Analítica
*   **Python (Pandas, NumPy):** Pipeline rigoroso de ETL para ingestão, tratamento e limpeza de logs transacionais. Tratamento explícito de `NaNs` e transformações de tipagem vetorial (parsing e manipulação de datas complexas).
*   **SQL & Modelagem de Dados:** Estruturação em *Star Schema*.
*   **Power BI:** Construção de dashboards executivos com análise de coorte e heatmaps de densidade temporal.

## 📂 Arquitetura do Repositório (DataOps & Pipeline)
A estrutura de diretórios foi desenhada para garantir reprodutibilidade, escalabilidade e a separação estrita entre a experimentação estatística e o código produtivo. Utilizamos uma adaptação da *Medallion Architecture* para os dados físicos.
```text
CP-24---Analise-Operacional-2025/
│
├── README.md              <- Documentação central do projeto e contrato de dados.
├── requirements.txt       <- Dependências do ambiente Python (Pandas, NumPy, etc).
├── .gitignore             <- Exclusão rigorosa de dados sensíveis e arquivos compilados.
│
├── data/                  <- [NÃO VERSIONADO - IGNORADO PELO GIT]
│   ├── raw/               <- (Bronze) Dados originais/imutáveis (Logs nativos e cadastros). Proibida a alteração manual.
│   └── processed/         <- (Gold) Bases refinadas e tabelas de fatos/dimensões para consumo.
│
├── notebooks/             <- (Sandbox) Ambientes interativos (.ipynb) para Análise Exploratória (EDA) e testes de hipóteses estatísticas (v1, v2).
│
├── src/                   <- (Produção) Scripts modulares em Python contendo o pipeline de ETL automatizável.
│   ├── extract.py         <- Ingestão automatizada e parse de tipagem de dados.
│   ├── transform.py       <- Tratamento de NaNs, cálculo do RevPAH, vetorização de regras de negócio.
│   ├── validate.py        <- Data Quality: assertivas de integridade relacional e distribuição.
│   └── export.py          <- Escrita otimizada para o Data Lake / persistência no disco.
│
├── reports/               <- Entregáveis estáticos. Pareceres executivos, simulações de EBITDA e apresentações (PDFs).
│
└── dashboards/            <- Arquivos do Power BI (.pbix) contendo o front-end analítico.
```

## 💡 Insights e Impacto no EBITDA
As transformações de dados revelaram gargalos e oportunidades claras de alavancagem de receita:

1.  **Saturação vs. Ociosidade Criminosa:** Matrizes de calor (Heatmaps) revelaram uma ociosidade superior a 70% nos sábados no período vespertino, gerando um custo fixo (OPEX) ineficiente. *Solução:* Precificação agressiva de fluxo livre ou encerramento de turno.
2.  **O Custo de Oportunidade do Mensalista:** Durante o pico de saturação (08h-11h em dias úteis), a vaga rotativa rende por hora até **12x mais** que a de contrato (mensalista). Foi estruturada uma recomendação de proteção do inventário para maximizar o fluxo.
3.  **Monetização da Tolerância:** Análise de distribuição estatística (assimetria à direita) evidenciou alto volume de evasão logística sem pagamento. A modelagem sugere a redução de tempo de tolerância para 10 minutos (incremento projetado de +2,5%) aliado ao ajuste fino do intervalo entre 60-90 minutos (incremento de +3,5%).

## 🚀 Como Executar o Projeto
1. Clone o repositório: `git clone https://github.com/seu-usuario/revenue-management-parking.git`
2. Instale as dependências analíticas: `pip install -r requirements.txt`
3. Execute os notebooks na pasta `/notebooks` para validar o pipeline de ETL e as inferências estatísticas construídas sobre o arquivo `MOV_CP.csv`.




---

## 📂 Arquitetura do Repositório (DataOps & Pipeline)
A estrutura de diretórios foi desenhada para garantir reprodutibilidade, escalabilidade e a separação estrita entre a experimentação estatística e o código produtivo. Utilizamos uma adaptação da *Medallion Architecture* para os dados físicos.
```text
CP-24---Analise-Operacional-2025/
│
├── README.md              <- Documentação central do projeto e contrato de dados.
├── requirements.txt       <- Dependências do ambiente Python (Pandas, NumPy, etc).
├── .gitignore             <- Exclusão rigorosa de dados sensíveis e arquivos compilados.
│
├── data/                  <- [NÃO VERSIONADO - IGNORADO PELO GIT]
│   ├── raw/               <- (Bronze) Dados originais/imutáveis (Logs nativos e cadastros). Proibida a alteração manual.
│   └── processed/         <- (Gold) Bases refinadas e tabelas de fatos/dimensões para consumo.
│
├── notebooks/             <- (Sandbox) Ambientes interativos (.ipynb) para Análise Exploratória (EDA) e testes de hipóteses estatísticas (v1, v2).
│
├── src/                   <- (Produção) Scripts modulares em Python contendo o pipeline de ETL automatizável.
│   ├── extract.py         <- Ingestão automatizada e parse de tipagem de dados.
│   ├── transform.py       <- Tratamento de NaNs, cálculo do RevPAH, vetorização de regras de negócio.
│   ├── validate.py        <- Data Quality: assertivas de integridade relacional e distribuição.
│   └── export.py          <- Escrita otimizada para o Data Lake / persistência no disco.
│
├── reports/               <- Entregáveis estáticos. Pareceres executivos, simulações de EBITDA e apresentações (PDFs).
│
└── dashboards/            <- Arquivos do Power BI (.pbix) contendo o front-end analítico.
