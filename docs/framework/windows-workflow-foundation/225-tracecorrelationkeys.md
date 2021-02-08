---
description: 'Hakkında daha fazla bilgi edinin: 225-Trackaydedilmiş Ilişki anahtarları'
title: 225 - TraceCorrelationKeys
ms.date: 03/30/2017
ms.assetid: d9083aaf-3816-4c1c-bae0-2d7f49628345
ms.openlocfilehash: c5fdb9305815cdc4df6bbae3e54209d2b5cffd9d
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99778119"
---
# <a name="225---tracecorrelationkeys"></a>225 - TraceCorrelationKeys

## <a name="properties"></a>Özellikler  
  
|||  
|-|-|  
|ID|225|  
|Anahtar sözcükler|Sorun giderme, ServiceModel|  
|Level|Bilgi|  
|Kanal|Microsoft-Windows-uygulama sunucusu-uygulamalar/analitik|  
  
## <a name="description"></a>Description  

 Bu olay, bir iş akışı hizmeti için içerik tabanlı bağıntı kullanıldığında yayınlanır. Bir iletinin bir örneğe ilişkilendirilmesi için uygulanan bağıntı anahtarlarını içerir.  
  
## <a name="message"></a>İleti  

 ' %3 ' üst kapsamındaki ' %2 ' değerleri kullanılarak ' %1 ' bağıntı anahtarı hesaplandı.  
  
## <a name="details"></a>Ayrıntılar  
  
|Veri öğesi adı|Veri öğesi türü|Description|  
|--------------------|--------------------|-----------------|  
|Örnek anahtarı|`xs:GUID`|Bağıntı değerlerinden oluşturulan anahtar.|  
|Değerler|`xs:string`|Bağıntı örneği anahtarını hesaplamak için kullanılan değerler.|  
|Üst kapsam|`xs:string`||  
|HostReference|`xs:string`|Web 'de barındırılan hizmetler için, bu alan hizmeti Web hiyerarşisinde benzersiz olarak tanımlar. Biçimi ' Web sitesi adı uygulama sanal yolu&#124;hizmet sanal yolu&#124;ServiceName ' olarak tanımlanmıştır. Örnek: ' Default Web site/Hesaplatooypplication&#124;/Hesaplatorservice.exe&#124;Hesaplatorservice '.|  
|AppDomain|`xs:string`|AppDomain. CurrentDomain. FriendlyName tarafından döndürülen dize.|
