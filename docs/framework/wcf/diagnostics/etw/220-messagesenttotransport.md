---
title: 220 - MessageSentToTransport
ms.date: 03/30/2017
ms.assetid: aef4e781-240b-45bc-bff8-400053037e71
ms.openlocfilehash: 9f95edf42e0b1ec19d2019773def282fc279871b
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/22/2019
ms.locfileid: "69948292"
---
# <a name="220---messagesenttotransport"></a>220 - MessageSentToTransport
## <a name="properties"></a>Özellikler  
  
|||  
|-|-|  
|Id|220|  
|anahtar sözcükler|EndToEndMonitoring, sorun giderme, ServiceModel|  
|Düzey|Bilgiler|  
|Kanalla|Microsoft-Windows-uygulama sunucusu-uygulamalar/analitik|  
  
## <a name="description"></a>Açıklama  
 Bu olay, hizmet modeli aktarıma bir ileti gönderdiğinde yayınlanır.  
  
> [!NOTE]
> Bu olay tek yönlü aktarımlar için yayınlanmayacak.  
  
## <a name="message"></a>`Message`  
 Dağıtıcı, aktarıma bir ileti gönderdi. Bağıntı KIMLIĞI = = '% 1 '.  
  
## <a name="details"></a>Ayrıntılar  
  
|Veri öğesi adı|Veri öğesi türü|Açıklama|  
|--------------------|--------------------|-----------------|  
|Bağıntı Kimliği|`xs:GUID`|Bir hizmet veya istemciden bir olayı diğer `MessageSentToTransport` uçta karşılık gelen `MessageReceivedFromTransport` bir olay ile ilişkilendirmek için kullanılan etkinlik kimliği.|  
|HostReference|`xs:string`|Web 'de barındırılan hizmetler için, bu alan hizmeti Web hiyerarşisinde benzersiz olarak tanımlar. Biçimi ' Web sitesi adı uygulama sanal yolu&#124;hizmeti sanal yolu&#124;ServiceName ' olarak tanımlanmıştır. Örnek: ' Default Web site/Hesaplatooypplication&#124;/Hesaplatorservice.exe&#124;'.|  
|AppDomain|`xs:string`|AppDomain. CurrentDomain. FriendlyName tarafından döndürülen dize.|
