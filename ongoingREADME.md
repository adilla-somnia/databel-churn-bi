# databel customer churn analysis

*Databel* é uma empresa de telecomunicações que opera em todos os Estados Unidos e busca reduzir sua taxa de churn para reter mais receita.

: **taxa de churn** (ou ***churn rate***): refere-se à taxa de cancelamento de clientes, ou seja, a porcentagem de clientes que deixam de usar os serviços da empresa em um determinado período

## Visão Geral

 Este projeto tem como objetivo identificar os principais fatores que contribuem para o churn, como tipo de contrato, plano, faixa etária e localização geográfica. A análise irá destacar padrões e comportamentos críticos, fornecendo insights valiosos para o desenvolvimento de estratégias de retenção e ações corretivas. O relatório criado no Power BI fornecerá informações acionáveis que apoiarão a equipe da Databel a ajustar suas ofertas e ações para minimizar o churn e maximizar a receita.

 ## Conhecendo o Dataset

 O dataset fornecido pela Databel contém informações sobre os seus clientes, incluindo dados demográficos, de contratos, uso de serviços, informações financeiras e de cancelamento. É importante destacar que esse dataset não é temporal, e sim um recorte de um momento específico do banco de dados da empresa.

 Abaixo estão as principais colunas presentes no dataset:

 ### 1. Informações Pessoais/Demográficas
    - State: Estado do cliente
    - Phone Number: Número de telefone
    - Gender: Gênero do cliente
    - Age: Faixa etária
    - Under 30: Indica se o cliente tem menos de 30 anos
    - Senior: Indica se o cliente é um idoso

### 2. Informações de Contrato
    - Group: Indica se o cliente faz parte de um plano em grupo
    - Number of Customers in Group: Número de pessoas no grupo
    - Device Protection & Online Backup: Se o cliente optou por proteção de dispositivo e backup online
    - Contract Type: Tipo de contrato (mensal ou anual)
    - Payment Method: Método de pagamento
    - Intl Active: Indica se o cliente tem plano de ligações internacionais ativo
    - Intl Plan: Indica se o cliente tem plano internacional
    - Unlimited Data Plan: Indica se o cliente possui plano de dados ilimitado

### 3. Uso de Serviços
    - Account Length (in months): Tempo de permanência do cliente.
    - Local Calls: Número de chamadas locais feitas.
    - Local Mins: Quantidade de minutos de chamadas locais.
    - Intl Calls: Número de chamadas internacionais feitas.
    - Intl Mins: Quantidade de minutos de chamadas internacionais.
    - Customer Service Calls: Número de chamadas feitas ao serviço de atendimento ao cliente.
    - Avg Monthly GB Download: Quantidade média de GB baixados mensalmente.

### 4. Cobranças
    - Monthly Charge: Valor mensal cobrado ao cliente.
    - Total Charges: Total de cobranças acumuladas.
    - Extra International Charges: Cobranças adicionais por serviços internacionais.
    - Extra Data Charges: Cobranças adicionais por consumo extra de dados.

### 5. Churn
    - Churn Label: Indica se o cliente cancelou ou não o serviço.
    - Churn Category: Categoria de churn (se o cliente cancelou, o motivo).
    - Churn Reason: Razão pela qual o cliente cancelou o serviço.

## Funcionamento da Databel

A Databel oferece uma variedade de planos e serviços, permitindo que o cliente escolha a opção que melhor se adequa às suas necessidades:

- **Planos Ilimitados**: fornece GBs ilimitados e permite que o cliente navegue sem se preocupar com o consumo de dados.

- **Planos Internacionais**: fornece cobertura para chamadas internacionais ilimitadas sem cobranças adicionais.

- **Planos Fixos de Internet**: fornece uma quantidade específica de GBs por mês, sem cobranças adicionais caso o limite não seja ultrapassado. Caso o cliente ultrapasse a cota, serão cobradas taxas extras.

- **Planos em Grupo**: proporciona descontos para todos os membros do grupo, tornando os planos mais acessíveis.