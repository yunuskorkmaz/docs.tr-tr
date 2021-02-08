---
description: 'Hakkında daha fazla bilgi edinin: 214-OperationCompleted'
title: 214 - OperationCompleted
ms.date: 03/30/2017
ms.assetid: a6287eef-023f-4816-813c-1802c82366df
ms.openlocfilehash: aad1ac49667a2ebbf172b5132507584e05d0f03e
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99794396"
---
# <a name="214---operationcompleted"></a>214 - OperationCompleted

## <a name="properties"></a>Özellikler  
  
|||  
|-|-|  
|ID|214|  
|Anahtar sözcükler|HealthMonitoring, EndToEndMonitoring, sorun giderme, ServiceModel|  
|Level|Bilgi|  
|Kanal|Microsoft-Windows-uygulama sunucusu-uygulamalar/analitik|  
  
## <a name="description"></a>Description  

 Bu olay, hizmet modelinin varsayılan yöntemi bir `OperationInvoker` özel durum oluşturmadan bir yönteme çağrı tamamladığında yayınlanır.  
  
## <a name="message"></a>İleti  

 Bir OperationInvoker ' %1 ' metoduna çağrıyı tamamladı. Yöntem çağrısı süresi ' %2 ' MS idi.  
  
## <a name="details"></a>Ayrıntılar  
  
|Veri öğesi adı|Veri öğesi türü|Description|  
|--------------------|--------------------|-----------------|  
|Yöntem adı|`xs:string`|Tarafından çağrılan metodun CLR adı `OperationInvoker` .|  
|Süre|`xs:long`|Yöntemi çağırmak için geçen milisaniye cinsinden süre `OperationInvoker` .|  
|HostReference|`xs:string`|Web 'de barındırılan hizmetler için, bu alan hizmeti Web hiyerarşisinde benzersiz olarak tanımlar. Biçimi ' Web sitesi adı uygulama sanal yolu&#124;hizmet sanal yolu&#124;ServiceName ' olarak tanımlanmıştır. Örnek: ' Default Web site/Hesaplatooypplication&#124;/Hesaplatorservice.exe&#124;Hesaplatorservice '.|  
|AppDomain|`xs:string`|AppDomain. CurrentDomain. FriendlyName tarafından döndürülen dize.|
