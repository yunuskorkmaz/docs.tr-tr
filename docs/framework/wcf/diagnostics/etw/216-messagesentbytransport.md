---
title: 216 - MessageSentByTransport
ms.date: 03/30/2017
ms.assetid: 150c3167-4154-4225-8d94-57cc94341233
ms.openlocfilehash: b3e9e1a48951ad5a2e5e7820dc1828c20e310635
ms.sourcegitcommit: bc293b14af795e0e999e3304dd40c0222cf2ffe4
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/26/2020
ms.locfileid: "96278914"
---
# <a name="216---messagesentbytransport"></a>216 - MessageSentByTransport

## <a name="properties"></a>Özellikler  
  
|||  
|-|-|  
|ID|216|  
|Anahtar sözcükler|Sorun giderme, ServiceModel|  
|Düzey|Bilgi|  
|Kanal|Microsoft-Windows-uygulama sunucusu-uygulamalar/analitik|  
  
## <a name="description"></a>Açıklama  

 Bu olay, TCP tabanlı bir aktarım bir ileti gönderdiğinde meydana gelir. Aktarım düzeyinde birden çok iletinin tek bir işlem için istemciler ve hizmetler arasında değiş tokuş olabileceğini unutmayın. Bunun nedeni altyapı davranışından kaynaklanabilir, güvenliğin iyi bir örnek olması olabilir. Bu nedenle, yayınlanan **Iletikübytransport** olaylarının sayısı hizmetinizin bağlamasına ve yapılandırmasına göre farklılık gösterir.  
  
## <a name="message"></a>İleti  

 Taşıma, ' %1 ' öğesine bir ileti gönderdi.  
  
## <a name="details"></a>Ayrıntılar  
  
|Veri öğesi adı|Veri öğesi türü|Açıklama|  
|--------------------|--------------------|-----------------|  
|Hedef adres|`xs:string`|İstek iletisinin gönderildiği adres.|  
|HostReference|xs: String|Web 'de barındırılan hizmetler için, bu alan hizmeti Web hiyerarşisinde benzersiz olarak tanımlar. Biçimi ' Web sitesi adı uygulama sanal yolu&#124;hizmet sanal yolu&#124;ServiceName ' olarak tanımlanmıştır. Örnek: ' Default Web site/Hesaplatooypplication&#124;/Hesaplatorservice.exe&#124;Hesaplatorservice '.|  
|AppDomain|`xs:string`|AppDomain. CurrentDomain. FriendlyName tarafından döndürülen dize.|
