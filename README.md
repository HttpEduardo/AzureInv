# Obtenha um inventário do seu ambiente Azure

O script exporta seu inventário do Azure como arquivos CSV. Ele cria diferentes arquivos CSV para cada assinatura com recursos.

Isso é mais útil se você alterar seu modelo de contrato. Por exemplo, de EA ou Pay-As-You-Go para um contrato CSP. Alguns dos recursos do mercado ainda não estão disponíveis no CSP. Você pode enviar esses arquivos ao seu provedor CSP para fornecer uma visão geral sobre seu ambiente do Azure.

# Pré-requisitos

1. PowerShell >= 5.1 ou PowerShell Core 6.x
2. Módulo Azure PowerShell Az \
    Você pode baixar este módulo em: https://github.com/Azure/azure-powershell/releases/latest \
    ou instale-o diretamente com `Install-Module -Name Az`
3. Pelo menos direitos de "leitor" nas assinaturas desejadas

# Uso

1. Baixe ou clone este repositório
2. Abra um PowerShell (não elevado é bom)
3. (opcional) Conecte-se ao seu ambiente Azure executando `Connect-AzAccount`
4. Execute `.\Get-AzureInventory.ps1`. Se você não estiver conectado agora, ele irá conectá-lo agora.
5. Como resultado, você obterá diferentes arquivos CSV:
    - "subscriptions.csv" com informações sobre todas as assinaturas verificadas.
    - "inventory_<subscription_id>.csv" com todas as informações do recurso (nome, grupo de recursos, tipo, SKU)
    - "marketplace_<subscription_id>.csv" com todos os recursos do marketplace

# Parâmetros
|Parâmetro|Padrão|Valor Possível|
|--|--|--|
| `-SubscriptionId` | vazio | Um ID de assinatura de seu ambiente. O script carregará apenas recursos desta assinatura.|
| `-Verbose` | | Defina este parâmetro para obter mais informações durante a execução do script |
