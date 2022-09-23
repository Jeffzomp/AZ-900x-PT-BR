---
wts:
  title: 12 – Implantar o Azure Key Vault (5 min)
  module: 'Module 04: Describe general security and network security features'
---
# <a name="12---implement-azure-key-vault-5-min"></a>12 – Implantar o Azure Key Vault (5 min)

Neste passo a passo, criaremos um Azure Key Vault e, em seguida, criaremos um segredo de senha dentro desse cofre de chaves, fornecendo uma senha armazenada com segurança e gerenciada centralmente para uso com aplicativos.

# <a name="task-1-create-an-azure-key-vault"></a>Tarefa 1: Criar um Azure Key Vault 

1. Entre no [portal do Azure](https://portal.azure.com).

2. Na folha **Todos os serviços**, procure e selecione **Cofres de chaves** e selecione **+Adicionar +Novo +Criar **.

3. Configure the key vault (replace <bpt id="p1">**</bpt>xxxx<ept id="p1">**</ept> in the name of the key vault with letters and digits such that the name is globally unique). Leave the defaults for everything else.

    | Configuração | Valor | 
    | --- | --- |
    | Subscription | **Use a padrão fornecida** |
    | Resource group | **Criar grupo de recursos** |
    | Nome do cofre de chaves | **keyvaulttestxxx** |
    | Location | **Leste dos EUA** |
    | Tipo de preço | **Standard** |
    
    **Observação** substitua **xxxx** para ter um nome exclusivo.
4. Clique em **Revisar + criar** e, em seguida, clique em **Criar**. 

5. Once the new key vault is provisioned, click <bpt id="p1">**</bpt>Go to resource<ept id="p1">**</ept>. Or you can locate your new key vault by searching for it. 

6. Click on the key vault <bpt id="p1">**</bpt>Overview<ept id="p1">**</ept> tab and take note of the <bpt id="p2">**</bpt>Vault URI<ept id="p2">**</ept>. Applications that use your vault through the REST APIs will need this URI.

7. Take a moment to browse through some of the other key vault options. Under <bpt id="p1">**</bpt>Settings<ept id="p1">**</ept> review <bpt id="p2">**</bpt>Keys<ept id="p2">**</ept>, <bpt id="p3">**</bpt>Secrets<ept id="p3">**</ept>, <bpt id="p4">**</bpt>Certificates<ept id="p4">**</ept>, <bpt id="p5">**</bpt>Access Policies<ept id="p5">**</ept>, <bpt id="p6">**</bpt>Firewalls and virtual networks<ept id="p6">**</ept>.

    <bpt id="p1">**</bpt>Note<ept id="p1">**</ept>: Your Azure account is the only one authorized to perform operations on this new vault. You can modify this if you wish in the <bpt id="p1">**</bpt>Settings<ept id="p1">**</ept> and then the <bpt id="p2">**</bpt>Access policies<ept id="p2">**</ept> section.

# <a name="task-2-add-a-secret-to-the-key-vault"></a>Tarefa 2: Adicionar um segredo ao cofre de chaves
        
Nesta tarefa, adicionaremos uma senha ao cofre de chaves. 

1. Em **Configurações**, clique em **Segredos** e, em seguida, clique em **+ Gerar/Importar**.

2. Configure the secret. Leave the other values at their defaults. Notice you can set an activation and expiration date. Notice you can also disable the secret.

    | Configuração | Valor | 
    | --- | --- |
    | Opções de upload | **Manual** |
    | Nome | **ExamplePassword** |
    | Valor | **hVFkk96** |

3. Clique em **Criar**.

4. Assim que o segredo tiver sido criado com sucesso, clique em **ExamplePassword** e observe que ele tem o status **Habilitado**

5. Select the secret you just created, note the the <bpt id="p1">**</bpt>Secret Identifier<ept id="p1">**</ept>. This is the url value that you can now use with applications. It provides a centrally managed and securely stored password. 

6. Clique no botão **Mostrar valor secreto** para exibir a senha que você especificou anteriormente.


Configure o cofre de chaves (substitua **xxxx** no nome do cofre de chaves por letras e dígitos de forma que o nome seja globalmente exclusivo).

Mantenha os padrões para todo o resto.
