---
title: 224 - MessageThrottleAtSeventyPercent
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 82bbbfd7-10d2-41fd-805d-2443b0c1b96b
caps.latest.revision: "5"
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: 0dd985e3986548938f06e86c1f49d23c43307d17
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/18/2017
---
# <a name="224---messagethrottleatseventypercent"></a>224 - MessageThrottleAtSeventyPercent
## <a name="properties"></a>Özellikler  
  
|||  
|-|-|  
|Kimlik|224|  
|Anahtar Sözcükler|Sorun giderme, ServiceModel EndToEndMonitoring, ögesi,|  
|Düzey|Uyarı|  
|Kanal|Microsoft Windows uygulama sunucusu-uygulamalar/analitik|  
  
## <a name="description"></a>Açıklama  
 Ana hizmet kısıtlamaları birini aşıldığında `MessageThrottleExceeded` olay yayılan. Ne zaman etkinlik depo yavaşlatır ve geçerli kısıtlama yüzde 70'i geçerli sınır ardından bu olay değeri yayınlanır. Bu olay yalnızca etkinlik olarak yavaşlamasını sonra yayınlanır unutmayın. Geçerli değeri yüzde 70 işaretinde gezinen varsa (örneğin, 70,69,70,71,70,69), yalnızca ilk örneğini yüzde 70 olayda sonuçlanır. Bu olay yayılan sonra azaltma ait aşan, gelecekteki oluşumları sonucunda sınırlamak bir `MessageThrottleExceeded` olay.  
  
## <a name="message"></a>İleti  
 70 '% 2' '%1' kısıtlama sınırı olan %%.  
  
## <a name="details"></a>Ayrıntılar  
  
|Veri öğesi adı|Veri öğesi türü|Açıklama|  
|--------------------|--------------------|-----------------|  
|Kısıtlama adı|`xs:string`|Aşıldı kısıtlama adı. Her iki `MaxConcurrentCalls`, `MaxConcurrentInstances`, veya `MaxConcurrentSessions`,|  
|Sınırı|`xs:long`|Kısıtlama şu anda yapılandırılmış sınırının.|  
|HostReference|`xs:string`|Bu alan, Web barındırılan hizmetler için Web hiyerarşi hizmetinde benzersiz olarak tanımlar. Biçimi olarak tanımlanan ' Web sitesi adı uygulamanın sanal yolu &#124; Hizmet sanal yolu &#124; ServiceName'. Örnek: ' varsayılan Web sitesi/CalculatorApplication, #124;/CalculatorService.svc &#124; CalculatorService'.|  
|AppDomain|`xs:string`|AppDomain.CurrentDomain.FriendlyName tarafından döndürülen dize.|
