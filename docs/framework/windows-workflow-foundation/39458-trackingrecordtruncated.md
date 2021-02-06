---
description: 'Hakkında daha fazla bilgi edinin: 39458-Trackingrecordkesildi'
title: 39458 - TrackingRecordTruncated
ms.date: 03/30/2017
ms.assetid: 5352f0eb-d571-454a-bab5-e2162888b218
ms.openlocfilehash: bb9a46dc5bd9bc4f4709a740dd0e7ec47ca826e3
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99631287"
---
# <a name="39458---trackingrecordtruncated"></a>39458 - TrackingRecordTruncated

## <a name="properties"></a>Özellikler  
  
|||  
|-|-|  
|ID|39458|  
|Anahtar sözcükler|WFTracking|  
|Level|Uyarı|  
|Kanal|Microsoft-Windows-Application Server-uygulamalar/hata ayıkla|  
  
## <a name="description"></a>Description  

 Bir izleme kaydının kesildiğini gösterir. Değişkenler/ek açıklamalar/Kullanıcı verileri kaldırıldı.  
  
## <a name="message"></a>İleti  

 %2 sağlayıcısı ile ETW oturumuna yazılan %1 izleme kaydı kesilmiş. Değişkenler/ek açıklamalar/Kullanıcı verileri kaldırıldı  
  
## <a name="details"></a>Ayrıntılar  
  
|Veri öğesi adı|Veri öğesi türü|Description|  
|--------------------|--------------------|-----------------|  
|RecordNumber|xs: String|İzleme kayıt numarası.|  
|Kimliği|xs: String|ETW sağlayıcı kimliği.|  
|AppDomain|xs: String|AppDomain. CurrentDomain. FriendlyName tarafından döndürülen dize.|
