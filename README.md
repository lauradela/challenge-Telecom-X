Desafio-Telecom-X

## Relatório de Análise de Evasão de Clientes

  Este relatório foi elaborado com base no conceito de aprendizado centrado em desafios, desenvolvido em parceria entre a Apple e a Alura. Seu objetivo é investigar as causas do alto índice de evasão (Churn) de clientes da empresa Telecom X, identificando padrões de comportamento que levaram ao cancelamento dos diferentes serviços oferecidos ao longo de um período de seis anos.

O processo envolveu as etapas de remoção, transformação, limpeza e análise exploratória dos dados (ETL). Como etapa final, este relatório detalha todo o processo realizado, explicando as metodologias adotadas em cada fase da análise.

### Introdução

>Inicialmente, sem a limpeza dos dados, o estudo revelou que  num período de 6 anos, 25,7% dos clientes cancelaram seus planos, representando uma perda significativa de receitatando uma perda significativa de receita.
Numa análise mais elaborada, foi possível identificar que a evasão de clientes no período desses 6 anos foi bastante elevada:  apenas 5% dos clientes permaneceram fiéis à Telecom X, o maior grupo de clientes (cerca de 9%) manteve-se na empresa por apenas 1 mês, o que sugere uma alta taxa de cancelamento logo após a aquisição do serviço.
----------------------------------------------
### Ferramenta Utilizadas:

>requests - para requisições HTTP e acesso a dados externos

>pandas - para manipulação e análise de dados

>seaborn - para visualização de daodos estatísticos

>matlotib - para criação de gráficos e visualizações
numpy - para operações numericas e manipulação de arrays

>os -  usado para interagir com o sistema operacional.
---------------------------------------------------
Limpeza e Tratamento dos Dados

>. Importação do arquivo a partir da URL  localizada no GITHUB

>. Normalização: as colunas que tinham informações em forma de dicionário foram "desdobradas", ou seja, cada item do dicionário virou uma coluna separada, deixando os dados mais organizados e fáceis de entender.

>. o arquivo foi salvo em um DataFrame chamado df_final como um arquivo CSV
.eliminação de dados nulos ou ausentes, strings vazias, linhas duplicadas e correção de colunas do tipo object para float
----------------------------------------------
Durante o processo de limpeza da base de dados, foram removidos 11 clientes que apresentavam tenure = 0 (ou seja, sem tempo de permanência) e valores ausentes nas colunas 'Churn' e 'Charges.Total'.
--------------------------------------------------
##* Análise Exploratória

>O serviço mais utilizado é o Phone Service (assinatura de serviço telefônico), com 6.560 clientes .
A taxa de churn entre quem tem só uma linha foi relativamente baixa, o que indica que esse grupo é mais estável se comparado com clientes que têm várias linhas, percebe=se diferenças de comportamento.

Clientes com múltiplas linhas têm uma taxa de churn levemente maior do que aqueles com apenas uma linha.
Essa pequena diferença indica que a simples posse do serviço telefônico não é um fator determinante isolado para a evasão.

A maioria dos clientes (aproximadamente 90%) possui o serviço telefônico ativo. Entre esses clientes, a taxa de churn observada é de 26,75%, ligeiramente superior à taxa de evasão de 25% registrada entre os clientes que não possuem o serviço.
A diferença entre os grupos não é muito grande, mas pode indicar que clientes com múltiplas linhas estão mais expostos a problemas técnicos ou cobranças, possuem perfis mais complexos, o que pode aumentar a chance de cancelamento.

Já os clientes com uma única linha mostram maior fidelidade, podendo representar um perfil mais simples e estável de usuário.

Embora a diferença não seja extrema, entender o comportamento de clientes com múltiplas linhas pode ajudar a identificar melhorias no serviço ou em pacotes oferecidos para esse público. Estratégias de retenção específicas podem ser exploradas para esse grupo.


