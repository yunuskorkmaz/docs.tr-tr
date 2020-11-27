---
title: ServiceTimeoutsBehavior
ms.date: 03/30/2017
ms.assetid: 4412525d-a3cc-4eae-b3e8-a50ce766d09d
ms.openlocfilehash: 867219130fc853f3ba2c1c2f807b1651f6480f13
ms.sourcegitcommit: bc293b14af795e0e999e3304dd40c0222cf2ffe4
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/26/2020
ms.locfileid: "96273977"
---
# <a name="servicetimeoutsbehavior"></a>ServiceTimeoutsBehavior

ServiceTimeoutsBehavior  
  
## <a name="syntax"></a>Syntax  
  
```csharp
class ServiceTimeoutsBehavior : Behavior  
{  
  datetime TransactionTimeout;  
};  
```  
  
## <a name="methods"></a>Yöntemler  

 ServiceTimeoutsBehavior sınıfı herhangi bir yöntem tanımlamaz.  
  
## <a name="properties"></a>Özellikler  

 ServiceTimeoutsBehavior sınıfı aşağıdaki özelliğe sahiptir:  
  
### <a name="transactiontimeout"></a>Işlem zaman aşımı  

 Veri türü: DateTime  
  
 Erişim türü: salt okunurdur  
  
 Bir işlemin tamamlaması gereken dönem.  
  
## <a name="requirements"></a>Gereksinimler  
  
|MOF|ServiceModel. mof içinde bildirilmiştir.|  
|---------|-----------------------------------|  
|Ad Alanı|Root\ServiceModel içinde tanımlı|  
  
## <a name="see-also"></a>Ayrıca bkz.

- <xref:System.ServiceModel.Configuration.ServiceTimeoutsElement>
