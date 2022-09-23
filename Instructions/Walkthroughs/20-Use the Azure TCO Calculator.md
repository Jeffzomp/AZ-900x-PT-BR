---
wts:
  title: 20 – Usar o Azure TCO Calculator (10 min)
  module: 'Module 06: Describe Azure cost management and service level agreements'
---
# <a name="20---use-the-azure-tco-calculator-10-min"></a>20 – Usar o Azure TCO Calculator (10 min)


Neste passo a passo, você usará a calculadora do custo total de propriedade (TCO) para gerar um relatório de comparação de custos para um ambiente local.

<bpt id="p1">**</bpt>Note<ept id="p1">**</ept>: This walkthrough provides example definitions of on-premises infrastructure and workloads for a typical datacenter. To create a TCO Calculator report, use the example definitions or provide details of your <bpt id="p1">*</bpt>actual<ept id="p1">*</ept> on-premises infrastructure and workloads.

# <a name="task-1-configure-the-tco-calculator"></a>Tarefa 1: Configurar a calculadora de TCO

Nesta tarefa, adicionaremos informações de infraestrutura à calculadora. 

1. Em um navegador, navegue até a página [Calculadora do custo total de propriedade (TCO)](https://azure.microsoft.com/en-us/pricing/tco/calculator/).

2. Para adicionar detalhes de sua infraestrutura de servidor local, clique em **+ Adicionar carga de trabalho do servidor** no painel **Definir suas cargas de trabalho**.

    | Configurações | Valor |
    | -- | -- |
    | Nome | **Servidores: VMs do Windows** |
    | Carga de trabalho | **Servidor Windows/Linux** |
    | Ambiente | **Máquinas virtuais** |
    | Sistema operacional | **Windows** |  
    | VMs | **50** |
    | Virtualização | **Hyper-V** |
    | Núcleo(s) | **8**|
    | RAM (GB) | **16** |
    | Otimizar por | **CPU** |
    | Windows Server 2008/2008 R2 | **Desativado** |

3. Selecione **+ Adicionar carga de trabalho do servidor** para criar uma linha para uma nova definição de carga de trabalho do servidor. 

    | Configurações | Valor |
    | -- | -- |
    | Nome | **Servidores: VMs Linux** |
    | Carga de trabalho | **Servidor Windows/Linux** |
    | Ambiente | **Máquinas virtuais** |
    | Sistema operacional | **Linux** |  
    | VMs | **50** |
    | Virtualização | **VMware** |
    | Núcleo(s) | **8**|
    | RAM (GB) | **16** |
    | Otimizar por | **CPU** |
    | Windows Server 2008/2008 R2 | **Desativado** |

4. No painel **Armazenamento**, clique em **Adicionar armazenamento**.

    | Configurações | Valor |
    | -- | -- |
    | Nome | **Armazenamento do Servidor** |
    | Tipo de armazenamento | **Disco Local/SAN** |
    | Tipo de disco | **HDD** |
    | Capacity | **60 TB** |  
    | Backup | **120 TB** |
    | Archive | **0 TB** |

5. No painel **Rede**, adicione largura de banda. 

    | Configurações | Valor |
    | -- | -- |
    | Largura de banda de saída | 15 TB|

6. Clique em **Próximo**.

7. Explore as opções e faça os ajustes necessários. 

    | Configurações | Valor |
    | -- | -- |
    | Moeda | **Euro** |

8. Clique em **Próximo**.

# <a name="task-2-review-the-results-and-save-a-copy"></a>Tarefa 2: Revisar os resultados e salvar uma cópia

Nesta tarefa, revisaremos as recomendações de redução de custos e faremos o download de um relatório. 

1. Revise as recomendações e visualizações de economia de custos do Azure.

    | Configurações | Valor |
    | -- | -- |
    | Período de tempo| **3 anos** |
    | Região | **Norte da Europa** |

2. Para modificar as informações fornecidas, vá até o final da página e clique em **Voltar**. 

3. Para salvar ou imprimir uma cópia em PDF do relatório, clique em **Baixar**.

    ![Screenshot of the report pane of the tco calculator in Azure. The highlighted and completed input fields indicates how set the tco calculator timeframe to three years and the region to north europe. A graph shows the cost of on-premises infrastructure and workloads off-set against the reduced cost of using Azure.](../images/2001.png)

Congratulations! You have used the TCO Calculator to generate a cost comparison report for an on-premises environment.
