---
title: COM+ ve ServiceModel İşlemlerini Karşılaştırma
ms.date: 03/30/2017
ms.assetid: e493bcdd-b91a-4486-853f-83dbcd1931b7
ms.openlocfilehash: 4a47fe1686dff2e705b06b001d7d5e4ea6e8c5f2
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33488653"
---
# <a name="comparing-transactions-in-com-and-servicemodel"></a>COM+ ve ServiceModel İşlemlerini Karşılaştırma
Bu konuda Windows Communication Foundation (WCF) özniteliklerini kullanarak işlem bir COM + hizmet davranışını benzetmek nasıl ele alınmıştır <xref:System.ServiceModel> ad alanı sağlar.  
  
## <a name="emulating-com-using-servicemodel-attributes"></a>COM + ServiceModel öznitelikleri kullanarak öykünmesini yapma  
 Aşağıdaki tabloda karşılaştırır <xref:System.EnterpriseServices.TransactionOption> numaralandırması oluşturmak için kullanılan bir `EnterpriseServices` işlem ve bunların nasıl WCF öznitelikleri ilişkilendirmek <xref:System.ServiceModel> ad alanı sağlar.  
  
|COM + özniteliği|WCF öznitelikleri|  
|---------------------|------------------------------------------------------------------------|  
|RequiresNew|<xref:System.ServiceModel.TransactionFlowAttribute> ayarlanmış <xref:System.ServiceModel.TransactionFlowOption.NotAllowed>.<br /><br /> <xref:System.ServiceModel.OperationBehaviorAttribute.TransactionScopeRequired%2A> olan `true`.<br /><br /> `TransactionFlow` Bağlama öğesi içinde özniteliktir `false`.|  
|Gerekli|<xref:System.ServiceModel.TransactionFlowAttribute> ayarlanmış <xref:System.ServiceModel.TransactionFlowOption.Allowed>.<br /><br /> <xref:System.ServiceModel.OperationBehaviorAttribute.TransactionScopeRequired%2A> olan `true`.<br /><br /> `TransactionFlow` Bağlama öğesi içinde özniteliktir `true`.|  
|Desteklenir|Doğrudan bir eşdeğeri yoktur. İçin belirtilen davranışı genel olarak, benimsemeyi `Required` yerine.|  
|NotSupported|<xref:System.ServiceModel.OperationBehaviorAttribute.TransactionScopeRequired%2A> olan `false`.<br /><br /> `TransactionFlow` Bağlama öğesi içinde özniteliktir `false`.|  
|Devre dışı|Doğrudan bir eşdeğeri yoktur. İçin belirtilen davranışı genel olarak, benimsemeyi `NotSupported` yerine.|
