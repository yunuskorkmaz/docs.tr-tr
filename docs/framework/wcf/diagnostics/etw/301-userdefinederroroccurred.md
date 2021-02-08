---
description: 'Hakkında daha fazla bilgi edinin: 301-UserDefinedErrorOccurred'
title: 301 - UserDefinedErrorOccurred
ms.date: 03/30/2017
ms.assetid: a0285d1c-550f-4c14-9c36-a96e97f1c4e4
ms.openlocfilehash: 15e12bb27e3626f80747498a1387aa90fc461d28
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99794253"
---
# <a name="301---userdefinederroroccurred"></a>301 - UserDefinedErrorOccurred

## <a name="properties"></a>Özellikler  
  
|||  
|-|-|  
|ID|301|  
|Anahtar sözcükler|Sorun giderme, HealthMonitoring, UserEvents, ServiceModel, EndToEndMonitoring|  
|Level|Hata|  
|Kanal|Microsoft-Windows-uygulama sunucusu-uygulamalar/analitik|  
  
## <a name="description"></a>Description  

 Bu olay kullanıcı kodundan yayınlanır. Geliştiriciler, hizmetinde özel olarak tanımlanan bir hata oluştuğunda bu olayı oluşturabilir. Bu, API 'ler kullanılarak yapılabilir <xref:System.Diagnostics.Eventing> . Ayrıca, bu API 'YI sarmalayan ve bu olayı doğru şekilde nasıl yayılacağını gösteren bir WCF örneği vardır.  
  
## <a name="message"></a>İleti  

 Ad: ' %1 ', başvuru: ' %2 ', yük: %3  
  
## <a name="details"></a>Ayrıntılar  
  
|Veri öğesi adı|Veri öğesi türü|Açıklama|  
|--------------------|--------------------|-----------------|  
|Ad|`xs:string`|Etkinliğin Kullanıcı tanımlı adı.|  
|HostReference|`xs:string`|Web 'de barındırılan hizmetler için, bu alan hizmeti Web hiyerarşisinde benzersiz olarak tanımlar. Biçimi ' Web sitesi adı uygulama sanal yolu&#124;hizmet sanal yolu&#124;ServiceName ' olarak tanımlanmıştır. Örnek: ' Default Web site/Hesaplatooypplication&#124;/Hesaplatorservice.exe&#124;Hesaplatorservice '.|  
|Te|`xs:string`|Etkinliğin Kullanıcı tanımlı yükü.|
