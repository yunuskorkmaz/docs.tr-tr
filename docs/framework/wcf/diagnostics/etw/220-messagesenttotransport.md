---
description: 'Hakkında daha fazla bilgi edinin: 220-Iletienttotransport'
title: 220 - MessageSentToTransport
ms.date: 03/30/2017
ms.assetid: aef4e781-240b-45bc-bff8-400053037e71
ms.openlocfilehash: 8d76f147c8a31a5aa08c21073cd03e63436095ff
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99794318"
---
# <a name="220---messagesenttotransport"></a>220 - MessageSentToTransport

## <a name="properties"></a>Özellikler  
  
|||  
|-|-|  
|Id|220|  
|Anahtar sözcükler|EndToEndMonitoring, sorun giderme, ServiceModel|  
|Level|Bilgi|  
|Kanal|Microsoft-Windows-uygulama sunucusu-uygulamalar/analitik|  
  
## <a name="description"></a>Description  

 Bu olay, hizmet modeli aktarıma bir ileti gönderdiğinde yayınlanır.  
  
> [!NOTE]
> Bu olay tek yönlü aktarımlar için yayınlanmayacak.  
  
## <a name="message"></a>İleti  

 Dağıtıcı, aktarıma bir ileti gönderdi. Bağıntı KIMLIĞI = = ' %1 '.  
  
## <a name="details"></a>Ayrıntılar  
  
|Veri öğesi adı|Veri öğesi türü|Description|  
|--------------------|--------------------|-----------------|  
|Bağıntı Kimliği|`xs:GUID`|`MessageSentToTransport`Bir hizmet veya istemciden bir olayı diğer uçta karşılık gelen bir olay ile ilişkilendirmek için kullanılan etkınlık kimliği `MessageReceivedFromTransport` .|  
|HostReference|`xs:string`|Web 'de barındırılan hizmetler için, bu alan hizmeti Web hiyerarşisinde benzersiz olarak tanımlar. Biçimi ' Web sitesi adı uygulama sanal yolu&#124;hizmet sanal yolu&#124;ServiceName ' olarak tanımlanmıştır. Örnek: ' Default Web site/Hesaplatooypplication&#124;/Hesaplatorservice.exe&#124;Hesaplatorservice '.|  
|AppDomain|`xs:string`|AppDomain. CurrentDomain. FriendlyName tarafından döndürülen dize.|
