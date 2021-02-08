---
description: 'Hakkında daha fazla bilgi edinin: 221-MessageReceivedFromTransport'
title: 221 - MessageReceivedFromTransport
ms.date: 03/30/2017
ms.assetid: 4995f0d5-c182-4d97-981f-6951da6df1fb
ms.openlocfilehash: 0cc15fa95ae321083afa2792810807971e909e6b
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99803509"
---
# <a name="221---messagereceivedfromtransport"></a>221 - MessageReceivedFromTransport

## <a name="properties"></a>Özellikler  
  
|||  
|-|-|  
|ID|221|  
|Anahtar sözcükler|EndToEndMonitoring, sorun giderme, ServiceModel|  
|Level|Bilgi|  
|Kanal|Microsoft-Windows-uygulama sunucusu-uygulamalar/analitik|  
  
## <a name="description"></a>Description  

 Bu olay, hizmet modeli aktarımdan bir ileti aldığında yayınlanır.  
  
## <a name="message"></a>İleti  

 Dağıtıcı aktarımdan bir ileti aldı. Bağıntı KIMLIĞI = = ' %1 '.  
  
## <a name="details"></a>Ayrıntılar  
  
|Veri öğesi adı|Veri öğesi türü|Description|  
|--------------------|--------------------|-----------------|  
|Bağıntı Kimliği|`xs:GUID`|`MessageSentToTransport`Bir hizmet veya istemciden bir olayı diğer uçta karşılık gelen bir olay ile ilişkilendirmek için kullanılan etkınlık kimliği `MessageReceivedFromTransport` .|  
|HostReference|`xs:string`|Web 'de barındırılan hizmetler için, bu alan hizmeti Web hiyerarşisinde benzersiz olarak tanımlar. Biçimi ' Web sitesi adı uygulama sanal yolu&#124;hizmet sanal yolu&#124;ServiceName ' olarak tanımlanmıştır. Örnek: ' Default Web site/Hesaplatooypplication&#124;/Hesaplatorservice.exe&#124;Hesaplatorservice '.|  
|AppDomain|`xs:string`|AppDomain. CurrentDomain. FriendlyName tarafından döndürülen dize.|
