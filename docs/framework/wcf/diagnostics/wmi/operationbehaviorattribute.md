---
description: 'Şu konuda daha fazla bilgi edinin: OperationBehaviorAttribute'
title: OperationBehaviorAttribute
ms.date: 03/30/2017
ms.assetid: 8c9b0755-9e83-411f-bdcb-61a586022797
ms.openlocfilehash: c1f1b80134163ee65d5015e52017f5bb455aeac7
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99803067"
---
# <a name="operationbehaviorattribute"></a>OperationBehaviorAttribute

OperationBehaviorAttribute  
  
## <a name="syntax"></a>Syntax  
  
```csharp
class OperationBehaviorAttribute : Behavior  
{  
  boolean AutoDisposeParameters;  
  string Impersonation;  
  string ReleaseInstanceMode;  
  boolean TransactionAutoComplete;  
  boolean TransactionScopeRequired;  
};  
```  
  
## <a name="methods"></a>Yöntemler  

 OperationBehaviorAttribute sınıfı herhangi bir yöntem tanımlamaz.  
  
## <a name="properties"></a>Özellikler  

 OperationBehaviorAttribute sınıfı aşağıdaki özelliklere sahiptir:  
  
### <a name="autodisposeparameters"></a>Oto Disposeparameters  

 Veri türü: Boole  
  
 Erişim türü: salt okunurdur  
  
 Parametrelerin otomatik atımı özelliğinin durumu.  
  
### <a name="impersonation"></a>Kimliğe bürünme  

 Veri türü: dize  
  
 Erişim türü: salt okunurdur  
  
 İşlemin desteklediği çağıran kimliğe bürünme düzeyini gösterir.  
  
### <a name="releaseinstancemode"></a>ReleaseInstanceMode  

 Veri türü: dize  
  
 Erişim türü: salt okunurdur  
  
 Nesnenin geri dönüştürülmesinin ne zaman bir işlem çağrısı olduğu gösterilir.  
  
### <a name="transactionautocomplete"></a>TransactionAutoComplete  

 Veri türü: Boole  
  
 Erişim türü: salt okunurdur  
  
 İşlenmeyen özel durumlar oluşursa geçerli işlemin otomatik olarak kaydedilip edilmeyeceğini belirtir.  
  
### <a name="transactionscoperequired"></a>TransactionScopeRequired  

 Veri türü: Boole  
  
 Erişim türü: salt okunurdur  
  
 İşlemin bir işlem gerektirip gerektirmediğini belirtir.  
  
## <a name="requirements"></a>Gereksinimler  
  
|MOF|ServiceModel. mof içinde bildirilmiştir.|  
|---------|-----------------------------------|  
|Ad Alanı|Root\ServiceModel içinde tanımlı|  
  
## <a name="see-also"></a>Ayrıca bkz.

- <xref:System.ServiceModel.OperationBehaviorAttribute>
