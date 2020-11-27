---
title: 3551 - BufferOutOfOrderMessageNoBookmark
ms.date: 03/30/2017
ms.assetid: 7930d6c4-c843-4a83-933a-cecd71b80d1e
ms.openlocfilehash: 5e6a5f9d21435fee8309bd222443407e50ec2cee
ms.sourcegitcommit: bc293b14af795e0e999e3304dd40c0222cf2ffe4
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/26/2020
ms.locfileid: "96263613"
---
# <a name="3551---bufferoutofordermessagenobookmark"></a>3551 - BufferOutOfOrderMessageNoBookmark

## <a name="properties"></a>Özellikler  
  
|||  
|-|-|  
|ID|3551|  
|Anahtar sözcükler|WFServices|  
|Düzey|Bilgi|  
|Kanal|Microsoft-Windows-uygulama sunucusu-uygulamalar/analitik|  
  
## <a name="description"></a>Açıklama  

 Sürdürme yer işaretinin başarısız olduğunu gösterir. Hizmet örneği bu işlemi işlemeye hazırsa, arabelleğe alınmış alma işlemi yeniden denenecek.  
  
## <a name="message"></a>İleti  

 ' %1 ' hizmet örneğindeki ' %2 ' işlemi şu anda gerçekleştirilemiyor. Hizmet örneği bu işlemi işlemeye hazırsa başka bir girişim yapılacak.  
  
## <a name="details"></a>Ayrıntılar  
  
|Veri öğesi adı|Veri öğesi türü|Açıklama|  
|--------------------|--------------------|-----------------|  
|OperationName|xs: String|İşlemin adı.|  
|ServiceInstanceId|xs: String|Hizmet örneğinin kimliği.|  
|AppDomain|xs: String|AppDomain. CurrentDomain. FriendlyName tarafından döndürülen dize.|
