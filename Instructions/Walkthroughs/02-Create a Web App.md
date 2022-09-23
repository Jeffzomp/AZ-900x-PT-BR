---
wts:
  title: 02 – Criar um Aplicativo Web (10 min)
  module: Module 02 - Core Azure Services (Workloads)
---
# <a name="02---create-a-web-app-10-min"></a>02 – Criar um Aplicativo Web (10 min)

In this walkthrough, we will create a web app that runs a Docker container. The Docker container contains a Welcome message. 

Azure App Service are actually a collection of four services, all of which are built to help you host and run web applications. The four services (Web Apps, Mobile Apps, API Apps, and Logic Apps) look different, but in the end they all operate in very similar ways. Web Apps are the most commonly used of the four services, and this is the service that we will be using in this lab.

# <a name="task-1-create-a-web-app"></a>Tarefa 1: Criar um aplicativo Web 

Nesta tarefa, você criará um Aplicativo Web do Serviço de Aplicativo do Azure. 

1. Entre no [portal do Azure](http://portal.azure.com/). 

2. Na folha **Todos os serviços**, procure e selecione **Serviços de Aplicativos** e clique em **+ Adicionar, + Criar, + Novo**

3. On the <bpt id="p1">**</bpt>Basics<ept id="p1">**</ept> tab of the <bpt id="p2">**</bpt>Web App<ept id="p2">**</ept> blade, specify the following settings (replace <bpt id="p3">**</bpt>xxxx<ept id="p3">**</ept> in the name of the web app with letters and digits such that the name is globally unique). Leave the defaults for everything else, including the App Service Plan. 

    | Configuração | Valor |
    | -- | -- |
    | Subscription | **Use a padrão fornecida** |
    | Grupo de recursos | **Criar grupo de recursos**|
    | Nome | **myDockerWebAppxxxx** |
    | Publicar | **Contêiner do Docker** |
    | Sistema operacional | **Linux** |
    | Região | **Leste dos EUA** |
    
    **Observação:** Lembre-se de alterar o **xxxx** para que o Aplicativo Web tenha um nome exclusivo.

4. Clique em **Avançar > Docker** e configure as informações do contêiner.  

    | Configuração | Valor |
    | -- | -- |
    | Opções | **Contêiner único** |
    | Origem da imagem | **Docker Hub** |
    | Tipo de acesso | **Público** |
    | Imagem e marca | **mcr.microsoft.com/azuredocs/aci-helloworld** |
    
 **Observação:** O comando de inicialização é opcional e não é necessário neste exercício.

5. Clique em **Revisar + criar** e, em seguida, clique em **Criar**. 

# <a name="task-2-test-the-web-app"></a>Tarefa 2: Testar o aplicativo Web

Nesta tarefa, testaremos o aplicativo Web.

1. Aguarde a implantação do aplicativo Web.

2. Em **Notificações**, clique em **Ir para o recurso**. 

3. Neste passo a passo, vamos criar um aplicativo Web que executa um contêiner do Docker.

    ![O contêiner do Docker exibe uma mensagem de Boas-Vindas.](../images/0801.png)

4. In a new browser window, paste the URl and press enter. The Welcome to Azure Container Instances! welcome message will be displayed.

    ![Captura de tela da página Bem-vindo à Instância de Contêiner do Azure.](../images/0802.png)

5. O Serviço de Aplicativo do Azure é, na verdade, uma coleção de quatro serviços compilados para ajudar a hospedar e executar aplicativos Web. 

Os quatro serviços (aplicativos Web, aplicativos móveis, aplicativos de API e aplicativos lógicos) parecem diferentes, mas no final todos operam de maneiras muito semelhantes.

Parabéns! Você acaba de criar um Serviço de Aplicativo do Azure com sucesso.
