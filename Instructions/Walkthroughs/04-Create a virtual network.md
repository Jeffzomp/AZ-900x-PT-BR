---
wts:
  title: 04 – Criar uma rede virtual (20 min)
  module: Module 02 - Core Azure Services (Workloads)
---
# <a name="04---create-a-virtual-network-20-min"></a>04 – Criar uma rede virtual (20 min)

Neste passo a passo, vamos criar uma rede virtual, implantar duas máquinas virtuais nessa rede e configurá-las para permitir que uma máquina virtual execute ping na outra dentro dessa rede virtual.

# <a name="task-1-create-a-virtual-network"></a>Tarefa 1: criar uma rede virtual 

Nesta tarefa, você criará uma rede virtual. 

Observação: antes de iniciar o laboratório, desabilite o firewall público e privado em sua máquina virtual abrindo a Rede menu Iniciar > Configurações > e a Internet > Localize Windows Firewall

1. Entre no portal do Microsoft Azure em <a href="https://portal.azure.com" target="_blank"><span style="color: #0066cc;" color="#0066cc">https://portal.azure.com</span></a>

2. Na folha **Todos os serviços**, procure e selecione **Máquinas virtuais** e, em seguida, selecione **+ Adicionar, + Criar, + Novo**. 

3. Na guia **Básico**, preencha as seguintes informações (mantenha os padrões para todo o resto):

    | Configuração | Valor | 
    | --- | --- |
    | Subscription | **Manter a padrão fornecida** |
    | Grupo de recursos | **Criar grupo de recursos** |
    | Nome | **vnet1** |
    | Região | **(EUA) Leste dos EUA** |
    
   
4. Click the <bpt id="p1">**</bpt>Review + create<ept id="p1">**</ept> button. Ensure the validation passes. Then hit create to deploy the resource.


# <a name="task-2-create-two-virtual-machines"></a>Tarefa 2: Criar duas máquinas virtuais

Nesta tarefa, criaremos duas máquinas virtuais na rede virtual. 

1. Na folha **Todos os serviços**, procure **Máquinas virtuais**, selecione **+ Adicionar, + Criar, + Novo** e, na lista suspensa, escolha **Máquina Virtual**. 

2. Na guia **Básico**, preencha as seguintes informações (mantenha os padrões para todo o resto):

   | Configuração | Valor | 
   | --- | --- |
   | Subscription | **Use a padrão fornecida** |
   | Resource group |  **Selecionar o padrão na lista suspensa** |
   | Nome da máquina virtual | **vm1**|
   | Região | **(EUA) Leste dos EUA** |
   | Image | **Windows Server 2019 Datacenter – Gen2** |
   | Nome de Usuário| **azureuser** |
   | Senha| **Pa$$w0rd1234** |
   | Porta de entrada públicas| Selecione **Permitir portas selecionadas**  |
   | Portas de entrada selecionadas| **RDP (3389)** |
   

3. Select the <bpt id="p1">**</bpt>Networking<ept id="p1">**</ept> tab. Make sure the virtual machine is placed in the <bpt id="p2">**</bpt>vnet1<ept id="p2">**</ept> virtual network. Review the default settings, but do not make any other changes. 

4. Click <bpt id="p1">**</bpt>Review + create<ept id="p1">**</ept>. After the Validation passes, click <bpt id="p1">**</bpt>Create<ept id="p1">**</ept>. Deployment times can vary but it can generally take between three to six minutes to deploy.

5. Monitore sua implantação, mas continue na próxima etapa. 

6. Create a second virtual machine by repeating steps <bpt id="p1">**</bpt>2 to 4<ept id="p1">**</ept> above. Make sure you use a different virtual machine name, that the virtual machine is in the same virtual network, and is using a new public IP address:

    | Configuração | Valor |
    | --- | --- |
    | Resource group | **selecione o padrão no menu suspenso (o mesmo que Tarefa1-3 e Tarefa2-2)** |
    | Nome da máquina virtual |  **vm2** |
    | Rede virtual | **vnet1** |
    | IP público | **vm2-ip** |

7. Espere as duas máquinas virtuais serem implantadas e o status mudar para *em execução*.

# <a name="task-3-test-the-connection"></a>Tarefa 3: Testar a conexão 

In this task, we will try to test whether the virtual machines can communicate (ping) each other. If not we will install a rule to allow an ICMP connection. Usually ICMP connections are automatically blocked.

1. From the <bpt id="p1">**</bpt>All resources<ept id="p1">**</ept> blade, search for <bpt id="p2">**</bpt>vm1<ept id="p2">**</ept>, open its <bpt id="p3">**</bpt>Overview<ept id="p3">**</ept> blade, and make sure its <bpt id="p4">**</bpt>Status<ept id="p4">**</ept> is <bpt id="p5">**</bpt>Running<ept id="p5">**</ept>. You may need to <bpt id="p1">**</bpt>Refresh<ept id="p1">**</ept> the page.

2. Na folha **Visão geral**, selecione **Conectar** e depois **RDP** na lista suspensa.

    **Observação**: As instruções a seguir mostram como se conectar à VM a partir de um computador Windows. 

3. Na folha **Conectar ao RDP**, mantenha as opções padrão para se conectar ao endereço IP na porta 3389 e selecione **Baixar Arquivo RDP**.

4. Abra o arquivo RDP baixado (no canto inferior esquerdo da VM) e selecione **Conectar** quando solicitado. 

5. Na janela **Segurança do Windows**, digite o nome de usuário **azureuser** e a senha **Pa$$w0rd1234** e clique em **OK**.

6. You may receive a certificate warning during the sign-in process. Click <bpt id="p1">**</bpt>Yes<ept id="p1">**</ept> to create the connection and connect to your deployed VM. You should connect successfully. Close the Windows Server and Dashboard windows that pop up. You should see a Blue Windows background. You are now in your virtual machine.

7. Em **ambas** as máquinas virtuais recém-criadas, conecte-se por meio de RDP e desabilite o firewall público e privado abrindo o menu Iniciar > Configurações > Rede e Internet > Localizar Windows Firewall.

8. Abra o PowerShell na máquina virtual selecionando o botão **Iniciar**. Em Pesquisar, insira **PowerShell** e clique com o botão direito em **Windows PowerShell** para **Executar como administrador**

9. No PowerShell, tente executar ping na vm2 inserindo:

   ```PowerShell
   ping vm2
   ```

 10. You should be successful. You have pinged VM2 from VM1.


<bpt id="p1">**</bpt>Congratulations!<ept id="p1">**</ept> You have configured and deployed two virtual machines in a virtual network, and then you were able to connect them.

<bpt id="p1">**</bpt>Note<ept id="p1">**</ept>: To avoid additional costs, you can optionally remove this resource group. Search for resource groups, click your resource group, and then click <bpt id="p1">**</bpt>Delete resource group<ept id="p1">**</ept>. Verify the name of the resource group and then click <bpt id="p1">**</bpt>Delete<ept id="p1">**</ept>. Monitor the <bpt id="p1">**</bpt>Notifications<ept id="p1">**</ept> to see how the delete is proceeding.
