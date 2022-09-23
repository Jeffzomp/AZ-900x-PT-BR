---
wts:
  title: 01 – Criar uma máquina virtual no portal (10 min)
  module: Module 02 - Core Azure Services (Workloads)
---
# <a name="01---create-a-virtual-machine-in-the-portal-10-min"></a>01 – Criar uma máquina virtual no portal (10 min)

Neste passo a passo, criaremos uma máquina virtual no portal do Azure, conectaremos à máquina virtual, instalaremos a função de servidor web e testaremos. 

**Observação**: Reserve um tempo durante este passo a passo para selecionar e ler os ícones informativos. 

# <a name="task-1-create-the-virtual-machine"></a>Tarefa 1: Criar a máquina virtual 
1. Entre no portal do Azure: **https://portal.azure.com**

3. Na folha **Todos os serviços** no Menu do Portal, pesquise e selecione **Máquinas virtuais**, clique em **+Criar** e escolha **+Máquina virtual do Azure** no menu suspenso.

4. Na guia **Básico**, preencha as seguintes informações (mantenha os padrões para todo o resto):

    | Configurações | Valores |
    |  -- | -- |
    | Subscription | **Use a padrão fornecida** |
    | Resource group | **Criar grupo de recursos** |
    | Nome da máquina virtual | **myVM** |
    | Região | **(EUA) Leste dos EUA**|
    | Opções de disponibilidade | Nenhuma opção de redundância de infraestrutura exigida|
    | Image | **Datacenter do Windows Server 2019 – Gen2**|
    | Tamanho | **Standard D2s v3**|
    | Nome de usuário da conta de administrador | **azureuser** |
    | Senha da conta de administrador (digite com atenção!) | **Pa$$w0rd1234**|
    | Regras da porta de entrada - | **Permitir portas selecionadas **|
    | Selecione as portas de entrada | **RDP (3389)** e **HTTP (80)**| 

5. Passe para a guia Rede para verificar se **HTTP (80) e RDP (3389)** estão selecionadas na seção **Selecionar portas de entrada**.

6. Alterne para a guia Gerenciamento e, em sua seção **Monitoring**, selecione a seguinte configuração:

    | Configurações | Valores |
    | -- | -- |
    | Diagnóstico de inicialização | **Desabilitar**|

7. Mantenha os valores restantes padrão e selecione **Revisar + criar** na parte inferior da página.

8. Once Validation is passed click the <bpt id="p1">**</bpt>Create<ept id="p1">**</ept> button. It can take anywhere from five to seven minutes to deploy the virtual machine.

9. Você vai receber atualizações na página de implantação e por meio da área de **Notificações** (ícone de sino na barra de menu superior).

# <a name="task-2-connect-to-the-virtual-machine"></a>Tarefa 2: Conectar-se à máquina virtual

Nesta tarefa, vamos nos conectar à nova máquina virtual usando RDP (Protocolo de Área de Trabalho Remota). 

1. Clique no ícone de sino na barra de ferramentas superior azul e selecione “Ir para o recurso” quando a implantação for concluída. 

    **Observação**: você também pode usar o link **Ir para o recurso** na página de implantação 

2. Na folha **Visão geral** da máquina virtual, selecione o botão **Conectar** e escolha **RDP** na lista suspensa.

    ![Captura de tela das propriedades da máquina virtual com o botão Conectar destacado.](../images/0101.png)

    <bpt id="p1">**</bpt>Note<ept id="p1">**</ept>: The following directions tell you how to connect to your VM from a Windows computer. On a Mac, you need an RDP client such as this Remote Desktop Client from the Mac App Store and on a Linux computer you can use an open source RDP client.

2. On the <bpt id="p1">**</bpt>Connect to virtual machine<ept id="p1">**</ept> page, keep the default options to connect with the public IP address over port 3389 and click <bpt id="p2">**</bpt>Download RDP File<ept id="p2">**</ept>. A file will download on the bottom left of your screen.

3. **Abra** o arquivo RDP baixado (no canto inferior esquerdo da máquina do laboratório) e selecione **Conectar** quando solicitado. 

    ![Captura de tela das propriedades da máquina virtual com o botão Conectar destacado. ](../images/0102.png)

