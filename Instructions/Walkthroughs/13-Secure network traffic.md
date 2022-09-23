---
wts:
  title: 13 – Tráfego de rede seguro (10 min)
  module: 'Module 04: Describe general security and network security features'
---
# <a name="13---secure-network-traffic-10-min"></a>13 – Tráfego de rede seguro (10 min)

Neste passo a passo, configuraremos um grupo de segurança de rede.

# <a name="task-1-create-a-virtual-machine"></a>Tarefa 1: Criar uma máquina virtual

Nesta tarefa, criaremos uma máquina virtual Windows Server 2019 Datacenter. 

1. Entre no [portal do Azure](https://portal.azure.com).

2. Na folha **Todos os serviços**, procure e selecione **Máquinas virtuais** e, em seguida, selecione **+ Adicionar, + Criar, + Nova** Máquina Virtual.

3. Na guia **Básico**, preencha as seguintes informações (mantenha os padrões para todo o resto):

    | Configurações | Valores |
    |  -- | -- |
    | Subscription | **Use o padrão fornecido** |
    | Resource group | **Criar grupo de recursos** |
    | Nome da máquina virtual | **SimpleWinVM** |
    | Região | **(EUA) Leste dos EUA**|
    | Image | **Windows Server 2019 Datacenter Gen 2**|
    | Tamanho | **Standard D2s v3**|
    | Nome de usuário da conta de administrador | **azureuser** |
    | Senha da conta de administrador | **Pa$$w0rd1234**|
    | Regras de porta de entrada | **Nenhuma**|

4. Alterne para a guia **Rede** e defina as seguintes configurações:

    | Configurações | Valores |
    | -- | -- |
    | Grupo de segurança de rede da NIC | **Nenhuma**|

5. Passe para a guia **Gerenciamento** e, na seção **Monitoramento**, selecione a seguinte configuração:

    | Configurações | Valores |
    | -- | -- |
    | Diagnóstico de inicialização | **Desabilitar**|

6. Mantenha os padrões restantes e clique no botão **Revisar + criar** na parte inferior da página.

7. Once Validation is passed click the <bpt id="p1">**</bpt>Create<ept id="p1">**</ept> button. It can take about five minutes to deploy the virtual machine.

8. Monitor the deployment. It may take a few minutes for the resource group and virtual machine to be created. 

9. Na folha de implantação ou na área de Notificação, clique em **Ir para o recurso**. 

10. Na folha da máquina virtual **SimpleWinVM**, clique em **Rede**, revise a guia **Regras de porta de entrada+** e observe que não há grupo de segurança de rede associado ao adaptador de rede da máquina virtual ou sub-rede à qual o adaptador de rede está conectado.

    <bpt id="p1">**</bpt>Note<ept id="p1">**</ept>: Identify the name of the network interface. You will need it in the next task.

# <a name="task-2-create-a-network-security-group"></a>Tarefa 2: Criar um 	Grupo de Segurança de Rede

Nesta tarefa, criaremos um grupo de segurança de rede e o associaremos ao adaptador de rede. 

1. Na folha **Todos os serviços**, procure e selecione **Grupos de segurança de rede** e, em seguida, selecione **+ Adicionar, + Criar, + Novo**

2. Na guia **Básico** da folha **Criar grupo de segurança de rede**, especifique as seguintes configurações.

    | Configuração | Valor |
    | -- | -- |
    | Subscription | **Use a assinatura padrão** |
    | Resource group | **Selecionar o padrão na lista suspensa** |
    | Nome | **myNSGSecure** |
    | Região | **(EUA) Leste dos EUA**  |

3. Clique em **Revisar + criar** e, em seguida, clique em **Criar** após a validação.

4. Depois que o NSG for criado, clique em **Ir para o recurso**.

5. Em **Configurações**, clique em **Adaptadores de rede** e em ** Associar**.

6. Selecione o adaptador de rede que você identificou na tarefa anterior. 

# <a name="task-3-configure-an-inbound-security-port-rule-to-allow-rdp"></a>Tarefa 3: Configurar uma regra de porta de segurança de entrada para permitir o RDP

Nesta tarefa, vamos permitir o tráfego do RDP para a máquina virtual configurando uma regra de porta de segurança de entrada. 

1. No portal do Azure, navegue até a folha da máquina virtual **SimpleWinVM**. 

2. No painel **Visão geral**, clique em **Conectar**.

3. Attempt to connect to the virtual machine by selecting RDP and downloading an running the RDP file. By default the network security group does not allow RDP. Close the error window. 


    ![Captura de tela da mensagem de erro informando que a conexão com a máquina virtual falhou.](../images/1201.png)

4. Na folha da máquina virtual, role para baixo até a seção **Configurações**. Selecione **Rede** e observe as regras de entrada para o grupo de segurança de rede **myNSGSecure (conectado ao adaptador de rede: myVMNic)** . Ele nega todo tráfego de entrada, exceto o tráfego dentro da rede virtual e as investigações do balanceador de carga.

5. On the <bpt id="p1">**</bpt>Inbound port rules<ept id="p1">**</ept> tab, click <bpt id="p2">**</bpt>Add inbound port rule<ept id="p2">**</ept> . Click <bpt id="p1">**</bpt>Add<ept id="p1">**</ept> when you are done. 

    | Configuração | Valor |
    | -- | -- |
    | Fonte | **Qualquer**|
    | Intervalos de portas de origem | **\*** |
    | Destino | **Qualquer** |
    | Intervalos de portas de destino | **3389** |
    | Protocolo | **TCP** |
    | Ação | **Permitir** |
    | Prioridade | **300** |
    | Nome | **AllowRDP** |

6. Select <bpt id="p1">**</bpt>Add<ept id="p1">**</ept> and wait for the rule to be provisioned and then try again to RDP into the virtual machine by going back to <bpt id="p2">**</bpt>Connect<ept id="p2">**</ept> This time you should be successful. Remember the user is <bpt id="p1">**</bpt>azureuser<ept id="p1">**</ept> and the password is <bpt id="p2">**</bpt>Pa$$w0rd1234<ept id="p2">**</ept>.

# <a name="task-4-configure-an-outbound-security-port-rule-to-deny-internet-access"></a>Tarefa 4: Configurar uma regra de porta de segurança de saída para negar o acesso à Internet

Nesta tarefa, criaremos uma regra de porta de saída do NSG que negará o acesso à Internet e, em seguida, testaremos para garantir que a regra está funcionando.

1. Continue na sua sessão do RDP da máquina virtual. 

2. Depois que a máquina iniciar, abra um navegador **Internet Explorer**. 

3. Verify that you can access <bpt id="p1">**</bpt><ph id="ph1">https://www.bing.com</ph><ept id="p1">**</ept> and then close Internet Explorer. You will need to work through the IE enhanced security pop-ups. 

    **Observação**: Agora vamos configurar uma regra para negar o acesso de saída à Internet. 

4. De volta ao portal do Azure, retorne à folha da máquina virtual **SimpleWinVM**. 

5. Em **Configurações**, clique em **Rede** e em **Regras de porta de saída**.

6. Notice there is a rule, <bpt id="p1">**</bpt>AllowInternetOutbound<ept id="p1">**</ept>. This a default rule and cannot be removed. 

7. Click <bpt id="p1">**</bpt>Add outbound port rule<ept id="p1">**</ept> to the right of the <bpt id="p2">**</bpt>myNSGSecure  (attached to network interface: myVMNic)<ept id="p2">**</ept> network security group and configure a new outbound security rule with a higher priority that will deny internet traffic. Click <bpt id="p1">**</bpt>Add<ept id="p1">**</ept> when you are finished. 

    | Configuração | Valor |
    | -- | -- |
    | Fonte | **Qualquer**|
    | Intervalos de portas de origem | **\*** |
    | Destino | **Marca de serviço** |
    | Marca de serviço de destino | **Internet** |
    | Intervalos de portas de destino | **\*** |
    | Protocolo | **TCP** |
    | Ação | **Deny** |
    | Prioridade | **4000** |
    | Nome | **DenyInternet** |

8. Selecione **Adicionar** Devolva os RDPs à VM. 

9. Browse to <bpt id="p1">**</bpt><ph id="ph1">https://www.microsoft.com</ph><ept id="p1">**</ept>. The page should not display. You may need to work through additional IE enhanced security pop-ups.  

<bpt id="p1">**</bpt>Note<ept id="p1">**</ept>: To avoid additional costs, you can optionally remove this resource group. Search for resource groups, click your resource group, and then click <bpt id="p1">**</bpt>Delete resource group<ept id="p1">**</ept>. Verify the name of the resource group and then click <bpt id="p1">**</bpt>Delete<ept id="p1">**</ept>. Monitor the <bpt id="p1">**</bpt>Notifications<ept id="p1">**</ept> to see how the delete is proceeding.
