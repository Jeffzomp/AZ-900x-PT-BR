---
wts:
  title: 21 – Calcular SLAs compostos (5 min)
  module: 'Module 06: Describe Azure cost management and service level agreements'
---
# <a name="21---calculate-composite-slas-5-min"></a>21 – Calcular SLAs compostos (5 min)

Neste passo a passo, determinaremos o SLA de disponibilidade dos serviços do Azure e, em seguida, calcularemos a disponibilidade esperada baseada no SLA composto do aplicativo.

Our example application consists of these Azure services. We will not go in to deep architectural configuration and considerations, the intention here is to give an high level example.

+ **Serviço de aplicativo**: Para hospedar o aplicativo.
+ **Azure AD B2C**: Para autenticar logons de usuários e gerenciar perfis.
+ **Gateway de Aplicativo**: Para gerenciar o acesso e o dimensionamento do aplicativo. 
+ **Banco de Dados SQL do Azure**: Para armazenar dados do aplicativo. 

# <a name="task-1-determine-the-sla-uptime-percentage-values-for-our-application"></a>Tarefa 1: Determinar os valores de porcentagem de tempo de atividade de SLA para o aplicativo

1. Em um navegador, vá para a página [Resumo do SLA para serviços do Azure](https://azure.microsoft.com/en-us/support/legal/sla/summary/).

2. Locate the <bpt id="p1">**</bpt>App Service<ept id="p1">**</ept> SLA uptime value, <bpt id="p2">**</bpt>99.95%<ept id="p2">**</ept>. Click <bpt id="p1">**</bpt>View full details<ept id="p1">**</ept>, and then expand <bpt id="p2">**</bpt>SLA details<ept id="p2">**</ept>. Notice the <bpt id="p1">**</bpt>Monthly uptime percentages<ept id="p1">**</ept> and <bpt id="p2">**</bpt>Service Credits<ept id="p2">**</ept>.

3. Retorne à página Web do SLA e localize o serviço **Azure Active Directory B2C** e determine o valor do tempo de atividade do SLA: **99,9%** . 

4. Localize o valor de tempo de atividade do SLA do **Gateway de Aplicativo**: **99,95%** . 

5. The Azure SQL database uses Premium tiers but is not configured for Zone Redundant Deployments. Locate the <bpt id="p1">**</bpt>Azure SQL Database<ept id="p1">**</ept> SLA uptime value, <bpt id="p2">**</bpt>99.99%<ept id="p2">**</ept>. 

    <bpt id="p1">**</bpt>Note<ept id="p1">**</ept>: There are different uptime values for different configurations and deployments of Azure SQL Database. It is important you are clear on your required uptime values, when planning and costing your deployment and configuration. Small changes in uptime can have impact on service costs as well as potentially increase complexity in configuration. Some other services that may be of interest on the Azure SLA summary web page would include <bpt id="p1">**</bpt>Virtual Machines<ept id="p1">**</ept>, <bpt id="p2">**</bpt>Storage Accounts<ept id="p2">**</ept> and <bpt id="p3">**</bpt>Cosmos DB<ept id="p3">**</ept>.

# <a name="task-2-calculate-the-application-composite-sla-percentage-uptime"></a>Tarefa 2: Calcular a porcentagem de tempo de atividade do SLA composto do aplicativo

1. Nosso aplicativo de exemplo consiste nesses serviços do Azure.

    **% do tempo de atividade do Serviço de Aplicativo** X **% do tempo de atividade do Azure AD B2C** X **% do tempo de atividade do Gateway de Aplicativo do Azure** X **% do tempo de atividade do Banco de Dados SQL do Azure** =  **% do tempo de atividade total**

    que em termos percentuais é o seguinte:

    **99,95%** X **99,9%** X **99,95%** X **99,99%**  = **99,79%**

    Esta é a disponibilidade esperada baseada em SLA de nosso aplicativo com os serviços e arquitetura atuais.

Não entraremos em configurações e considerações arquitetônicas profundas, a intenção aqui é dar um exemplo de alto nível.