InternetService e seus adicionais:
Número de clientes com somente Internet: 685
Total de clientes com Internet: 5504
Percentual de clientes com somente Internet: 12.45%

### Churn por Tipo de Internet 

![Gráfico de Churn](tipo_ de_ internet.png)

### Proporção de Clientes por Serviços Adicionais de Internet
![Gráfico de Adicionais de Internet/Proporção]
(adicionaisInt.png)

Parece evidente que os serviços adicionais de internet contribuem para uma menor taxa de evasão, principalmente aqueles que dependem de um feedback da empresa.

### Churn por tipo de Contrato (tipo_de_contrato.png)

Há um claro efeito protetor da fidelização: quanto maior a duração do contrato, menor a evasão.

### Churn por faixa Etária
(seniorCit.png)

### Churn por Senior
(proporcaoChurn.png)

Isso indica que clientes mais velhos talvez necessitem de  um atendimento mais direcionado a esse público.

Clientes com dependentes e companheiros apresentam um comportamento muito semelhante, enquanto aqueles sem vínculos familiares demonstram uma taxa de evasão maior, indicando que o comprometimento pessoal pode estar associado a maior fidelidade ao serviço

## Análise das colunas numéricas:
SeniorCitizen: A maioria dos clientes (cerca de 84%) não é idosa, enquanto aproximadamente 16% são idosos.

tenure: O tempo médio de permanência é cerca de 32,5 meses, com mediana de 29 meses. Isso indica que metade dos clientes está com a empresa há menos de 29 meses. O tempo varia bastante, de 1 a 72 meses.

Charges.Monthly: A média das mensalidades é aproximadamente R$64,89, com valores que variam entre R$18,25 e R$118,75. O desvio padrão é alto (cerca de 30), indicando grande variação nas cobranças mensais.

Charges.Total: A média é de aproximadamente R$2.290,00, porém os valores vão de R$18,80 até quase R$8.700,00. Isso sugere que alguns clientes estão há muito tempo na base, enquanto outros são recentes.

Contas_Diarias: A média é 2,16, com desvio padrão de 1,00, mostrando que a maioria dos clientes gasta entre aproximadamente 1,19 (25º percentil) e 3,00 (75º percentil) por dia.


## Análise das colunas categóricas:
gender: A divisão entre homens e mulheres é praticamente igual, com uma leve predominância masculina.

Partner: Cerca de 48% dos clientes possuem parceiro(a), enquanto 52% não possuem.

Dependents: Aproximadamente 30% dos clientes têm dependentes, e 70% não têm.

PhoneService: A grande maioria (cerca de 90%) possui serviço de telefone.

MultipleLines: Entre os clientes com telefone, a divisão entre ter múltiplas linhas ou não é equilibrada; cerca de 45% têm múltiplas linhas.

InternetService: A maior parte dos clientes usa internet via Fiber optic (44%), seguida por DSL (34%) e 22% não possuem internet.

OnlineSecurity: Cerca de 29% dos clientes contratam segurança online, enquanto 50% não contratam e 21% não têm serviço de internet.

OnlineBackup: 35% possuem backup online, 44% não possuem e 21% não têm internet.

DeviceProtection: Proteção de dispositivos está presente em 34% dos clientes, ausente em 44%, e 21% não têm internet.

TechSupport: Aproximadamente 29% têm suporte técnico, 50% não têm, e 21% não possuem internet.

StreamingTV: Cerca de 39% usam streaming de TV, 40% não usam, e 21% não têm internet.

StreamingMovies: Streaming de filmes está presente em 39%, ausente em 40%, e 21% não possuem internet.

Contract: O tipo de contrato mais comum é mensal (Month-to-month, 55%), seguido por contrato de 2 anos (24%) e 1 ano (21%).

PaperlessBilling: Cerca de 59% usam faturamento eletrônico, 41% usam faturas em papel.

PaymentMethod: O método de pagamento mais comum é Electronic check (34%), seguido por Mailed check (23%), Bank transfer (22%) e Credit card (22%).

