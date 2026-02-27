# databel-churn-bi

## Columns

Customer ID, Churn Label, Account Length (in months), Local Calls, Local Mins, Intl Calls, Intl Mins, Intl Active, Intl Plan, Extra International Charges, Customer Service Calls, Avg Monthly GB Download, Unlimited Data Plan, Extra Data Charges, State, Phone Number, Gender, Age, Under 30, Senior, Group, Number of Customers in Group, Device Protection & Online Backup, Contract Type, Payment Method, Monthly Charge, Total Charges, Churn Category, Churn Reason

## KPIs

Churn Rate

Churn by Contract Type

Churn by Payment Method

Average Monthly Charge

Revenue Lost Due to Churn
churn rate x average monthly charge

Total Active Customers
customers total - churned customers

### KPIs secundarios

Churn by Age Group

Churn by Plan Type

Churn by Group Size

Churn by Region (State)

Churn by Device Protection

Average Number of Customer Service Calls Before Churn

## pages

página 1 - Executive Overview
Churn Rate
Total Active Customers, Revenue Lost
Linha do tempo de churn, Total active customers por mês

página 2 - Churn Segmentation
Churn by Contract Type, Churn by Payment Method, Churn by Age Group
gráficos de barras ou colunas com essas segs

página 3 - financial impact
revenue lost, average monthly charge
comparação de churn e perda de receita por região, por plano

página 4 - customer insights
churn by customer service calls, churn by group size
heatmaps ou scatter plots pra correlacionar com o numero de chamadas e outros fatores


## Business Problem
- descrever brevemente o problema resolvido
## Data Cleaning
- explicar oq foi feito na limpeza e transf. se aplicavel
## Data Modeling
- descreva como organizou os dados para o BI
## Key Metrics & KPIs
- listar todos os KPIs e explicar como cada um foi calculado
## Dashboard Layout
- explicação de como as páginas estão organizadas e por que
## Business Insights
- com base nas análises, descrever insights estratégicos
## Technical Insights (DAX, M)
- se DAX ou Power Query foi usado, descrever as formulas mais importantes

telecom-churn-bi/
│
├── data/
│   └── raw_dataset.csv
│
├── pbix/
│   └── telecom_churn_analysis.pbix
│
├── dashboard-web/   (futuro dash/plotly)
│
├── images/
│   ├── executive_page.png
│   ├── churn_profile.png
│   ├── data_cleaning_step1.png
│
└── README.md




Projeto 1 — BI Profissional
Customer Churn (Empresa de Telecom)

Esse deve ser seu projeto mais “corporativo”.

Esse dataset é muito usado para churn de telecom (estilo empresa americana fictícia). Perfeito para BI.

💼 Enquadramento de negócio (MUITO IMPORTANTE)

Não apresente como:

"Análise de dataset de churn"

Apresente como:

"Análise estratégica de churn em empresa de telecom para redução de cancelamentos"

Isso muda completamente o peso do projeto.

Estrutura Ideal
1️⃣ Problema de Negócio

Alta taxa de cancelamento

Receita recorrente sendo perdida

Necessidade de identificar perfis de risco

2️⃣ Ferramentas

Power BI (principal)

DAX

Power Query

Modelagem Star Schema

Dash + Plotly (para versão web)

GitHub

Você está certo:
Não precisa forçar Python se o dataset já está limpo. BI forte é sobre modelagem e insight.

Página 1 — Visão Executiva

Taxa geral de churn

Receita perdida

Ticket médio

KPIs principais

Segmentação por tipo de contrato

📌 Página 2 — Perfil de Clientes que Cancelam

Por tipo de contrato (mensal vs anual)

Por tempo de permanência

Por tipo de serviço (internet fibra vs DSL)

Por método de pagamento

📌 Página 3 — Análise Financeira

Receita por segmento

Receita perdida por churn

Impacto por região (se houver)

📌 Página 4 — Recomendações Estratégicas

Essa parte quase ninguém faz — e é aqui que você se diferencia.

Exemplo:

Clientes com contrato mensal têm 3x mais churn → oferecer desconto para migração anual

Clientes novos (< 6 meses) cancelam mais → criar onboarding melhor

Isso mostra maturidade.











Telecom Customer Churn Analysis
1️⃣ Business Problem

Explique como se fosse consultor:

Uma empresa de telecom enfrenta alta taxa de cancelamento. O objetivo é identificar padrões de churn e propor estratégias de retenção.

2️⃣ Dataset Overview

Número de clientes

Número de variáveis

Tipo de variáveis

Receita média

% churn inicial

3️⃣ Data Cleaning & Transformation (Power Query)

Aqui é onde você mostra maturidade.

Crie uma seção tipo:

🔹 3.1 Data Quality Assessment

Exemplo do que você pode escrever:

Verificação de valores nulos

Colunas com tipo incorreto

Inconsistências em TotalCharges

Conversão de tipos (texto → número)

Padronização de categorias

🔹 3.2 Transformations Performed in Power Query

Aqui você pode:

