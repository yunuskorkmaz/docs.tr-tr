---
title: 39456 - TrackingRecordDropped
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: da13d5bc-1736-47a4-b3fd-064ca8040326
caps.latest.revision: "2"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 592d7c0a3725dcb50f7911a198c9dc9b7199a0a8
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/22/2017
---
# <a name="39456---trackingrecorddropped"></a>39456 - TrackingRecordDropped
## <a name="properties"></a>Özellikler  
  
|||  
|-|-|  
|Kimlik|39456|  
|Anahtar Sözcükler|WFTracking|  
|Düzey|Uyarı|  
|Kanal|Microsoft Windows uygulaması sunucu-uygulamalar/hata ayıklama|  
  
## <a name="description"></a>Açıklama  
 ETW oturum sağlayıcı tarafından izin verilen en fazla boyut üst sınırını aştığı için bir izleme kaydını bırakıldı gösterir.  
  
## <a name="message"></a>İleti  
 %1 kaydı izleme ETW oturum tarafından %2 sağlayıcısı için izin verilen üst sınırı aşıyor  
  
## <a name="details"></a>Ayrıntılar  
  
|Veri öğesi adı|Veri öğesi türü|Açıklama|  
|--------------------|--------------------|-----------------|  
|Özel Durum|xs: String|Özel durum için özel durum ayrıntıları|  
|AppDomain|xs: String|AppDomain.CurrentDomain.FriendlyName tarafından döndürülen dize.|
