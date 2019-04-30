---
title: 39458 - TrackingRecordTruncated
ms.date: 03/30/2017
ms.assetid: 5352f0eb-d571-454a-bab5-e2162888b218
ms.openlocfilehash: 416feb4073b31178b016ae72c9cd85e15c4a68c3
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/23/2019
ms.locfileid: "61774419"
---
# <a name="39458---trackingrecordtruncated"></a>39458 - TrackingRecordTruncated
## <a name="properties"></a>Özellikler  
  
|||  
|-|-|  
|Kimlik|39458|  
|anahtar sözcükler|WFTracking|  
|Düzey|Uyarı|  
|Kanal|Microsoft Windows uygulaması sunucu-uygulamalar/hata ayıklama|  
  
## <a name="description"></a>Açıklama  
 Bir izleme kaydını kesildi gösterir. Ek açıklamalar/değişkenler/kullanıcı verileri kaldırılmıştır.  
  
## <a name="message"></a>İleti  
 %1 ETW oturumu %2 sağlayıcısı ile yazılmış kaydı İzleme kesildi. Veri ek açıklamaları/değişkenler/kullanıcı kaldırıldı  
  
## <a name="details"></a>Ayrıntılar  
  
|Veri öğesi adı|Veri öğesi türü|Açıklama|  
|--------------------|--------------------|-----------------|  
|Kayıt numarası|xs:string|İzleme kayıt numarası.|  
|ProviderID değeri|xs:string|ETW sağlayıcısı kimliği.|  
|AppDomain|xs:string|AppDomain.CurrentDomain.FriendlyName tarafından döndürülen dize.|
