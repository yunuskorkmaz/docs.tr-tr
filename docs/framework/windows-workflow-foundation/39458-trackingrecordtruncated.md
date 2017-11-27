---
title: 39458 - TrackingRecordTruncated
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 5352f0eb-d571-454a-bab5-e2162888b218
caps.latest.revision: "2"
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: ecf18d6d751edd47dbeca7d2e5f4491892e41e6d
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/18/2017
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
