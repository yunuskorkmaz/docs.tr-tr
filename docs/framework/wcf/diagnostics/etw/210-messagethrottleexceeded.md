---
description: 'Hakkında daha fazla bilgi edinin: 210-Messagethrottleaşıldı'
title: 210 - MessageThrottleExceeded
ms.date: 03/30/2017
ms.assetid: 24ca08ea-c11c-4753-946e-98aa820f8711
ms.openlocfilehash: e02a115995fa0e18a2ed4582710881d30bb4b846
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99794448"
---
# <a name="210---messagethrottleexceeded"></a>210 - MessageThrottleExceeded

## <a name="properties"></a>Özellikler  
  
|||  
|-|-|  
|ID|210|  
|Anahtar sözcükler|EndToEndMonitoring, HealthMonitoring, sorun giderme, ServiceModel|  
|Level|Uyarı|  
|Kanal|Microsoft-Windows-uygulama sunucusu-uygulamalar/analitik|  
  
## <a name="description"></a>Description  

 Bu olay, üç ana hizmet kısıtlarından biri aşıldığında yayınlanır. Bu olayın yalnızca kısıtlama sınırı ilk kez aşıldığında yayınlandığını unutmayın. Örneğin, eşzamanlı aramaların kısıtlama sınırı 10 ise, 11. eşzamanlı çağrı bir olay ile sonuçlanır `MessageThrottleExceeded` . 12. çağrı başka bir olayla sonuçlanmaz. Ayrıca, gürültülü bir olay akışından kaçınmak için, sınır etrafında gezinen etkinlik başka bir olayla sonuçlanmaz. Bu örnekte, birkaç çağrı tamamlandıktan sonra 9 eşzamanlı çağrı vardır. Daha sonra iki çağrı de geliyorsa, geçerli değer yeniden 11 ' dir. Bu, başka bir olay sonucu vermez. Geçerli değer kısıtlama sınırının yüzde 70 ' una düştüğünde, etkinliğin yavaşladığını belirten farklı bir olay yayınlanır. Daha sonraki etkinlik, başka bir `MessageThrottleExceeded` olayın yayılmasına neden olur. Bu örnekte, eşzamanlı çağrı miktarı 7 ' ye denk geliyorsa ve daha sonra 11 ' e ulaşırsa ve başka bir `MessageThrottleExceeded` olay yayılıyorsa.  
  
## <a name="message"></a>İleti  

 ' %2 ' için ' %1 ' kısıtlama sınırına ulaşıldı.  
  
## <a name="details"></a>Ayrıntılar  
  
|Veri öğesi adı|Veri öğesi türü|Description|  
|--------------------|--------------------|-----------------|  
|Kısıtlama adı|`xs:string`|Aşılan kısıtlama adı. `MaxConcurrentCalls`,, `MaxConcurrentInstances` Veya `MaxConcurrentSessions` ,|  
|Sınır|`xs:long`|Kısıtlama sınırının Şu anda yapılandırılmış sınırı.|  
|HostReference|`xs:string`|Web 'de barındırılan hizmetler için, bu alan hizmeti Web hiyerarşisinde benzersiz olarak tanımlar. Biçimi ' Web sitesi adı uygulama sanal yolu&#124;hizmet sanal yolu&#124;ServiceName ' olarak tanımlanmıştır. Örnek: ' Default Web site/Hesaplatooypplication&#124;/Hesaplatorservice.exe&#124;Hesaplatorservice '.|  
|AppDomain|`xs:string`|AppDomain. CurrentDomain. FriendlyName tarafından döndürülen dize.|
