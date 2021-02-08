---
description: 'Hakkında daha fazla bilgi edinin: 213-ServiceHostStarted'
title: 213 - ServiceHostStarted
ms.date: 03/30/2017
ms.assetid: a6f7facc-342f-46bb-9d52-a470178ba6bb
ms.openlocfilehash: 5e2b5b7c633ef053c449ad62c4f8fee40798a386
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99794422"
---
# <a name="213---servicehoststarted"></a>213 - ServiceHostStarted

## <a name="properties"></a>Özellikler  
  
|||  
|-|-|  
|ID|213|  
|Anahtar sözcükler|EndToEndMonitoring, HealthMonitoring, sorun giderme, ServiceHost|  
|Level|Günlüğe kaydetme her zaman|  
|Kanal|Microsoft-Windows-uygulama sunucusu-uygulamalar/analitik|  
  
## <a name="description"></a>Description  

 Bu olay, Web 'de barındırılan bir hizmet ana bilgisayarı başlatıldığında yayınlanır. Bu genellikle hizmet bir ileti tarafından etkinleştirildiğinde meydana gelir. Hizmet otomatik olarak başlatılacak şekilde yapılandırıldıysa da bu durum oluşabilir.  
  
## <a name="message"></a>İleti  

 ServiceHost başlatıldı: ' %1 '.  
  
## <a name="details"></a>Ayrıntılar  
  
|Veri öğesi adı|Veri öğesi türü|Description|  
|--------------------|--------------------|-----------------|  
|Hizmet türü adı|`xs:string`|Hizmet uygulamasının türünün CLR FullName.|  
|HostReference|`xs:string`|Web 'de barındırılan hizmetler için, bu alan hizmeti Web hiyerarşisinde benzersiz olarak tanımlar. Biçimi ' Web sitesi adı uygulama sanal yolu&#124;hizmet sanal yolu&#124;ServiceName ' olarak tanımlanmıştır. Örnek: ' Default Web site/Hesaplatooypplication&#124;/Hesaplatorservice.exe&#124;Hesaplatorservice '.|  
|AppDomain|`xs:string`|AppDomain. CurrentDomain. FriendlyName tarafından döndürülen dize.|