Colocar prints do Power Query

Mostrar cada etapa aplicada

Explicar por que fez

Exemplo:

Converted TotalCharges to numeric type due to import inconsistencies

Created TenureGroup column to segment customers by lifetime

Standardized categorical values (Yes/No)

Created MonthlyRevenue derived metric

Isso mostra pensamento estruturado.

4️⃣ Data Modeling

Isso é o que separa amador de profissional.

Explique:

Você usou Star Schema?

Criou tabelas dimensão?

Criou tabela calendário?

Criou medidas DAX?

Exemplo:

🔹 4.1 Model Structure

Fact table: Customer data

Dimensions:

Contract Type

Payment Method

Internet Service

Tenure Group

Se for dataset flat, você pode explicar que manteve modelo simplificado por se tratar de dataset único, mas estruturou medidas via DAX.

🔹 4.2 Key DAX Measures

Você pode colocar fórmulas simples no README:

Churn Rate = 
DIVIDE(
    CALCULATE(COUNT(Customer[CustomerID]), Customer[Churn] = "Yes"),
    COUNT(Customer[CustomerID])
)

Isso adiciona peso técnico.

5️⃣ Dashboard Design Strategy

Explique por que cada página existe.

Exemplo:

Executive Overview

Foco em tomada de decisão rápida:

Churn rate

Revenue impact

High risk segments

Customer Risk Profile

Identificar padrões comportamentais.

Isso mostra que você não saiu criando gráfico aleatório.

6️⃣ Key Business Insights

Aqui você brilha.

Exemplo:

Customers with month-to-month contracts churn 3x more

Fiber optic users show higher churn than DSL

Customers with < 6 months tenure have highest cancellation rate

Automatic payment users churn less

Depois escreva:

Strategic Recommendation: Incentivize annual contracts and automatic payments.

7️⃣ Project Impact Simulation (opcional, mas impressionante)

Você pode estimar:

If churn is reduced by 5%, estimated revenue retention = $X annually.

Isso é nível consultoria.

📸 Sobre os Prints

Coloque prints de:

Power Query steps panel

Model view

DAX measure screen

Dashboard final

Mas sempre com explicação abaixo da imagem.

Não jogue imagem solta.

# meu passo a passo

num report blank eu abri o arquivo data.csv no power query, ativei o profile e descobri que o arquivo possui 6687 rows
todas as colunas estão 0% erro e 0% empty com exceção das colunas Churn Category(erro 0%, empty 74%) e Churn Reason(erro 0% e empty 74%). isso acontece pois existe uma coluna chamada Churn Label(yes or no) toda preenchida, porém os que tiveram 'No' em churn label ficaram empty em churn category e churn reason, pois churn não se aplica a eles

## divisão de colunas por grupos

### informações pessoais/demograficas

State, phone number, gender, age, under 30, senior

### informações de contrato

group, no of customers in group, device protection online backup, contract type, payment method
intl active, intl plan, unlimited data plan

### usage

account length(in months), local calls, local mins, intl calls, intl mins, customer service calls
avg monthly gb download

### charging

monthly charge, total charges, extra intl charges, extra data charges

### churn

churn label, churn category, churn reason


## data cleaning / manipulation

precisei adicionar ", US" na coluna State pra certificar que nos mapas os estados apareçam no estado correto, nos US
utilizei a função "Add Sufix", com valor ", US"
salvei e fui verificar se os estados estavam aparecendo corretamente no mapa
não estavam, fui no table  view e mudei a categoria da coluna State para "Place". agora sim os locais estão aparecendo corretamente

criei measures

Churned Customers = CALCULATE(COUNTROWS('Databel - Data'), 'Databel - Data'[Churn Label] = "Yes")
Active Customers = CALCULATE(COUNTROWS('Databel - Data'), 'Databel - Data'[Churn Label] = "No")
Total Customers = COUNTROWS('Databel - Data')
Churn Rate = DIVIDE(Churned Customers, Total Customers) [percentage]

Number of Unique Customers = DISTINCTCOUNT('Databel - Data'[Customer ID]) 
- essa aqui foi para verificar que Number of Unique Customers = Total Customers = all rows
não há customers repetidos nesse dataset

Age (bins)
Churned(0 ou 1)
Demographics (Under 30, Other, Senior)

Average Monthly Charge = AVERAGE('Databel - Data'[Monthly Charge])
Monthly Charge Total = SUM('Databel - Data'[Monthly Charge])
Revenue Lost Due to Churn = [Churn Rate] * [Monthly Charge Total]
Revenue Shrinking Rate = DIVIDE([Revenue Lost Due to Churn], ([Monthly Charge Total] + [Revenue Lost Due to Churn]))

## perguntas possiveis

qual a relação de idade, estado e genero com churn?

qual a relação de tipo de contrato, payment method e account length?

qual a relação de charges em planos inlimitados e internacionais?
- customers com intl active mas sem intl plan, pagam mais? cancelam mais?
- customer sem intl active e com intl plan cancelam mais?

churn category, customer service calls e account length?