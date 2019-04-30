---
title: 210 - MessageThrottleExceeded
ms.date: 03/30/2017
ms.assetid: 24ca08ea-c11c-4753-946e-98aa820f8711
ms.openlocfilehash: 7ba5948b36642085ef44661b3d580e7f1c4102cb
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/23/2019
ms.locfileid: "61781894"
---
# <a name="210---messagethrottleexceeded"></a>210 - MessageThrottleExceeded
## <a name="properties"></a>Özellikler  
  
|||  
|-|-|  
|Kimlik|210|  
|anahtar sözcükler|Sorun giderme, ServiceModel EndToEndMonitoring, ögesi,|  
|Düzey|Uyarı|  
|Kanal|Microsoft Windows uygulama sunucusu-uygulamalar/analitik|  
  
## <a name="description"></a>Açıklama  
 Bu olay bir yayıldığını üç ana hizmet kısıtlamalar aşıldı. Kısıtlama sınırı başlangıçta aşıldığında bu olay yalnızca yayıldığını unutmayın. Örneğin, eş zamanlı çağrılar için kısıtlama sınırı 10, 11 eşzamanlı arama sonuçları bir `MessageThrottleExceeded` olay. 12 çağrı başka bir olaya sonuçlanmaz. Ayrıca, gürültülü olay akışını önlemek için sınırı gezinen etkinlik başka bir olaya sonuçlanmaz. Bu örnekte, birkaç çağrıları tamamlarsanız ardından var. 9 eş zamanlı çağrılar Daha sonra iki daha fazla çağrıları geldiğinde, geçerli değeri yeniden 11 olur. Bu, başka bir olaya sonuçlanmaz. Kısıtlama sınırı % 70 yüzdesi geçerli değeri düştüğünde farklı bir olay etkinliği yavaş olmuştur gösteren yayınlanır. Sınırı aşan gelecekteki etkinliğine neden başka `MessageThrottleExceeded` yayılan olay. Bu örnekte, eş zamanlı çağrı miktarı 7'ye döner ve daha sonra tekrar 11 ve başka ulaştığında `MessageThrottleExceeded` olay yayılır.  
  
## <a name="message"></a>İleti  
 '%2', '%1' azaltma sınırına ulaşıldı.  
  
## <a name="details"></a>Ayrıntılar  
  
|Veri öğesi adı|Veri öğesi türü|Açıklama|  
|--------------------|--------------------|-----------------|  
|Kısıtlama adı|`xs:string`|Aşıldı kısıtlama adı. Her iki `MaxConcurrentCalls`, `MaxConcurrentInstances`, veya `MaxConcurrentSessions`,|  
|Sınır|`xs:long`|Şu anda yapılandırılmış olan kısıtlama sınırı.|  
|HostReference|`xs:string`|Bu alan, Web barındırılan hizmetleri, Web hiyerarşideki hizmet benzersiz olarak tanımlar. Biçimi olarak tanımlanan ' Web sitesi adı uygulamanın sanal yolu&#124;hizmet sanal yolu&#124;HizmetAdı '. Örnek: ' Varsayılan Web sitesi/CalculatorApplication&#124;/CalculatorService.svc&#124;CalculatorService'.|  
|AppDomain|`xs:string`|AppDomain.CurrentDomain.FriendlyName tarafından döndürülen dize.|
