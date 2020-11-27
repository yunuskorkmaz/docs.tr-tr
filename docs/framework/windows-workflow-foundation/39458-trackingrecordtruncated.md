---
title: 39458 - TrackingRecordTruncated
ms.date: 03/30/2017
ms.assetid: 5352f0eb-d571-454a-bab5-e2162888b218
ms.openlocfilehash: f02a34673c51be6e0b127a64e4622131575d836f
ms.sourcegitcommit: bc293b14af795e0e999e3304dd40c0222cf2ffe4
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/26/2020
ms.locfileid: "96275898"
---
# <a name="39458---trackingrecordtruncated"></a>39458 - TrackingRecordTruncated

## <a name="properties"></a>Özellikler  
  
|||  
|-|-|  
|ID|39458|  
|Anahtar sözcükler|WFTracking|  
|Düzey|Uyarı|  
|Kanal|Microsoft-Windows-Application Server-uygulamalar/hata ayıkla|  
  
## <a name="description"></a>Açıklama  

 Bir izleme kaydının kesildiğini gösterir. Değişkenler/ek açıklamalar/Kullanıcı verileri kaldırıldı.  
  
## <a name="message"></a>İleti  

 %2 sağlayıcısı ile ETW oturumuna yazılan %1 izleme kaydı kesilmiş. Değişkenler/ek açıklamalar/Kullanıcı verileri kaldırıldı  
  
## <a name="details"></a>Ayrıntılar  
  
|Veri öğesi adı|Veri öğesi türü|Açıklama|  
|--------------------|--------------------|-----------------|  
|RecordNumber|xs: String|İzleme kayıt numarası.|  
|Kimliği|xs: String|ETW sağlayıcı kimliği.|  
|AppDomain|xs: String|AppDomain. CurrentDomain. FriendlyName tarafından döndürülen dize.|
