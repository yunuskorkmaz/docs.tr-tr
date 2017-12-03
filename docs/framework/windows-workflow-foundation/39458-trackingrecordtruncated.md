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
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 1d2bc07cff75fce7ddb50da9f54d161d7f235cab
ms.sourcegitcommit: ce279f2d7fe2220e6ea0a25a8a7a5370ddf8d9f0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/02/2017
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
