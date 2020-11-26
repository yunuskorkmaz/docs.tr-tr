---
title: 302 - UserDefinedWarningOccurred
ms.date: 03/30/2017
ms.assetid: 8d1f0bf1-0151-45e6-be92-573d397b54de
ms.openlocfilehash: b942b2e9716713371b8679fc9df9b9634dfc7283
ms.sourcegitcommit: bc293b14af795e0e999e3304dd40c0222cf2ffe4
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/26/2020
ms.locfileid: "96243449"
---
# <a name="302---userdefinedwarningoccurred"></a>302 - UserDefinedWarningOccurred

## <a name="properties"></a>Özellikler  
  
|||  
|-|-|  
|ID|302|  
|Anahtar sözcükler|Sorun giderme, HealthMonitoring, UserEvents, ServiceModel, EndToEndMonitoring|  
|Düzey|Uyarı|  
|Kanal|Microsoft-Windows-uygulama sunucusu-uygulamalar/analitik|  
  
## <a name="description"></a>Açıklama  

 Bu olay kullanıcı kodundan yayınlanır. Geliştiriciler, hizmetinde özel tanımlanmış bir uyarı olayı oluştuğunda bu olayı oluşturabilir. Bu, API 'ler kullanılarak yapılabilir <xref:System.Diagnostics.Eventing> . Ayrıca, bu API 'YI sarmalayan ve bu olayı doğru şekilde nasıl yayılacağını gösteren bir WCF örneği vardır.  
  
## <a name="message"></a>İleti  

 Ad: ' %1 ', başvuru: ' %2 ', yük: %3  
  
## <a name="details"></a>Ayrıntılar  
  
|Veri öğesi adı|Veri öğesi türü|Açıklama|  
|--------------------|--------------------|-----------------|  
|Ad|`xs:string`|Etkinliğin Kullanıcı tanımlı adı.|  
|HostReference|`xs:string`|Web 'de barındırılan hizmetler için, bu alan hizmeti Web hiyerarşisinde benzersiz olarak tanımlar. Biçimi ' Web sitesi adı uygulama sanal yolu&#124;hizmet sanal yolu&#124;ServiceName ' olarak tanımlanmıştır. Örnek: ' Default Web site/Hesaplatooypplication&#124;/Hesaplatorservice.exe&#124;Hesaplatorservice '.|  
|Te|`xs:string`|Etkinliğin Kullanıcı tanımlı yükü.|
