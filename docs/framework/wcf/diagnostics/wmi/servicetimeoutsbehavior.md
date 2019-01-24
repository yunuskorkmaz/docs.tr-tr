---
title: ServiceTimeoutsBehavior
ms.date: 03/30/2017
ms.assetid: 4412525d-a3cc-4eae-b3e8-a50ce766d09d
ms.openlocfilehash: b129483b60a62f04f522036c9d1fa54268f6f346
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54566677"
---
# <a name="servicetimeoutsbehavior"></a>ServiceTimeoutsBehavior
ServiceTimeoutsBehavior  
  
## <a name="syntax"></a>Sözdizimi  
  
```csharp
class ServiceTimeoutsBehavior : Behavior  
{  
  datetime TransactionTimeout;  
};  
```  
  
## <a name="methods"></a>Yöntemler  
 ServiceTimeoutsBehavior sınıf herhangi bir yöntemi tanımlamaz.  
  
## <a name="properties"></a>Özellikler  
 ServiceTimeoutsBehavior sınıfı şu özelliğe sahip:  
  
### <a name="transactiontimeout"></a>TransactionTimeout  
 Veri türü: tarih/saat  
  
 Erişim türü: salt okunur  
  
 İçinde bir işlemin tamamlanması gereken süre.  
  
## <a name="requirements"></a>Gereksinimler  
  
|MOF|Bildirilmiş Servicemodel.mof.|  
|---------|-----------------------------------|  
|Ad Alanı|İçinde tanımlı root\ServiceModel|  
  
## <a name="see-also"></a>Ayrıca bkz.
- <xref:System.ServiceModel.Configuration.ServiceTimeoutsElement>
