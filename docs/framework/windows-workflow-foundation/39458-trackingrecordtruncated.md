---
title: 39458 - TrackingRecordTruncated
ms.date: 03/30/2017
ms.assetid: 5352f0eb-d571-454a-bab5-e2162888b218
ms.openlocfilehash: 416feb4073b31178b016ae72c9cd85e15c4a68c3
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
---
# <a name="39458---trackingrecordtruncated"></a>39458 - TrackingRecordTruncated
## <a name="properties"></a>Özellikler  
  
|||  
|-|-|  
|Kimlik|39458|  
|Anahtar Sözcükler|WFTracking|  
|Düzey|Uyarı|  
|Kanal|Microsoft Windows uygulaması sunucu-uygulamalar/hata ayıklama|  
  
## <a name="description"></a>Açıklama  
 Bir izleme kaydını kesildi gösterir. Ek açıklamalar/değişkenleri/kullanıcı verileri kaldırılmıştır.  
  
## <a name="message"></a>İleti  
 ETW oturumuna %2 sağlayıcısı ile yazılmış %1 kaydı İzleme kesildi. Ek açıklamalar/değişkenleri/kullanıcı verilerini kaldırıldı  
  
## <a name="details"></a>Ayrıntılar  
  
|Veri öğesi adı|Veri öğesi türü|Açıklama|  
|--------------------|--------------------|-----------------|  
|Kayıt numarası|xs: String|İzleme kayıt numarası.|  
|ProviderID|xs: String|ETW sağlayıcı kimliği.|  
|AppDomain|xs: String|AppDomain.CurrentDomain.FriendlyName tarafından döndürülen dize.|
