---
title: ServiceThrottlingBehavior
ms.date: 03/30/2017
ms.assetid: 37b9e517-1f1f-4ec4-9fcb-2b8016794f5b
ms.openlocfilehash: 3bcf205964a22cdb418d0158e5ee6439169538ee
ms.sourcegitcommit: bc293b14af795e0e999e3304dd40c0222cf2ffe4
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/26/2020
ms.locfileid: "96273990"
---
# <a name="servicethrottlingbehavior"></a>ServiceThrottlingBehavior

ServiceThrottlingBehavior  
  
## <a name="syntax"></a>Syntax  
  
```csharp  
class ServiceThrottlingBehavior : Behavior  
{  
  sint32 MaxConcurrentCalls;  
  sint32 MaxConcurrentInstances;  
  sint32 MaxConcurrentSessions;  
};  
```  
  
## <a name="methods"></a>Yöntemler  

 Servicekısıtlar Lingbehavior sınıfı herhangi bir yöntem tanımlamaz.  
  
## <a name="properties"></a>Özellikler  

 Servicekısıtlar Lingbehavior sınıfı aşağıdaki özelliklere sahiptir:  
  
### <a name="maxconcurrentcalls"></a>Maxconcurrentçağrıları  

 Veri türü: Sint32  
  
 Erişim türü: salt okunurdur  
  
 ServiceHost içindeki tüm Dispatcher nesnelerinde etkin olarak işlenen en fazla ileti sayısı.  
  
### <a name="maxconcurrentinstances"></a>MaxConcurrentInstances  

 Veri türü: Sint32  
  
 Erişim türü: salt okunurdur  
  
 Tek seferde yürütebilmesi için en fazla hizmet nesnesi sayısı.  
  
### <a name="maxconcurrentsessions"></a>MaxConcurrentSessions  

 Veri türü: Sint32  
  
 Erişim türü: salt okunurdur  
  
 Bir konağın bir anda kabul edebileceği en fazla oturum sayısı.  
  
## <a name="requirements"></a>Gereksinimler  
  
|MOF|ServiceModel. mof içinde bildirilmiştir.|  
|---------|-----------------------------------|  
|Ad Alanı|Root\ServiceModel içinde tanımlı|  
  
## <a name="see-also"></a>Ayrıca bkz.

- <xref:System.ServiceModel.Description.ServiceThrottlingBehavior>
