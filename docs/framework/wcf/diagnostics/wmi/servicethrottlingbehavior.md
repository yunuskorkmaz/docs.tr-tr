---
description: 'Hakkında daha fazla bilgi edinin: Servicekısıtlar Lingbehavior'
title: ServiceThrottlingBehavior
ms.date: 03/30/2017
ms.assetid: 37b9e517-1f1f-4ec4-9fcb-2b8016794f5b
ms.openlocfilehash: c4cf354c96340b910807bf7904e63a08dc01764b
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99715450"
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
