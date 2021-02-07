---
description: 'Daha fazla bilgi edinin: COM+ ve ServiceModel Işlemlerini karşılaştırma'
title: COM+ ve ServiceModel İşlemlerini Karşılaştırma
ms.date: 03/30/2017
ms.assetid: e493bcdd-b91a-4486-853f-83dbcd1931b7
ms.openlocfilehash: 9b4e8e0940297e887ec9a3085ebe521afe4d000d
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99743427"
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
