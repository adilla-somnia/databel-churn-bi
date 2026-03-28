# Análise de Churn de Clientes da Databel

A Databel é uma empresa de telecomunicações que opera em todo os Estados Unidos. Este projeto analisa os padrões de churn de clientes para fornecer insights acionáveis e prever o impacto futuro na receita.

> Importante!
> *Churn*: percentual de clientes que cancelaram ou deixaram de utilizar o serviço em um período específico.

## Visão Geral do Projeto

O objetivo deste projeto é identificar os fatores que impulsionam o churn de clientes, como tipo de contrato, seleção de plano, fatores demográficos e comportamento dos clientes, e estimar tanto as perdas de receita históricas quanto projetadas. A análise é apresentada por meio de um relatório dinâmico no Power BI, com painéis interativos.

## Dataset

O dataset contém 6.687 registros de clientes, incluindo:

- Dados Demográficos
    - Estado, Idade, Gênero, Idoso, Menor de 30 anos
- Contratos
    - Tipo de Contrato, Método de Pagamento, Participação em Grupo, Plano Internacional, Plano de Dados Ilimitados, Proteção de Dispositivo e Backup Online
- Uso de Serviços
    - Tempo de Conta, Chamadas Locais e Minutos, Chamadas Internacionais e Minutos, Chamadas ao Suporte ao Cliente, Uso Médio de GB por Mês
- Cobranças
    - Cobrança Mensal, Total de Cobranças, Cobranças Extras de Dados e Internacionais
- Churn
    - Status de Churn, Categoria de Churn, Motivo do Churn

> Nota: O dataset analisado é um recorte em um dado momento da empresa, não são dados temporais.

## Dashboards

### 1. Overview

Fornece uma visão geral de:

- Clientes ativos, clientes perdidos, e receita total
- Cobranças médias mensais (geral e para churners)
- Diminuição da receita (absoluta e %)

### 2. Overview do Churn

![Churn Overview](images/churn_overview.png)

Destaca o churn por:

- Tipo de contrato, tipo de plano, método de pagamento e participação em grupo
- Insight chave: Contratos mensais e clientes que não estão em grupos têm as taxas de churn mais altas.

### 3. Comportamento do Cliente

Explora as diferenças comportamentais entre churners e clientes ativos pelas:

- Chamadas de serviço, tempo de conta e cobranças
- Visualizações mostram que churners entram em contato com o suporte mais frequentemente e deixam a empresa mais cedo, com cobranças mensais médias mais altas.

### 4. Análise Geográfica

Analisa o churn por localização:

- 5 principais estados por número de churners (gráfico de barras)
- 5 principais estados por taxa de churn (funil)
- **Insight**: Embora o churn seja bastante consistente, alguns estados mostram maior perda de clientes e taxa.

### 5. Motivos de Churn

Examina o "porquê" ao mostrar:

- Principais categorias e motivos de churn
- Treemap com a distribuição das 5 principais razões de churn
- **Motivo principal**: Ofertas de concorrentes, seguidas pela experiência com o serviço e questões de preço.

### 6. Especulações do Passado

Mostra o impacto histórico do churn na receita com:

- Receita total perdida devido aos churners
- Totais acumulados e cobranças médias
- KPIs com seletores para análise

### 7. Especulações do Futuro

Prevê o impacto futuro do churn ao longo de 48 meses:

- Projeções mensais de receita com análise baseada em cenários
- Visualização da perda acumulada de receita
- Métricas para perda total de receita, clientes perdidos e clientes restantes

## Metodologia
 
- Criei colunas calculadas e medidas para churn, cobranças e receita
- Criei tabelas dimensionais para estados e outros atributos categóricos para normalizar nomes e melhorar o desempenho de filtros/relacionamentos no Power BI
- Criei bins para idade, tempo de conta e cobranças para melhor segmentação
- Normalizei os dados de planos para combinar planos ilimitados e internacionais
- Usei tanto métricas absolutas quanto relativas para uma narrativa clara

** Para uma análise completa das medidas calculadas e metodologia, consulte a [Documentação Técnica](TECHNICAL.md).

## Ferramentas

- **Power BI** para dashboards e visuais interativos
- **DAX** para colunas e medidas calculadas
- **Plotly & Dash (plano futuro)** para versão interativa na web

## Insights Principais

1. Segmentos de Clientes de Alto Risco:
    - Clientes com contratos mensais e não membros de grupos são os mais propensos a churn.

2. Diferenças Comportamentais:
    - Churners entram em contato com o suporte ao cliente 2,4 vezes mais frequentemente, saem mais cedo e pagam um pouco mais de cobrança mensal.

3. Desalinhamento de Planos:
    - ~80% dos churners tinham o plano de dados ilimitados, mas usavam em sua maioria 0–10GB por mês, resultando em cobranças mais altas por serviços não utilizados.
    - Metade desses churners eram ativos internacionalmente, mas não possuíam plano internacional, gerando cobranças extras significativas (chegando a até $586).
    - Isso sugere que os clientes podem estar escolhendo planos que não se adequam aos seus padrões de uso, gerando insatisfação e churn.

4. Principais Fatores de Churn:
    - As ofertas de concorrentes são a principal razão do churn, seguidas pela experiência com o serviço e preocupações com os preços.

5. Impacto na Receita:
    - O churn histórico impactou significativamente a receita. A análise mostra que, se os churners passados tivessem permanecido ativos por toda a vida útil do cliente, a empresa poderia ter gerado um adicional de $1.26M, um aumento de 17,33% sobre a receita total atual.
    - Projeções futuras indicam que, se o churn continuar na taxa atual, a receita mensal da empresa poderia diminuir 13,6% em dois anos, resultando em uma perda de $20K por mês.
    - Esses achados enfatizam a importância financeira de estratégias de retenção direcionadas e otimização de planos.

<p align="center"> <img src="./images/churn_impact.png"> </p>

## Recomendações / Próximas Ações

Aqui vão algumas ações que podem melhorar a situação do churn na empresa:

+ Otimização de Planos
    + Analisar padrões de uso para redesenhar planos que atendam às necessidades dos clientes (ex.: usuários internacionais ou usuários de baixo consumo de dados) e reduzir o pagamento excessivo.

+ Campanhas de Retenção Direcionadas
    + Focar em clientes com contratos mensais e não membros de grupos que apresentam comportamento de alto risco.

+ Suporte Proativo ao Cliente
    + Identificar clientes propensos ao churn com base no uso de serviços e cobranças e fornecer suporte ou incentivos personalizados.

+ Benchmarking com Concorrentes
    + Investigar as ofertas dos concorrentes que estão causando o churn e explorar ajustes competitivos.

+ Análise Futura
    + Incorporar conjuntos de dados temporais para monitorar tendências de churn ao longo do tempo e aprimorar os modelos preditivos.

## Recursos

Veja mais sobre esse projeto no meu **website**!

<p align="center"> <img src="./images/website.png"> </p>

Você também pode clonar este repositório e abrir o arquivo Power BI incluído nesse repositório (.pbix) para explorar os dashboards de forma interativa. Todos os arquivos de dados necessários estão incluídos para uma experiência completa.
