---
title: COM+ ve ServiceModel İşlemlerini Karşılaştırma
ms.date: 03/30/2017
ms.assetid: e493bcdd-b91a-4486-853f-83dbcd1931b7
ms.openlocfilehash: 30ecbd374e909141dbc944740f90c1b41ac44ed2
ms.sourcegitcommit: bc293b14af795e0e999e3304dd40c0222cf2ffe4
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/26/2020
ms.locfileid: "96264914"
---
# <a name="comparing-transactions-in-com-and-servicemodel"></a>COM+ ve ServiceModel İşlemlerini Karşılaştırma

Bu konuda, bir işlem COM+ hizmeti davranışının, ad alanının sağladığı Windows Communication Foundation (WCF) özniteliklerini kullanarak nasıl benzetiminin ele alınmaktadır <xref:System.ServiceModel> .  
  
## <a name="emulating-com-using-servicemodel-attributes"></a>ServiceModel özniteliklerini kullanarak COM+ öykünmesi  

 Aşağıdaki tablo, <xref:System.EnterpriseServices.TransactionOption> bir işlem oluşturmak için kullanılan numaralandırmayı `EnterpriseServices` ve ad ALANıNıN sağladığı WCF öznitelikleriyle nasıl ilişkilendiritireceğini karşılaştırır <xref:System.ServiceModel> .  
  
|COM+ özniteliği|WCF öznitelikleri|  
|---------------------|------------------------------------------------------------------------|  
|RequiresNew|<xref:System.ServiceModel.TransactionFlowAttribute> , olarak ayarlanır <xref:System.ServiceModel.TransactionFlowOption.NotAllowed> .<br /><br /> <xref:System.ServiceModel.OperationBehaviorAttribute.TransactionScopeRequired%2A>, `true` değeridir.<br /><br /> `TransactionFlow`Binding öğesindeki özniteliği `false` .|  
|Gerekli|<xref:System.ServiceModel.TransactionFlowAttribute> , olarak ayarlanır <xref:System.ServiceModel.TransactionFlowOption.Allowed> .<br /><br /> <xref:System.ServiceModel.OperationBehaviorAttribute.TransactionScopeRequired%2A>, `true` değeridir.<br /><br /> `TransactionFlow`Binding öğesindeki özniteliği `true` .|  
|Desteklenir|Doğrudan eşdeğer olmaz. Genel olarak, bunun yerine için belirtilen davranışı benimsemelisiniz `Required` .|  
|NotSupported|<xref:System.ServiceModel.OperationBehaviorAttribute.TransactionScopeRequired%2A>, `false` değeridir.<br /><br /> `TransactionFlow`Binding öğesindeki özniteliği `false` .|  
|Devre dışı|Doğrudan eşdeğer olmaz. Genel olarak, bunun yerine için belirtilen davranışı benimsemelisiniz `NotSupported` .|
