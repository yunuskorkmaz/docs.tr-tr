---
title: ServiceThrottlingBehavior
ms.date: 03/30/2017
ms.assetid: 37b9e517-1f1f-4ec4-9fcb-2b8016794f5b
ms.openlocfilehash: edc154fcce0058455f1376a2a45807c92f7f2457
ms.sourcegitcommit: c93fd5139f9efcf6db514e3474301738a6d1d649
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/27/2018
ms.locfileid: "50190963"
---
# <a name="servicethrottlingbehavior"></a>ServiceThrottlingBehavior
ServiceThrottlingBehavior  
  
## <a name="syntax"></a>Sözdizimi  
  
```csharp  
class ServiceThrottlingBehavior : Behavior  
{  
  sint32 MaxConcurrentCalls;  
  sint32 MaxConcurrentInstances;  
  sint32 MaxConcurrentSessions;  
};  
```  
  
## <a name="methods"></a>Yöntemler  
 Denetlemek ServiceThrottlingBehavior sınıf herhangi bir yöntemi tanımlamaz.  
  
## <a name="properties"></a>Özellikler  
 Denetlemek ServiceThrottlingBehavior sınıfı aşağıdaki özelliklere sahiptir:  
  
### <a name="maxconcurrentcalls"></a>maxConcurrentCalls  
 Veri türü: SINT32  
  
 Erişim türü: salt okunur  
  
 Bir ServiceHost tüm dağıtıcı nesneler arasında etkin bir şekilde işlenen ileti sayısı.  
  
### <a name="maxconcurrentinstances"></a>MaxConcurrentInstances  
 Veri türü: SINT32  
  
 Erişim türü: salt okunur  
  
 Aynı anda çalışabilecek hizmet nesneleri sayısı.  
  
### <a name="maxconcurrentsessions"></a>MaxConcurrentSessions  
 Veri türü: SINT32  
  
 Erişim türü: salt okunur  
  
 En fazla bir konak aynı anda kabul edebileceği oturum sayısını.  
  
## <a name="requirements"></a>Gereksinimler  
  
|MOF|Bildirilmiş Servicemodel.mof.|  
|---------|-----------------------------------|  
|Ad Alanı|İçinde tanımlı root\ServiceModel|  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 <xref:System.ServiceModel.Description.ServiceThrottlingBehavior>
