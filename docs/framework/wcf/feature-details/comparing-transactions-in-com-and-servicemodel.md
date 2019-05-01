---
title: COM+ ve ServiceModel İşlemlerini Karşılaştırma
ms.date: 03/30/2017
ms.assetid: e493bcdd-b91a-4486-853f-83dbcd1931b7
ms.openlocfilehash: 4a47fe1686dff2e705b06b001d7d5e4ea6e8c5f2
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/23/2019
ms.locfileid: "61857876"
---
# <a name="comparing-transactions-in-com-and-servicemodel"></a>COM+ ve ServiceModel İşlemlerini Karşılaştırma
Bu konu, Windows Communication Foundation (WCF) öznitelikleri kullanarak işlemsel bir COM + hizmet davranışını benzetmekte anlatılmaktadır <xref:System.ServiceModel> ad alanı sağlar.  
  
## <a name="emulating-com-using-servicemodel-attributes"></a>COM + ServiceModel öznitelikleri kullanarak öykünmesini yapma  
 Aşağıdaki tabloda karşılaştırır <xref:System.EnterpriseServices.TransactionOption> sabit listesi oluşturmak için kullanılan bir `EnterpriseServices` işlem ve bunların nasıl WCF öznitelikleri ilişkilendirmek <xref:System.ServiceModel> ad alanı sağlar.  
  
|COM + özniteliği|WCF öznitelikleri|  
|---------------------|------------------------------------------------------------------------|  
|RequiresNew|<xref:System.ServiceModel.TransactionFlowAttribute> ayarlanır <xref:System.ServiceModel.TransactionFlowOption.NotAllowed>.<br /><br /> <xref:System.ServiceModel.OperationBehaviorAttribute.TransactionScopeRequired%2A> olan `true`.<br /><br /> `TransactionFlow` Bağlama öğesi öznitelik `false`.|  
|Gerekli|<xref:System.ServiceModel.TransactionFlowAttribute> ayarlanır <xref:System.ServiceModel.TransactionFlowOption.Allowed>.<br /><br /> <xref:System.ServiceModel.OperationBehaviorAttribute.TransactionScopeRequired%2A> olan `true`.<br /><br /> `TransactionFlow` Bağlama öğesi öznitelik `true`.|  
|Desteklenir|Doğrudan eşdeğeri yoktur. Genel olarak, belirtilen davranışı benimsemeye `Required` yerine.|  
|NotSupported|<xref:System.ServiceModel.OperationBehaviorAttribute.TransactionScopeRequired%2A> olan `false`.<br /><br /> `TransactionFlow` Bağlama öğesi öznitelik `false`.|  
|Devre dışı|Doğrudan eşdeğeri yoktur. Genel olarak, belirtilen davranışı benimsemeye `NotSupported` yerine.|
