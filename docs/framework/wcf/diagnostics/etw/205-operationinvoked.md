---
title: 205 - OperationInvoked
ms.date: 03/30/2017
ms.assetid: 9c8d6c90-dfa5-4ae0-a589-96679a8fb3ba
ms.openlocfilehash: c36294a4a430c3e372e8213246e85dba45ce03c8
ms.sourcegitcommit: bc293b14af795e0e999e3304dd40c0222cf2ffe4
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/26/2020
ms.locfileid: "96286025"
---
# <a name="205---operationinvoked"></a>205 - OperationInvoked

## <a name="properties"></a>Özellikler  
  
|||  
|-|-|  
|ID|205|  
|Anahtar sözcükler|Sorun giderme, ServiceModel|  
|Düzey|Bilgi|  
|Kanal|Microsoft-Windows-uygulama sunucusu-uygulamalar/analitik|  
  
## <a name="description"></a>Açıklama  

 Bu olay, hizmet modeli varsayılanı `OperationInvoker` bir yönteme çağrı yapmaya başlamadan hemen önce yayınlanır.  
  
## <a name="message"></a>İleti  

 Bir OperationInvoker ' %1 ' metodunu çağırdı. Çağıran bilgileri: ' %2 '.  
  
## <a name="details"></a>Ayrıntılar  
  
|Veri öğesi adı|Veri öğesi türü|Açıklama|  
|--------------------|--------------------|-----------------|  
|Yöntem adı|`xs:string`|Tarafından çağrılan metodun CLR adı `OperationInvoker` .|  
|Arayan Bilgileri|`xs:string`|İstemcinin IP adresi ve bağlantı noktası numarası ' IPAddress: bağlantınoktasınumarası ' biçiminde. İki değer, işlem bağlamı içindeki ' System. ServiceModel. Channels. RemoteEndpointMessageProperty ' ileti özelliğinden alınır. TCP olmayan bağlamalar için bu değeri unutmayın `null` .|  
|HostReference|`xs:string`|Web 'de barındırılan hizmetler için, bu alan hizmeti Web hiyerarşisinde benzersiz olarak tanımlar. Biçimi ' Web sitesi adı uygulama sanal yolu&#124;hizmet sanal yolu&#124;ServiceName ' olarak tanımlanmıştır. Örnek: ' Default Web site/Hesaplatooypplication&#124;/Hesaplatorservice.exe&#124;Hesaplatorservice '.|  
|AppDomain|`xs:string`|AppDomain. CurrentDomain. FriendlyName tarafından döndürülen dize.|
