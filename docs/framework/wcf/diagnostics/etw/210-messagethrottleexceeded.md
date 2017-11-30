---
title: 210 - MessageThrottleExceeded
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 24ca08ea-c11c-4753-946e-98aa820f8711
caps.latest.revision: "5"
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: 2d027f549e86095c732d0e60df3faded44a39fd2
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/18/2017
---
# <a name="210---messagethrottleexceeded"></a>210 - MessageThrottleExceeded
## <a name="properties"></a>Özellikler  
  
|||  
|-|-|  
|Kimlik|210|  
|Anahtar Sözcükler|Sorun giderme, ServiceModel EndToEndMonitoring, ögesi,|  
|Düzey|Uyarı|  
|Kanal|Microsoft Windows uygulama sunucusu-uygulamalar/analitik|  
  
## <a name="description"></a>Açıklama  
 Bu olay varsa gösterilen üç ana hizmet kısıtlamaları aşılmış. Kısıtlama sınırı başlangıçta aşıldığında, bu olay yalnızca yayılan unutmayın. Örneğin, eşzamanlı çağrıları kısıtlama sınırı 10, 11 eşzamanlı arama sonuçları bir `MessageThrottleExceeded` olay. 12 çağrısı içinde başka bir olay oluşmaz. Ayrıca, gürültülü olay akışını önlemek için sınırı gezinen etkinlik başka bir olaya oluşmaz. Bu örnekte, birkaç çağrıları tamamlarsanız sonra var. 9 eşzamanlı çağrıları Daha sonra iki çağrı gelse, geçerli yeniden 11 değeridir. Bu, başka bir olaya oluşmaz. Kısıtlama sınırı % 70 yüzdesi geçerli değeri düştüğünde farklı bir olay etkinliği yavaş gösteren yayınlanır. Sınırı aşan gelecekteki etkinlik sonuçları başka bir programda `MessageThrottleExceeded` gösterilmesini olay. Bu örnekte, eşzamanlı çağrıları miktarını 7'ye döner ve daha sonra tekrar 11 ve başka ulaştığında `MessageThrottleExceeded` olay yayılan.  
  
## <a name="message"></a>İleti  
 '% 2' '%1' kısıtlama sınırına ulaşıldı.  
  
## <a name="details"></a>Ayrıntılar  
  
|Veri öğesi adı|Veri öğesi türü|Açıklama|  
|--------------------|--------------------|-----------------|  
|Kısıtlama adı|`xs:string`|Aşıldı kısıtlama adı. Her iki `MaxConcurrentCalls`, `MaxConcurrentInstances`, veya `MaxConcurrentSessions`,|  
|Sınırı|`xs:long`|Kısıtlama şu anda yapılandırılmış sınırının.|  
|HostReference|`xs:string`|Bu alan, Web barındırılan hizmetler için Web hiyerarşi hizmetinde benzersiz olarak tanımlar. Biçimi olarak tanımlanan ' Web sitesi adı uygulamanın sanal yolu &#124; Hizmet sanal yolu &#124; ServiceName'. Örnek: ' varsayılan Web sitesi/CalculatorApplication, #124;/CalculatorService.svc &#124; CalculatorService'.|  
|AppDomain|`xs:string`|AppDomain.CurrentDomain.FriendlyName tarafından döndürülen dize.|