4. Na janela **Segurança do Windows**, entre usando as Credenciais de Administrador usadas ao criar a VM **azureuser** e a senha **Pa$$w0rd1234**. 

5. You may receive a warning certificate during the sign-in process. Click <bpt id="p1">**</bpt>Yes<ept id="p1">**</ept> or to create the connection and connect to your deployed VM. You should connect successfully.

    ![Captura de tela do diálogo de aviso de Certificado informando ao usuário sobre um certificado não confiável, com o botão Sim destacado. ](../images/0104.png)

A new Virtual Machine (myVM) will launch inside your Lab. Close the Server Manager and dashboard windows that pop up (click "x" at top right). You should see the blue background of your virtual machine. <bpt id="p1">**</bpt>Congratulations!<ept id="p1">**</ept> You have deployed and connected to a Virtual Machine running Windows Server. 

# <a name="task-3-install-the-web-server-role-and-test"></a>Tarefa 3: Instalar a função de servidor Web e testar

Nesta tarefa, instale a função de Servidor Web no servidor da máquina virtual recém-criada e verifique se a página de boas-vindas padrão do IIS é exibida. 

1. Na máquina virtual que foi aberta, inicie o PowerShell: pesquise **PowerShell** na barra de pesquisa, clique com o botão direito em **Windows PowerShell** e selecione **Executar como administrador**.

    ![Captura de tela da área de trabalho da máquina virtual com o botão Iniciar clicado e o PowerShell selecionado com Executar como administrador destacado.](../images/0105.png)

2. In PowerShell, install the <bpt id="p1">**</bpt>Web-Server<ept id="p1">**</ept> feature on the virtual machine by running the following command. (Paste in the command and hit ENTER for the installment to begin).

    ```PowerShell
    Install-WindowsFeature -name Web-Server -IncludeManagementTools
    ```
  
3. When completed, a prompt will state <bpt id="p1">**</bpt>Success<ept id="p1">**</ept> with a value <bpt id="p2">**</bpt>True<ept id="p2">**</ept>. You do not need to restart the virtual machine to complete the installation. Close the RDP connection to the VM by clicking the <bpt id="p1">**</bpt>x<ept id="p1">**</ept> on the blue bar at the top center of your virtual machine. You can also minimize it by clicking the <bpt id="p1">**</bpt><ph id="ph1">-</ph><ept id="p1">**</ept> on the blue bar at the top center.

    ![Captura de tela do prompt de comando do Windows PowerShell com o comando Install-WindowsFeature -name Web-Server -IncludeManagementTools concluído com êxito e saída informando que foi bem-sucedido.](../images/0106.png)

4. De volta ao portal, navegue até a folha **Visão geral** da myVM e use o botão **Clique para área de transferência** para copiar o endereço IP público da myVM. Abra uma nova guia do navegador, cole o endereço IP público na caixa de texto URL e pressione a tecla **Enter** para navegar até ele.

    ![Captura de tela do painel de propriedades da máquina virtual do portal do Azure com o endereço IP copiado.](../images/0107.png)

5. A página de boas-vindas padrão do Servidor Web do IIS será aberta.

    ![Captura de tela da página de boas-vindas do servidor Web do IIS padrão sendo acessada por meio do endereço IP público em um navegador Web.](../images/0108.png)

<bpt id="p1">**</bpt>Congratulations!<ept id="p1">**</ept> You have created a new VM running a web server that is accessible via its public IP address. If you had a web application to host, you could deploy application files to the virtual machine and host them for public access on the deployed virtual machine.


<bpt id="p1">**</bpt>Note<ept id="p1">**</ept>: To avoid additional costs, you can optionally remove this resource group. Search for resource groups, click your resource group, and then click <bpt id="p1">**</bpt>Delete resource group<ept id="p1">**</ept>. Verify the name of the resource group and then click <bpt id="p1">**</bpt>Delete<ept id="p1">**</ept>. Monitor the <bpt id="p1">**</bpt>Notifications<ept id="p1">**</ept> to see verify that the deletion completed successfully. 
