---
title: 215 - MessageReceivedByTransport
ms.date: 03/30/2017
ms.assetid: bb32aa60-5207-4711-9f08-110e8ac327e5
ms.openlocfilehash: 2f247e751a0690f13d059eff29d633c6d047775d
ms.sourcegitcommit: bc293b14af795e0e999e3304dd40c0222cf2ffe4
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/26/2020
ms.locfileid: "96279083"
---
# <a name="215---messagereceivedbytransport"></a>215 - MessageReceivedByTransport

## <a name="properties"></a>Özellikler  
  
|||  
|-|-|  
|ID|215|  
|Anahtar sözcükler|Sorun giderme, ServiceModel|  
|Düzey|Bilgi|  
|Kanal|Microsoft-Windows-uygulama sunucusu-uygulamalar/analitik|  
  
## <a name="description"></a>Açıklama  

 Bu olay, TCP tabanlı bir aktarım bir ileti aldığında oluşur. Aktarım düzeyinde, tek bir işlem için istemciler ve hizmetler arasında birden çok ileti değiş tokuş olabileceğini unutmayın. Bunun nedeni altyapı davranışından kaynaklanıyor olabilir, güvenlik iyi bir örnektir. Bu nedenle, yayınlanan `MessageReceivedByTransport` olay sayısı hizmetinizin bağlamasına ve yapılandırmasına göre farklılık gösterir.  
  
> [!NOTE]
> Bu olay tek yönlü aktarımlar için yayınlanmaz.  
  
## <a name="message"></a>İleti  

 Taşıma, ' %1 ' öğesinden bir ileti aldı.  
  
## <a name="details"></a>Ayrıntılar  
  
|Veri öğesi adı|Veri öğesi türü|Açıklama|  
|--------------------|--------------------|-----------------|  
|Dinleme adresi|`xs:string`|İletiyi alan adres.|  
|HostReference|`xs:string`|Web 'de barındırılan hizmetler için, bu alan hizmeti Web hiyerarşisinde benzersiz olarak tanımlar. Biçimi ' Web sitesi adı uygulama sanal yolu&#124;hizmet sanal yolu&#124;ServiceName ' olarak tanımlanmıştır. Örnek: ' Default Web site/Hesaplatooypplication&#124;/Hesaplatorservice.exe&#124;Hesaplatorservice '.|  
|AppDomain|`xs:string`|AppDomain. CurrentDomain. FriendlyName tarafından döndürülen dize.|
