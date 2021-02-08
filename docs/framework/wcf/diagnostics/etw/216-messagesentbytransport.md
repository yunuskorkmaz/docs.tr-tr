---
description: 'Hakkında daha fazla bilgi edinin: 216-Iletientbytransport'
title: 216 - MessageSentByTransport
ms.date: 03/30/2017
ms.assetid: 150c3167-4154-4225-8d94-57cc94341233
ms.openlocfilehash: 34c10fbbf61adde102641cb44db6645ea648a646
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99794383"
---
# <a name="216---messagesentbytransport"></a>216 - MessageSentByTransport

## <a name="properties"></a>Özellikler  
  
|||  
|-|-|  
|ID|216|  
|Anahtar sözcükler|Sorun giderme, ServiceModel|  
|Level|Bilgi|  
|Kanal|Microsoft-Windows-uygulama sunucusu-uygulamalar/analitik|  
  
## <a name="description"></a>Description  

 Bu olay, TCP tabanlı bir aktarım bir ileti gönderdiğinde meydana gelir. Aktarım düzeyinde birden çok iletinin tek bir işlem için istemciler ve hizmetler arasında değiş tokuş olabileceğini unutmayın. Bunun nedeni altyapı davranışından kaynaklanabilir, güvenliğin iyi bir örnek olması olabilir. Bu nedenle, yayınlanan **Iletikübytransport** olaylarının sayısı hizmetinizin bağlamasına ve yapılandırmasına göre farklılık gösterir.  
  
## <a name="message"></a>İleti  

 Taşıma, ' %1 ' öğesine bir ileti gönderdi.  
  
## <a name="details"></a>Ayrıntılar  
  
|Veri öğesi adı|Veri öğesi türü|Description|  
|--------------------|--------------------|-----------------|  
|Hedef adres|`xs:string`|İstek iletisinin gönderildiği adres.|  
|HostReference|xs: String|Web 'de barındırılan hizmetler için, bu alan hizmeti Web hiyerarşisinde benzersiz olarak tanımlar. Biçimi ' Web sitesi adı uygulama sanal yolu&#124;hizmet sanal yolu&#124;ServiceName ' olarak tanımlanmıştır. Örnek: ' Default Web site/Hesaplatooypplication&#124;/Hesaplatorservice.exe&#124;Hesaplatorservice '.|  
|AppDomain|`xs:string`|AppDomain. CurrentDomain. FriendlyName tarafından döndürülen dize.|
