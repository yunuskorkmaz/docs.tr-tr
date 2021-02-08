---
description: 'Hakkında daha fazla bilgi edinin: 302-Userdefinedwarningoluştu'
title: 302 - UserDefinedWarningOccurred
ms.date: 03/30/2017
ms.assetid: 8d1f0bf1-0151-45e6-be92-573d397b54de
ms.openlocfilehash: eb79e32d8993ec60c05e5aaaee1b5e15ee7e32e2
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99794227"
---
# <a name="302---userdefinedwarningoccurred"></a>302 - UserDefinedWarningOccurred

## <a name="properties"></a>Özellikler  
  
|||  
|-|-|  
|ID|302|  
|Anahtar sözcükler|Sorun giderme, HealthMonitoring, UserEvents, ServiceModel, EndToEndMonitoring|  
|Level|Uyarı|  
|Kanal|Microsoft-Windows-uygulama sunucusu-uygulamalar/analitik|  
  
## <a name="description"></a>Description  

 Bu olay kullanıcı kodundan yayınlanır. Geliştiriciler, hizmetinde özel tanımlanmış bir uyarı olayı oluştuğunda bu olayı oluşturabilir. Bu, API 'ler kullanılarak yapılabilir <xref:System.Diagnostics.Eventing> . Ayrıca, bu API 'YI sarmalayan ve bu olayı doğru şekilde nasıl yayılacağını gösteren bir WCF örneği vardır.  
  
## <a name="message"></a>İleti  

 Ad: ' %1 ', başvuru: ' %2 ', yük: %3  
  
## <a name="details"></a>Ayrıntılar  
  
|Veri öğesi adı|Veri öğesi türü|Açıklama|  
|--------------------|--------------------|-----------------|  
|Ad|`xs:string`|Etkinliğin Kullanıcı tanımlı adı.|  
|HostReference|`xs:string`|Web 'de barındırılan hizmetler için, bu alan hizmeti Web hiyerarşisinde benzersiz olarak tanımlar. Biçimi ' Web sitesi adı uygulama sanal yolu&#124;hizmet sanal yolu&#124;ServiceName ' olarak tanımlanmıştır. Örnek: ' Default Web site/Hesaplatooypplication&#124;/Hesaplatorservice.exe&#124;Hesaplatorservice '.|  
|Te|`xs:string`|Etkinliğin Kullanıcı tanımlı yükü.|
