---
title: 224 - MessageThrottleAtSeventyPercent
ms.date: 03/30/2017
ms.assetid: 82bbbfd7-10d2-41fd-805d-2443b0c1b96b
ms.openlocfilehash: f70dc235e037b4f490a25866940fe2bccceae2a1
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/23/2019
ms.locfileid: "61916311"
---
# <a name="224---messagethrottleatseventypercent"></a>224 - MessageThrottleAtSeventyPercent
## <a name="properties"></a>Özellikler  
  
|||  
|-|-|  
|Kimlik|224|  
|anahtar sözcükler|Sorun giderme, ServiceModel EndToEndMonitoring, ögesi,|  
|Düzey|Uyarı|  
|Kanal|Microsoft Windows uygulama sunucusu-uygulamalar/analitik|  
  
## <a name="description"></a>Açıklama  
 Ana hizmet kısıtlamalar biri aşıldığında `MessageThrottleExceeded` olay yayılır. Ne zaman ani etkinlik yavaşlatır ve kısıtlama geçerli değeri, geçerli sınır yüzde 70 bu olay ise yayılır. Bu olay etkinliği olarak yavaşlamasını sonra yalnızca yayıldığını unutmayın. Geçerli değer yüzde 70 işaretinde getirirse (örneğin, 70,69,70,71,70,69), bir olayı yüzde 70 yalnızca ilk geçtiği sonuçlanır. Bu olay yayılan sonra gelecekte tekrarlanma olasılığını azaltması'nın aşılması, sonuç sınırlamak bir `MessageThrottleExceeded` olay.  
  
## <a name="message"></a>İleti  
 70 sırasında '%2', '%1' kısıtlama sınırı olan %%.  
  
## <a name="details"></a>Ayrıntılar  
  
|Veri öğesi adı|Veri öğesi türü|Açıklama|  
|--------------------|--------------------|-----------------|  
|Kısıtlama adı|`xs:string`|Aşıldı kısıtlama adı. Her iki `MaxConcurrentCalls`, `MaxConcurrentInstances`, veya `MaxConcurrentSessions`,|  
|Sınır|`xs:long`|Şu anda yapılandırılmış olan kısıtlama sınırı.|  
|HostReference|`xs:string`|Bu alan, Web barındırılan hizmetleri, Web hiyerarşideki hizmet benzersiz olarak tanımlar. Biçimi olarak tanımlanan ' Web sitesi adı uygulamanın sanal yolu&#124;hizmet sanal yolu&#124;HizmetAdı '. Örnek: ' Varsayılan Web sitesi/CalculatorApplication&#124;/CalculatorService.svc&#124;CalculatorService'.|  
|AppDomain|`xs:string`|AppDomain.CurrentDomain.FriendlyName tarafından döndürülen dize.|
