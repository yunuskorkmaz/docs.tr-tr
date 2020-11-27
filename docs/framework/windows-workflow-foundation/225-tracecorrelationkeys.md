---
title: 225 - TraceCorrelationKeys
ms.date: 03/30/2017
ms.assetid: d9083aaf-3816-4c1c-bae0-2d7f49628345
ms.openlocfilehash: 04c5e0f4fbf3b95485e5bf4aae53aa2e4912d893
ms.sourcegitcommit: bc293b14af795e0e999e3304dd40c0222cf2ffe4
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/26/2020
ms.locfileid: "96294501"
---
# <a name="225---tracecorrelationkeys"></a>225 - TraceCorrelationKeys

## <a name="properties"></a>Özellikler  
  
|||  
|-|-|  
|ID|225|  
|Anahtar sözcükler|Sorun giderme, ServiceModel|  
|Düzey|Bilgi|  
|Kanal|Microsoft-Windows-uygulama sunucusu-uygulamalar/analitik|  
  
## <a name="description"></a>Açıklama  

 Bu olay, bir iş akışı hizmeti için içerik tabanlı bağıntı kullanıldığında yayınlanır. Bir iletinin bir örneğe ilişkilendirilmesi için uygulanan bağıntı anahtarlarını içerir.  
  
## <a name="message"></a>İleti  

 ' %3 ' üst kapsamındaki ' %2 ' değerleri kullanılarak ' %1 ' bağıntı anahtarı hesaplandı.  
  
## <a name="details"></a>Ayrıntılar  
  
|Veri öğesi adı|Veri öğesi türü|Açıklama|  
|--------------------|--------------------|-----------------|  
|Örnek anahtarı|`xs:GUID`|Bağıntı değerlerinden oluşturulan anahtar.|  
|Değerler|`xs:string`|Bağıntı örneği anahtarını hesaplamak için kullanılan değerler.|  
|Üst kapsam|`xs:string`||  
|HostReference|`xs:string`|Web 'de barındırılan hizmetler için, bu alan hizmeti Web hiyerarşisinde benzersiz olarak tanımlar. Biçimi ' Web sitesi adı uygulama sanal yolu&#124;hizmet sanal yolu&#124;ServiceName ' olarak tanımlanmıştır. Örnek: ' Default Web site/Hesaplatooypplication&#124;/Hesaplatorservice.exe&#124;Hesaplatorservice '.|  
|AppDomain|`xs:string`|AppDomain. CurrentDomain. FriendlyName tarafından döndürülen dize.|
