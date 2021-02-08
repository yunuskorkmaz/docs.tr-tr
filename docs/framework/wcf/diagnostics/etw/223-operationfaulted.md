---
description: 'Hakkında daha fazla bilgi edinin: 223-Operationhatalı'
title: 223 - OperationFaulted
ms.date: 03/30/2017
ms.assetid: 2f7d89d7-3a6a-40fe-9610-5424eb6bbf61
ms.openlocfilehash: e4155516e07568d4ee4ca76d63754ec4171e1064
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99794292"
---
# <a name="223---operationfaulted"></a>223 - OperationFaulted

## <a name="properties"></a>Özellikler  
  
|||  
|-|-|  
|ID|223|  
|Anahtar sözcükler|EndToEndMonitoring, HealthMonitoring, sorun giderme, ServiceModel|  
|Level|Uyarı|  
|Kanal|Microsoft-Windows-uygulama sunucusu-uygulamalar/analitik|  
  
## <a name="description"></a>Description  

 Bu olay, hizmet modeli varsayılan, `OperationInvoker` yöntemini çağırırken öğesinden türetilen bir özel durumla karşılaştıysa yayınlanır `FaultException` .  
  
## <a name="message"></a>İleti  

 ' %1 ' yöntemi, OperationInvoker tarafından çağrıldığında bir FaultException belirtti. Yöntem çağrısı süresi ' %2 ' MS idi.  
  
## <a name="details"></a>Ayrıntılar  
  
|Veri öğesi adı|Veri öğesi türü|Description|  
|--------------------|--------------------|-----------------|  
|MethodName|`xs:string`|Tarafından çağrılan metodun CLR adı `OperationInvoker` .|  
|Süre|`xs:long`|Yöntemi çağırmak için geçen milisaniye cinsinden süre `OperationInvoker` .|  
|HostReference|`xs:string`|Web 'de barındırılan hizmetler için, bu alan hizmeti Web hiyerarşisinde benzersiz olarak tanımlar. Biçimi ' Web sitesi adı uygulama sanal yolu&#124;hizmet sanal yolu&#124;ServiceName ' olarak tanımlanmıştır. Örnek: ' Default Web site/Hesaplatooypplication&#124;/Hesaplatorservice.exe&#124;Hesaplatorservice '.|  
|AppDomain|`xs:string`|AppDomain. CurrentDomain. FriendlyName tarafından döndürülen dize.|
