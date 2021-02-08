---
description: 'Hakkında daha fazla bilgi edinin: 3551-BufferOutOfOrderMessageNoBookmark'
title: 3551 - BufferOutOfOrderMessageNoBookmark
ms.date: 03/30/2017
ms.assetid: 7930d6c4-c843-4a83-933a-cecd71b80d1e
ms.openlocfilehash: 573056fed1753ac55c51d9a074047e8eea15e229
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99778002"
---
# <a name="3551---bufferoutofordermessagenobookmark"></a>3551 - BufferOutOfOrderMessageNoBookmark

## <a name="properties"></a>Özellikler  
  
|||  
|-|-|  
|ID|3551|  
|Anahtar sözcükler|WFServices|  
|Level|Bilgi|  
|Kanal|Microsoft-Windows-uygulama sunucusu-uygulamalar/analitik|  
  
## <a name="description"></a>Description  

 Sürdürme yer işaretinin başarısız olduğunu gösterir. Hizmet örneği bu işlemi işlemeye hazırsa, arabelleğe alınmış alma işlemi yeniden denenecek.  
  
## <a name="message"></a>İleti  

 ' %1 ' hizmet örneğindeki ' %2 ' işlemi şu anda gerçekleştirilemiyor. Hizmet örneği bu işlemi işlemeye hazırsa başka bir girişim yapılacak.  
  
## <a name="details"></a>Ayrıntılar  
  
|Veri öğesi adı|Veri öğesi türü|Description|  
|--------------------|--------------------|-----------------|  
|OperationName|xs: String|İşlemin adı.|  
|ServiceInstanceId|xs: String|Hizmet örneğinin kimliği.|  
|AppDomain|xs: String|AppDomain. CurrentDomain. FriendlyName tarafından döndürülen dize.|
