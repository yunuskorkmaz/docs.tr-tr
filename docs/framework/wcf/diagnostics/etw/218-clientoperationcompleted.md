---
description: 'Hakkında daha fazla bilgi edinin: 218-Clienentoperationcompleted'
title: 218 - ClientOperationCompleted
ms.date: 03/30/2017
ms.assetid: b069bced-7bb2-4e01-8227-e5dbda17af09
ms.openlocfilehash: 3719b77ce653c5177cf7b92901ecd51982504b83
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99794344"
---
# <a name="218---clientoperationcompleted"></a>218 - ClientOperationCompleted

## <a name="properties"></a>Özellikler  
  
|||  
|-|-|  
|ID|218|  
|Anahtar sözcükler|Sorun giderme, ServiceModel|  
|Level|Bilgi|  
|Kanal|Microsoft-Windows-uygulama sunucusu-uygulamalar/analitik|  
  
## <a name="description"></a>Description  

 Bu olay, yalnızca bir işlem tamamlandıktan sonra istemciler tarafından yayılır. Tek yönlü işlemlerde bu, ileti başarıyla gönderildikten hemen sonra olur. İstek-yanıt işlemleri için, yanıt alındıktan sonra olur.  
  
## <a name="message"></a>İleti  

 Istemci, ' %2 ' sözleşmesiyle ilişkili ' %1 ' eylemini yürütmeyi tamamladı. İleti, ' %3 ' öğesine gönderildi.  
  
## <a name="details"></a>Ayrıntılar  
  
|Veri öğesi adı|Veri öğesi türü|Açıklama|  
|--------------------|--------------------|-----------------|  
|Eylem|xs: String|Giden iletinin SOAP eylem üst bilgisi.|  
|Sözleşme adı|`xs:string`|Sözleşmenin adı. Örnek: Icalbir.|  
|Hedef|`xs:string`|İletinin gönderildiği hizmet uç noktasının adresi.|  
|HostReference|`xs:string`|Web 'de barındırılan hizmetler için, bu alan hizmeti Web hiyerarşisinde benzersiz olarak tanımlar. Biçimi ' Web sitesi adı uygulama sanal yolu&#124;hizmet sanal yolu&#124;ServiceName ' olarak tanımlanmıştır. Örnek: ' Default Web site/Hesaplatooypplication&#124;/Hesaplatorservice.exe&#124;Hesaplatorservice '.|  
|AppDomain|`xs:string`|AppDomain. CurrentDomain. FriendlyName tarafından döndürülen dize.|
