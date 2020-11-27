---
title: 223 - OperationFaulted
ms.date: 03/30/2017
ms.assetid: 2f7d89d7-3a6a-40fe-9610-5424eb6bbf61
ms.openlocfilehash: 310e91320d27dd9817302fc14ef088d180152b73
ms.sourcegitcommit: bc293b14af795e0e999e3304dd40c0222cf2ffe4
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/26/2020
ms.locfileid: "96263080"
---
# <a name="223---operationfaulted"></a>223 - OperationFaulted

## <a name="properties"></a>Özellikler  
  
|||  
|-|-|  
|ID|223|  
|Anahtar sözcükler|EndToEndMonitoring, HealthMonitoring, sorun giderme, ServiceModel|  
|Düzey|Uyarı|  
|Kanal|Microsoft-Windows-uygulama sunucusu-uygulamalar/analitik|  
  
## <a name="description"></a>Açıklama  

 Bu olay, hizmet modeli varsayılan, `OperationInvoker` yöntemini çağırırken öğesinden türetilen bir özel durumla karşılaştıysa yayınlanır `FaultException` .  
  
## <a name="message"></a>İleti  

 ' %1 ' yöntemi, OperationInvoker tarafından çağrıldığında bir FaultException belirtti. Yöntem çağrısı süresi ' %2 ' MS idi.  
  
## <a name="details"></a>Ayrıntılar  
  
|Veri öğesi adı|Veri öğesi türü|Açıklama|  
|--------------------|--------------------|-----------------|  
|MethodName|`xs:string`|Tarafından çağrılan metodun CLR adı `OperationInvoker` .|  
|Süre|`xs:long`|Yöntemi çağırmak için geçen milisaniye cinsinden süre `OperationInvoker` .|  
|HostReference|`xs:string`|Web 'de barındırılan hizmetler için, bu alan hizmeti Web hiyerarşisinde benzersiz olarak tanımlar. Biçimi ' Web sitesi adı uygulama sanal yolu&#124;hizmet sanal yolu&#124;ServiceName ' olarak tanımlanmıştır. Örnek: ' Default Web site/Hesaplatooypplication&#124;/Hesaplatorservice.exe&#124;Hesaplatorservice '.|  
|AppDomain|`xs:string`|AppDomain. CurrentDomain. FriendlyName tarafından döndürülen dize.|
