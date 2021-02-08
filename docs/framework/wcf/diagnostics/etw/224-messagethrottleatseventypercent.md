---
description: 'Hakkında daha fazla bilgi edinin: 224-Messagethrottleaton Typercent'
title: 224 - MessageThrottleAtSeventyPercent
ms.date: 03/30/2017
ms.assetid: 82bbbfd7-10d2-41fd-805d-2443b0c1b96b
ms.openlocfilehash: 14c08371c5db7e6f7deb0a5851a1d24dfc94475e
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99794279"
---
# <a name="224---messagethrottleatseventypercent"></a>224 - MessageThrottleAtSeventyPercent

## <a name="properties"></a>Özellikler  
  
|||  
|-|-|  
|ID|224|  
|Anahtar sözcükler|EndToEndMonitoring, HealthMonitoring, sorun giderme, ServiceModel|  
|Level|Uyarı|  
|Kanal|Microsoft-Windows-uygulama sunucusu-uygulamalar/analitik|  
  
## <a name="description"></a>Description  

 Ana hizmet kısıtlarından biri aşıldığında, `MessageThrottleExceeded` olay yayınlanır. Etkinliğin ani artış ve geçerli sınırın %70 ' i geçerli sınırın yüzde ' sinden sonra bu olay yayınlanır. Etkinlik yavaşlattığı için bu olayın yalnızca bir kez yayınlandığını unutmayın. Geçerli değer yüzde 70 işaretine (örneğin, 70, 69, 70, 71, 70, 69) olursa, yalnızca %70 ' in ilk oluşumu bir olay ile sonuçlanır. Bu olay oluşturulduktan sonra, bir olayda kısıtlama sınırını aşmaya neden olan Tekrarların elde edilmesine neden olur `MessageThrottleExceeded` .  
  
## <a name="message"></a>İleti  

 ' %2 ' öğesinin ' %1 ' kısıtlama sınırı %70.  
  
## <a name="details"></a>Ayrıntılar  
  
|Veri öğesi adı|Veri öğesi türü|Description|  
|--------------------|--------------------|-----------------|  
|Kısıtlama adı|`xs:string`|Aşılan kısıtlama adı. `MaxConcurrentCalls`,, `MaxConcurrentInstances` Veya `MaxConcurrentSessions` ,|  
|Sınır|`xs:long`|Kısıtlama sınırının Şu anda yapılandırılmış sınırı.|  
|HostReference|`xs:string`|Web 'de barındırılan hizmetler için, bu alan hizmeti Web hiyerarşisinde benzersiz olarak tanımlar. Biçimi ' Web sitesi adı uygulama sanal yolu&#124;hizmet sanal yolu&#124;ServiceName ' olarak tanımlanmıştır. Örnek: ' Default Web site/Hesaplatooypplication&#124;/Hesaplatorservice.exe&#124;Hesaplatorservice '.|  
|AppDomain|`xs:string`|AppDomain. CurrentDomain. FriendlyName tarafından döndürülen dize.|
