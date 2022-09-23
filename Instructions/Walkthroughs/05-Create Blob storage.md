---
wts:
  title: 05 – Criar um armazenamento de blobs (5 min)
  module: Module 02 - Core Azure Services (Workloads)
---
# <a name="05---create-blob-storage-5-min"></a>05 – Criar um armazenamento de blobs (5 min)

Neste passo a passo, criaremos uma conta de armazenamento e, em seguida, trabalharemos com arquivos de armazenamento de blobs.

# <a name="task-1-create-a-storage-account"></a>Tarefa 1: Criar uma conta de armazenamento 

Nesta tarefa, criaremos uma nova conta de armazenamento. 

1. Entre no portal do Microsoft Azure em <a href="https://portal.azure.com" target="_blank"><span style="color: #0066cc;" color="#0066cc">https://portal.azure.com</span></a>

2. Na folha **Todos os serviços**, procure e selecione **Contas de armazenamento** e depois selecione **+ Adicionar, + Criar, + Novo**. 

3. On the <bpt id="p1">**</bpt>Basics<ept id="p1">**</ept> tab of the <bpt id="p2">**</bpt>Create storage account<ept id="p2">**</ept> blade, fill in the following information (replace <bpt id="p3">**</bpt>xxxx<ept id="p3">**</ept> in the name of the storage account with letters and digits such that the name is globally unique). Leave the defaults for everything else.

    | Configuração | Valor | 
    | --- | --- |
    | Subscription | **Mantenha a padrão fornecida** |
    | Resource group | **Criar grupo de recursos** |
    | Nome da conta de armazenamento | **storageaccountxxxxx** |
    | Location | **(EUA) Leste dos EUA**  |
    | Desempenho | **Standard** |
    | Redundância | **Armazenamento com redundância local (LRS)** |
    
    **Observação**: lembre-se de alterar o **xxxxx** para que tenha um **Nome de conta de armazenamento** exclusivo

5. Clique em **Revisar + Criar** para revisar as configurações da sua conta de armazenamento e permitir que o Azure valide a configuração. 

6. Once validated, click <bpt id="p1">**</bpt>Create<ept id="p1">**</ept>. Wait for the notification that the account was successfully created. 

7. Na página inicial, procure e selecione **Contas de armazenamento** e certifique-se de que sua nova conta de armazenamento esteja listada.

    ![Captura de tela da conta de armazenamento recém-criada no portal do Azure.](../images/0401.png)

# <a name="task-2-work-with-blob-storage"></a>Tarefa 2: Trabalhar com armazenamento de blobs

Nesta tarefa, criaremos um contêiner de blob e carregaremos um arquivo de blob. 

1. Selecione o nome da nova conta de armazenamento, role até a seção **Armazenamento de dados** e, em seguida, selecione **Contêineres**.

2. Click <bpt id="p1">**</bpt>+ Container<ept id="p1">**</ept> and complete the information. Use the Information icons to learn more. When done click <bpt id="p1">**</bpt>Create<ept id="p1">**</ept>.


    | Configuração | Valor |
    | --- | --- |
    | Nome | **container1**  |
    | Nível de acesso público| **Privado (sem acesso anônimo)** |
  

    ![Captura de tela do contêiner de blob recém-criado na conta de armazenamento no portal do Azure.](../images/0402.png)

4. Open a new browser window and search <bpt id="p1">**</bpt>Bing<ept id="p1">**</ept> for an image of a flower. Right click on the image and save it to your VM. 

6. De volta ao Portal, selecione **contêiner1** e depois **Carregar**.

5. Browse for the image file you just saved on your local computer. Select it and then select upload.

   
6. Clique na seta **Avançado**, deixe os valores padrão, mas revise as opções disponíveis e clique em **Carregar**.

    <bpt id="p1">**</bpt>Note<ept id="p1">**</ept>: You can upload as many blobs as you like in this way. New blobs will be listed within the container.

7. Assim que for carregado, clique com o botão direito do mouse no arquivo e observe as opções, incluindo Exibir/Editar, Baixar, Propriedades e Excluir. 

8. Se tiver tempo, revise as opções para Arquivos, Tabelas e Filas.

# <a name="task-3-monitor-the-storage-account"></a>Tarefa 3: Monitorar a conta de armazenamento

1. Volte para a folha da conta de armazenamento e selecione **Diagnosticar e resolver problemas**. 

2. Explore some of the most common storage problems. Notice there are multiple troubleshooters here.

3. On the storage account blade, scroll down to the <bpt id="p1">**</bpt>Monitoring<ept id="p1">**</ept> section and click <bpt id="p2">**</bpt>Insights<ept id="p2">**</ept>. Notice there is information on Failures, Performance, Availability, and Capacity. Your information will be different.

    ![Captura de tela da página Insights da conta de armazenamento.](../images/0403.PNG)

Na guia **Básico** da folha **Criar conta de armazenamento**, preencha as seguintes informações (substitua **xxxx** no nome da conta de armazenamento por letras e dígitos de forma que o nome seja globalmente exclusivo).

Mantenha os padrões para todo o resto.
