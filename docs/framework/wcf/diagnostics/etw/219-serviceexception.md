---
description: 'Hakkında daha fazla bilgi edinin: 219-ServiceException'
title: 219 - ServiceException
ms.date: 03/30/2017
ms.assetid: 81e2efac-39aa-4ed2-85a9-97eb8793b844
ms.openlocfilehash: b2ac12d6c5c68517b085b39dd7d0f81c39db9ebd
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99794331"
---
# <a name="219---serviceexception"></a>219 - ServiceException

## <a name="properties"></a>Özellikler  
  
|||  
|-|-|  
|ID|219|  
|Anahtar sözcükler|EndToEndMonitoring, HealthMonitoring, sorun giderme, ServiceModel|  
|Level|Hata|  
|Kanal|Microsoft-Windows-uygulama sunucusu-uygulamalar/analitik|  
  
## <a name="description"></a>Description  

 Bu olay, bir WCF hizmeti işlenmeyen bir özel durumla karşılaştığında yayınlanır. Bu, etkinleştirme sırasında, ileti işleme sırasında ve Kullanıcı kodunda işlenmeyen özel durumları içerir.  
  
## <a name="message"></a>İleti  

 İleti işleme sırasında ' %2 ' türünde işlenmeyen bir özel durum oluştu. Tam özel durum ToString: %1.  
  
## <a name="details"></a>Ayrıntılar  
  
|Veri öğesi adı|Veri öğesi türü|Description|  
|--------------------|--------------------|-----------------|  
|ExceptionToString|`xs:string`|`ToString`Clr özel durumuyla () çağırmanın sonucu.|  
|ExceptionTypeName|`xs:string`|Özel durum türünün CLR FullName değeri.|  
|HostReference|`xs:string`|Web 'de barındırılan hizmetler için, bu alan hizmeti Web hiyerarşisinde benzersiz olarak tanımlar. Biçimi ' Web sitesi adı uygulama sanal yolu&#124;hizmet sanal yolu&#124;ServiceName ' olarak tanımlanmıştır. Örnek: ' Default Web site/Hesaplatooypplication&#124;/Hesaplatorservice.exe&#124;Hesaplatorservice '.|  
|AppDomain|`xs:string`|AppDomain. CurrentDomain. FriendlyName tarafından döndürülen dize.|
