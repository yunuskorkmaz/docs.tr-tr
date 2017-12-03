---
title: 57398 - MaxInstancesExceeded
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: f943d209-dfeb-43e5-b572-c9a06217936e
caps.latest.revision: "2"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 803616fdd287491afa27d3ac23dfce99c5db08ca
ms.sourcegitcommit: ce279f2d7fe2220e6ea0a25a8a7a5370ddf8d9f0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/02/2017
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
