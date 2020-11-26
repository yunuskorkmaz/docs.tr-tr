---
title: 303 - UserDefinedInformationEventOccured
ms.date: 03/30/2017
ms.assetid: 5ed5acaf-3755-4417-92c4-4ebc8e854ca1
ms.openlocfilehash: 8597d84184caea9fc5dc7778cfc6d05e7dc592db
ms.sourcegitcommit: bc293b14af795e0e999e3304dd40c0222cf2ffe4
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/26/2020
ms.locfileid: "96243436"
---
# <a name="303---userdefinedinformationeventoccured"></a>303 - UserDefinedInformationEventOccured

## <a name="properties"></a>Özellikler  
  
|||  
|-|-|  
|ID|303|  
|Anahtar sözcükler|Sorun giderme, HealthMonitoring, UserEvents, ServiceModel, EndToEndMonitoring|  
|Düzey|Bilgi|  
|Kanal|Microsoft-Windows-uygulama sunucusu-uygulamalar/analitik|  
  
## <a name="description"></a>Açıklama  

 Bu olay kullanıcı kodundan yayınlanır. Geliştiriciler, hizmetinde özel tanımlanmış bilgilendirici bir olay gerçekleştiğinde bu olayı oluşturabilir. Bu, API 'ler kullanılarak yapılabilir <xref:System.Diagnostics.Eventing> . Ayrıca, bu API 'YI sarmalayan ve bu olayı doğru şekilde nasıl yayılacağını gösteren bir WCF örneği vardır.  
  
## <a name="message"></a>İleti  

 Ad: ' %1 ', başvuru: ' %2 ', yük: %3  
  
## <a name="details"></a>Ayrıntılar  
  
|Veri öğesi adı|Veri öğesi türü|Açıklama|  
|--------------------|--------------------|-----------------|  
|Ad|`xs:string`|Etkinliğin Kullanıcı tanımlı adı|  
|HostReference|`xs:string`|Web 'de barındırılan hizmetler için, bu alan hizmeti Web hiyerarşisinde benzersiz olarak tanımlar. Biçimi ' Web sitesi adı uygulama sanal yolu&#124;hizmet sanal yolu&#124;ServiceName ' olarak tanımlanmıştır. Örnek: ' Default Web site/Hesaplatooypplication&#124;/Hesaplatorservice.exe&#124;Hesaplatorservice '.|  
|Te|`xs:string`|Etkinliğin Kullanıcı tanımlı yükü.|
