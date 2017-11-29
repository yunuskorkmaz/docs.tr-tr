---
title: "COM+ ve ServiceModel İşlemlerini Karşılaştırma"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: e493bcdd-b91a-4486-853f-83dbcd1931b7
caps.latest.revision: "5"
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: 712f8a7a153d7255275ff7ebaa647d5a624f8ae9
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/18/2017
---
# <a name="comparing-transactions-in-com-and-servicemodel"></a>COM+ ve ServiceModel İşlemlerini Karşılaştırma
Bu konuda işlem COM + kullanarak hizmet davranışına benzetmek nasıl ele alınmıştır [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] öznitelikleri <xref:System.ServiceModel> ad alanı sağlar.  
  
## <a name="emulating-com-using-servicemodel-attributes"></a>COM + ServiceModel öznitelikleri kullanarak öykünmesini yapma  
 Aşağıdaki tabloda karşılaştırır <xref:System.EnterpriseServices.TransactionOption> numaralandırması oluşturmak için kullanılan bir `EnterpriseServices` işlem ve nasıl bunlar için bağıntısını [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] öznitelikleri <xref:System.ServiceModel> ad alanı sağlar.  
  
|COM + özniteliği|[!INCLUDE[indigo2](../../../../includes/indigo2-md.md)]öznitelikleri|  
|---------------------|------------------------------------------------------------------------|  
|RequiresNew|<xref:System.ServiceModel.TransactionFlowAttribute>ayarlanmış <xref:System.ServiceModel.TransactionFlowOption.NotAllowed>.<br /><br /> <xref:System.ServiceModel.OperationBehaviorAttribute.TransactionScopeRequired%2A>olan `true`.<br /><br /> `TransactionFlow` Bağlama öğesi içinde özniteliktir `false`.|  
|Gerekli|<xref:System.ServiceModel.TransactionFlowAttribute>ayarlanmış <xref:System.ServiceModel.TransactionFlowOption.Allowed>.<br /><br /> <xref:System.ServiceModel.OperationBehaviorAttribute.TransactionScopeRequired%2A>olan `true`.<br /><br /> `TransactionFlow` Bağlama öğesi içinde özniteliktir `true`.|  
|Desteklenir|Doğrudan bir eşdeğeri yoktur. İçin belirtilen davranışı genel olarak, benimsemeyi `Required` yerine.|  
|NotSupported|<xref:System.ServiceModel.OperationBehaviorAttribute.TransactionScopeRequired%2A>olan `false`.<br /><br /> `TransactionFlow` Bağlama öğesi içinde özniteliktir `false`.|  
|Devre dışı|Doğrudan bir eşdeğeri yoktur. İçin belirtilen davranışı genel olarak, benimsemeyi `NotSupported` yerine.|
