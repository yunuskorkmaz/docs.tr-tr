---
title: 222 - OperationFailed
ms.date: 03/30/2017
ms.assetid: 6b530ded-8f20-4d78-8bfe-1875276df6ba
ms.openlocfilehash: 64b41ee78e943ca16eaa791133454ec62ccf6ed8
ms.sourcegitcommit: bc293b14af795e0e999e3304dd40c0222cf2ffe4
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/26/2020
ms.locfileid: "96263093"
---
# <a name="222---operationfailed"></a>222 - OperationFailed

## <a name="properties"></a>Özellikler  
  
|||  
|-|-|  
|ID|222|  
|Anahtar sözcükler|EndToEndMonitoring, HealthMonitoring, sorun giderme, ServiceModel|  
|Düzey|Uyarı|  
|Kanal|Microsoft-Windows-uygulama sunucusu-uygulamalar/analitik|  
  
## <a name="description"></a>Açıklama  

 Bu olay, hizmet modelinin varsayılan `OperationInvoker` yöntemi çağrılırken bir özel durumla karşılaştıysa yayınlanır. Öğesinden türetilen özel durumların `FaultException` Bu olayın yayınlanmamasına neden olduğunu unutmayın.  
  
## <a name="message"></a>İleti  

 ' %1 ' yöntemi, OperationInvoker tarafından çağrıldığında işlenmeyen bir özel durum oluşturdu. Yöntem çağrısı süresi ' %2 ' MS idi.  
  
## <a name="details"></a>Ayrıntılar  
  
|Veri öğesi adı|Veri öğesi türü|Açıklama|  
|--------------------|--------------------|-----------------|  
|Yöntem adı|`xs:string`|Tarafından çağrılan metodun CLR adı `OperationInvoker` .|  
|Süre|`xs:long`|Yöntemi çağırmak için geçen milisaniye cinsinden süre `OperationInvoker` .|  
|HostReference|`xs:string`|Web 'de barındırılan hizmetler için, bu alan hizmeti Web hiyerarşisinde benzersiz olarak tanımlar. Biçimi ' Web sitesi adı uygulama sanal yolu&#124;hizmet sanal yolu&#124;ServiceName ' olarak tanımlanmıştır. Örnek: ' Default Web site/Hesaplatooypplication&#124;/Hesaplatorservice.exe&#124;Hesaplatorservice '.|  
|AppDomain|`xs:string`|AppDomain. CurrentDomain. FriendlyName tarafından döndürülen dize.|
