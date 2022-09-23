---
wts:
  title: 03 – Implantar Instâncias de Contêiner do Azure (10 min)
  module: Module 02 - Core Azure Services (Workloads)
---

# <a name="03---deploy-azure-container-instances-10-min"></a>03 – Implantar Instâncias de Contêiner do Azure (10 min)

In this walkthrough we create, configure, and deploy a container by using Azure Container Instances (ACI) in the Azure Portal. The container is a Welcome to ACI web application that displays a static HTML page. 

# <a name="task-1-create-a-container-instance"></a>Tarefa 1: Criar uma instância de contêiner 

Nesta tarefa, criaremos uma nova instância de contêiner para o aplicativo Web.  

1. Entre no [portal do Azure](https://portal.azure.com).

2. Na folha **Todos os serviços**, procure e selecione **Instâncias de contêiner** e depois **+ Adicionar, + Criar, + Novo**. 

3. Forneça os seguintes detalhes básicos para a nova instância de contêiner (mantenha os padrões para todo o resto): 

    | Configuração| Valor|
    |----|----|
    | Subscription | ***Use a padrão fornecida*** |
    | Resource group | **Criar grupo de recursos** |
    | Nome do contêiner| **mycontainer**|
    | Região | **(EUA) Leste dos EUA** |
    | Origem da imagem| **Docker Hub ou outro registro**|
    | Tipo de imagem| **Público**|
    | Image| **mcr.microsoft.com/azuredocs/aci-helloworld**|
    | Tipo do SO| **Linux** |
    | Tamanho| ***Mantenha o padrão***|


4. Configure the Networking tab (replace <bpt id="p1">**</bpt>xxxxx<ept id="p1">**</ept> with letters and digits such that the name is globally unique). Leave all other settings at their default values.

    | Configuração| Valor|
    |--|--|
    | Rótulo do nome DNS| **mycontainerdnsxxxxx** |

    
    <bpt id="p1">**</bpt>Note<ept id="p1">**</ept>: Your container will be publicly reachable at dns-name-label.region.azurecontainer.io. If you receive a <bpt id="p1">**</bpt>DNS name label not available<ept id="p1">**</ept> error message following the deployment, specify a different DNS name label (replacing the xxxxx) and re-deploy. 

5. Clique em **Revisar e criar** para iniciar o processo de validação automática.

6. Clique em **Criar** para criar a instância de contêiner. 

7. Monitore a página de implantação e a página de **Notificações**. 


# <a name="task-2-verify-deployment-of-the-container-instance"></a>Tarefa 2: Verificar a implantação da instância de contêiner

Nesta tarefa, verificamos se a instância de contêiner está em execução, garantindo que a página de boas-vindas seja exibida.

1. Após a conclusão da implantação, clique no link **Ir para o recurso** na folha de implantação ou no link para o recurso na área de Notificação.

2. Na folha **Visão geral** de **mycontainer**, certifique-se de que o **Status** do seu contêiner seja **Em execução**. 

3. Localize o nome de domínio totalmente qualificado (FQDN).

    ![Captura de tela do painel de visão geral do contêiner recém-criado no portal do Azure, com o FQDN destacado. ](../images/0202.png)

2. Neste passo a passo, vamos criar, configurar e implantar um contêiner do Docker usando as Instâncias de Contêiner do Azure (ACI) no Portal do Azure. 

    ![Captura de tela da mensagem de boas-vindas da ACI exibida em um navegador Web.](../images/0203.png)


O contêiner é um aplicativo Web de Bem-vindo à ACI que exibe uma página HTML estática.

<bpt id="p1">**</bpt>Note<ept id="p1">**</ept>: To avoid additional costs, you can optionally remove this resource group. Search for resource groups, click your resource group, and then click <bpt id="p1">**</bpt>Delete resource group<ept id="p1">**</ept>. Verify the name of the resource group and then click <bpt id="p1">**</bpt>Delete<ept id="p1">**</ept>. Monitor the <bpt id="p1">**</bpt>Notifications<ept id="p1">**</ept> to see how the delete is proceeding.
