---
external help file: Microsoft.Azure.Commands.Network.dll-Help.xml
Module Name: AzureRM.Network
online version: https://docs.microsoft.com/en-us/powershell/module/azurerm.network/remove-azurermvirtualwan
schema: 2.0.0
---

# Remove-AzureRmVirtualWan

## SYNOPSIS
Removes an Azure Virtual WAN and all associated P2SVpnServerConfigurations if any.

## SYNTAX

### ByVirtualWanName (Default)
```
Remove-AzureRmVirtualWan -ResourceGroupName <String> -Name <String> [-Force] [-PassThru]
 [-DefaultProfile <IAzureContextContainer>] [-WhatIf] [-Confirm] [<CommonParameters>]
```

### ByVirtualWanObject
```
Remove-AzureRmVirtualWan -InputObject <PSVirtualWan> [-Force] [-PassThru]
 [-DefaultProfile <IAzureContextContainer>] [-WhatIf] [-Confirm] [<CommonParameters>]
```

### ByVirtualWanResourceId
```
Remove-AzureRmVirtualWan -ResourceId <String> [-Force] [-PassThru] [-DefaultProfile <IAzureContextContainer>]
 [-WhatIf] [-Confirm] [<CommonParameters>]
```

## DESCRIPTION
Removes an Azure Virtual WAN and all associated P2SVpnServerConfigurations if any.

## EXAMPLES

### Example 1

```powershell
PS C:\> New-AzureRmResourceGroup -Name "TestResourceGroup" -Location "Central US"
PS C:\> $p2sVpnServerConfigCertFilePath = "PathToCertFile.cer"
PS C:\> $listOfCerts = New-Object "System.Collections.Generic.List[String]"
PS C:\> $listOfCerts.Add($p2sVpnServerConfigCertFilePath)
PS C:\> $p2sVpnServerConfigObject1 = New-AzureRmP2SVpnServerConfigurationObject -Name "p2sVpnServerConfiguration1Name" -VpnProtocol IkeV2 -VpnClientRootCertificateFilesList $listOfCerts -VpnClientRevokedCertificateFilesList $listOfCerts
PS C:\> New-AzureRmVirtualWan -Name "MyVirtualWan" -ResourceGroupName "TestResourceGroup" -Location "Central US" -P2SVpnServerConfiguration $p2sVpnServerConfigs
PS C:\> Remove-AzureRmVirtualWan -Name "MyVirtualWan" -ResourceGroupName "TestResourceGroup" -Passthru
```

This example creates a Virtual WAN in a resource group. Also creates a P2SVpnServerConfiguration and associates it with created Virtual WAN and then immediately deletes it. 
To suppress the prompt when deleting the Virtual WAN, use the -Force flag.

### Example 2

```powershell
PS C:\> New-AzureRmResourceGroup -Name "TestResourceGroup" -Location "Central US"
PS C:\> $virtualWan = New-AzureRmVirtualWan -Name "MyVirtualWan" -ResourceGroupName "TestResourceGroup" -Location "Central US"
PS C:\> Remove-AzureRmVirtualWan -InputObject $virtualWan -Passthru
```

This example creates a Virtual WAN in a resource group and then immediately deletes it. This deletion happens using the virtual wan object returned by New-AzureRmVirtualWan.
To suppress the prompt when deleting the Virtual WAN, use the -Force flag.

### Example 3

```powershell
PS C:\> New-AzureRmResourceGroup -Name "TestResourceGroup" -Location "Central US"
PS C:\> $virtualWan = New-AzureRmVirtualWan -Name "MyVirtualWan" -ResourceGroupName "TestResourceGroup" -Location "Central US"
PS C:\> Remove-AzureRmVirtualWan -ResourceId $virtualWan.Id -Passthru
```

This example creates a Virtual WAN in a resource group and then immediately deletes it. This deletion happens using the virtual wan resource id returned by New-AzureRmVirtualWan.
To suppress the prompt when deleting the Virtual WAN, use the -Force flag.

## PARAMETERS

### -DefaultProfile
The credentials, account, tenant, and subscription used for communication with Azure.

```yaml
Type: Microsoft.Azure.Commands.Common.Authentication.Abstractions.IAzureContextContainer
Parameter Sets: (All)
Aliases: AzureRmContext, AzureCredential

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -Force
Do not ask for confirmation.

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -InputObject
The virtual wan object to be deleted.

```yaml
Type: Microsoft.Azure.Commands.Network.Models.PSVirtualWan
Parameter Sets: ByVirtualWanObject
Aliases: VirtualWan

Required: True
Position: Named
Default value: None
Accept pipeline input: True (ByValue)
Accept wildcard characters: False
```

### -Name
The virtual wan name.

```yaml
Type: System.String
Parameter Sets: ByVirtualWanName
Aliases: ResourceName, VirtualWanName

Required: True
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -PassThru
Returns an object representing the item on which this operation is being performed.

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -ResourceGroupName
The resource group name.

```yaml
Type: System.String
Parameter Sets: ByVirtualWanName
Aliases:

Required: True
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -ResourceId
The Azure resource ID for the virtual wan to be deleted.

```yaml
Type: System.String
Parameter Sets: ByVirtualWanResourceId
Aliases: VirtualWanId

Required: True
Position: Named
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### -Confirm
Prompts you for confirmation before running the cmdlet.

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: (All)
Aliases: cf

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -WhatIf
Shows what would happen if the cmdlet runs.
The cmdlet is not run.

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: (All)
Aliases: wi

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### CommonParameters
This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable. For more information, see about_CommonParameters (http://go.microsoft.com/fwlink/?LinkID=113216).

## INPUTS

### Microsoft.Azure.Commands.Network.Models.PSVirtualWan

### System.String

## OUTPUTS

### System.Boolean

## NOTES

## RELATED LINKS