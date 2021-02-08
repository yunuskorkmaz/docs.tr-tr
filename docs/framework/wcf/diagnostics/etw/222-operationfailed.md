---
description: 'Hakkında daha fazla bilgi edinin: 222-OperationFailed'
title: 222 - OperationFailed
ms.date: 03/30/2017
ms.assetid: 6b530ded-8f20-4d78-8bfe-1875276df6ba
ms.openlocfilehash: ea07dbabb651413f213db6789f2af8059d2595c6
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99794305"
---
# <a name="222---operationfailed"></a>222 - OperationFailed

## <a name="properties"></a>Özellikler  
  
|||  
|-|-|  
|ID|222|  
|Anahtar sözcükler|EndToEndMonitoring, HealthMonitoring, sorun giderme, ServiceModel|  
|Level|Uyarı|  
|Kanal|Microsoft-Windows-uygulama sunucusu-uygulamalar/analitik|  
  
## <a name="description"></a>Description  

 Bu olay, hizmet modelinin varsayılan `OperationInvoker` yöntemi çağrılırken bir özel durumla karşılaştıysa yayınlanır. Öğesinden türetilen özel durumların `FaultException` Bu olayın yayınlanmamasına neden olduğunu unutmayın.  
  
## <a name="message"></a>İleti  

 ' %1 ' yöntemi, OperationInvoker tarafından çağrıldığında işlenmeyen bir özel durum oluşturdu. Yöntem çağrısı süresi ' %2 ' MS idi.  
  
## <a name="details"></a>Ayrıntılar  
  
|Veri öğesi adı|Veri öğesi türü|Description|  
|--------------------|--------------------|-----------------|  
|Yöntem adı|`xs:string`|Tarafından çağrılan metodun CLR adı `OperationInvoker` .|  
|Süre|`xs:long`|Yöntemi çağırmak için geçen milisaniye cinsinden süre `OperationInvoker` .|  
|HostReference|`xs:string`|Web 'de barındırılan hizmetler için, bu alan hizmeti Web hiyerarşisinde benzersiz olarak tanımlar. Biçimi ' Web sitesi adı uygulama sanal yolu&#124;hizmet sanal yolu&#124;ServiceName ' olarak tanımlanmıştır. Örnek: ' Default Web site/Hesaplatooypplication&#124;/Hesaplatorservice.exe&#124;Hesaplatorservice '.|  
|AppDomain|`xs:string`|AppDomain. CurrentDomain. FriendlyName tarafından döndürülen dize.|
