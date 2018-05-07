---
title: 57398 - MaxInstancesExceeded
ms.date: 03/30/2017
ms.assetid: f943d209-dfeb-43e5-b572-c9a06217936e
ms.openlocfilehash: d644c25ec2dee06eea4a5fb66c30792bb650f252
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
---
# <a name="57398---maxinstancesexceeded"></a>57398 - MaxInstancesExceeded
## <a name="properties"></a>Özellikler  
  
|||  
|-|-|  
|Kimlik|57398|  
|Anahtar Sözcükler|WFServices|  
|Düzey|Uyarı|  
|Kanal|Microsoft Windows uygulama sunucusu-uygulamalar/analitik|  
  
## <a name="description"></a>Açıklama  
 Sistem 'MaxConcurrentInstances' kısıtlama için ayarlanmış sınırına gösterir.  
  
## <a name="message"></a>İleti  
 Sistem 'MaxConcurrentInstances' kısıtlama için ayarladığı sınırına ulaştı. Bu kısıtlama için sınır %1'e ayarlandı. Kısıtlama değeri özniteliği 'maxConcurrentInstances' serviceThrottle öğesindeki değiştirerek veya 'MaxConcurrentInstances' özelliği davranışına ServiceThrottlingBehavior'dan değiştirilerek değiştirilebilir.  
  
## <a name="details"></a>Ayrıntılar  
  
|Veri öğesi adı|Veri öğesi türü|Açıklama|  
|--------------------|--------------------|-----------------|  
|Ad|xs: String|Öğenin adı.|  
|AppDomain|xs: String|AppDomain.CurrentDomain.FriendlyName tarafından döndürülen dize.|
