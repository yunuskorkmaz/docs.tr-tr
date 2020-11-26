---
title: 219 - ServiceException
ms.date: 03/30/2017
ms.assetid: 81e2efac-39aa-4ed2-85a9-97eb8793b844
ms.openlocfilehash: 832ced406b6079fad8f4b9bea512a6d390bdcc0f
ms.sourcegitcommit: bc293b14af795e0e999e3304dd40c0222cf2ffe4
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/26/2020
ms.locfileid: "96241947"
---
# <a name="219---serviceexception"></a>219 - ServiceException

## <a name="properties"></a>Özellikler  
  
|||  
|-|-|  
|ID|219|  
|Anahtar sözcükler|EndToEndMonitoring, HealthMonitoring, sorun giderme, ServiceModel|  
|Düzey|Hata|  
|Kanal|Microsoft-Windows-uygulama sunucusu-uygulamalar/analitik|  
  
## <a name="description"></a>Açıklama  

 Bu olay, bir WCF hizmeti işlenmeyen bir özel durumla karşılaştığında yayınlanır. Bu, etkinleştirme sırasında, ileti işleme sırasında ve Kullanıcı kodunda işlenmeyen özel durumları içerir.  
  
## <a name="message"></a>İleti  

 İleti işleme sırasında ' %2 ' türünde işlenmeyen bir özel durum oluştu. Tam özel durum ToString: %1.  
  
## <a name="details"></a>Ayrıntılar  
  
|Veri öğesi adı|Veri öğesi türü|Açıklama|  
|--------------------|--------------------|-----------------|  
|ExceptionToString|`xs:string`|`ToString`Clr özel durumuyla () çağırmanın sonucu.|  
|ExceptionTypeName|`xs:string`|Özel durum türünün CLR FullName değeri.|  
|HostReference|`xs:string`|Web 'de barındırılan hizmetler için, bu alan hizmeti Web hiyerarşisinde benzersiz olarak tanımlar. Biçimi ' Web sitesi adı uygulama sanal yolu&#124;hizmet sanal yolu&#124;ServiceName ' olarak tanımlanmıştır. Örnek: ' Default Web site/Hesaplatooypplication&#124;/Hesaplatorservice.exe&#124;Hesaplatorservice '.|  
|AppDomain|`xs:string`|AppDomain. CurrentDomain. FriendlyName tarafından döndürülen dize.|
