---
title: 217 - ClientOperationPrepared
ms.date: 03/30/2017
ms.assetid: ad207f04-b038-4f33-95e9-27a361df8ecd
ms.openlocfilehash: e8aaf65bdff0718e932d07937e052541b7134f11
ms.sourcegitcommit: bc293b14af795e0e999e3304dd40c0222cf2ffe4
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/26/2020
ms.locfileid: "96278888"
---
# <a name="217---clientoperationprepared"></a>217 - ClientOperationPrepared

## <a name="properties"></a>Özellikler  
  
|||  
|-|-|  
|ID|217|  
|Anahtar sözcükler|Sorun giderme, ServiceModel|  
|Düzey|Bilgi|  
|Kanal|Microsoft-Windows-uygulama sunucusu-uygulamalar/analitik|  
  
## <a name="description"></a>Açıklama  

 Bu olay, yalnızca bir işlem hizmete gönderilmeden önce istemciler tarafından yayılır.  
  
## <a name="message"></a>İleti  

 Istemci, ' %2 ' sözleşmesiyle ilişkili ' %1 ' eylemini yürütüyor. İleti, ' %3 ' öğesine gönderilecek.  
  
## <a name="details"></a>Ayrıntılar  
  
|Veri öğesi adı|Veri öğesi türü|Açıklama|  
|--------------------|--------------------|-----------------|  
|Eylem|`xs:string`|Giden iletinin SOAP eylem üst bilgisi.|  
|Sözleşme adı|`xs:string`|Sözleşmenin adı. Örnek: Icalbir.|  
|Hedef|`xs:string`|İletinin gönderildiği hizmet uç noktasının adresi.|  
|HostReference|`xs:string`|Web 'de barındırılan hizmetler için, bu alan hizmeti Web hiyerarşisinde benzersiz olarak tanımlar. Biçimi ' Web sitesi adı uygulama sanal yolu&#124;hizmet sanal yolu&#124;ServiceName ' olarak tanımlanmıştır. Örnek: ' Default Web site/Hesaplatooypplication&#124;/Hesaplatorservice.exe&#124;Hesaplatorservice '.|  
|AppDomain|`xs:string`|AppDomain. CurrentDomain. FriendlyName tarafından döndürülen dize.|
