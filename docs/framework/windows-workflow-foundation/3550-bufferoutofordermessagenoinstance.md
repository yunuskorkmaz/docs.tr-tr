---
title: 3550 - BufferOutOfOrderMessageNoInstance
ms.date: 03/30/2017
ms.assetid: 1299d294-99b8-430e-98b1-55f5f17002f3
ms.openlocfilehash: 61605d666911cce277bcebbb0a2f803e9a5dcfeb
ms.sourcegitcommit: bc293b14af795e0e999e3304dd40c0222cf2ffe4
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/26/2020
ms.locfileid: "96261312"
---
# <a name="3550---bufferoutofordermessagenoinstance"></a>3550 - BufferOutOfOrderMessageNoInstance

## <a name="properties"></a>Özellikler  
  
|||  
|-|-|  
|ID|3550|  
|Anahtar sözcükler|WFServices|  
|Düzey|Bilgi|  
|Kanal|Microsoft-Windows-uygulama sunucusu-uygulamalar/analitik|  
  
## <a name="description"></a>Açıklama  

 Arabelleğe alınan bir alma başarısız olduğunu gösterir. Hizmet örneği bu belirli işlemi işlemeye hazırsa işlem yeniden denenecek.  
  
## <a name="message"></a>İleti  

 ' %1 ' işlemi şu anda gerçekleştirilemiyor. Hizmet örneği bu işlemi işlemeye hazırsa başka bir girişim yapılacak.  
  
## <a name="details"></a>Ayrıntılar  
  
|Veri öğesi adı|Veri öğesi türü|Açıklama|  
|--------------------|--------------------|-----------------|  
|OperationName|xs: String|İşlemin adı.|  
|AppDomain|xs: String|AppDomain. CurrentDomain. FriendlyName tarafından döndürülen dize.|
