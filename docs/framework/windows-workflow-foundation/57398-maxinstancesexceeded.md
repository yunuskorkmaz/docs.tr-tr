---
title: 57398 - MaxInstancesExceeded
ms.date: 03/30/2017
ms.assetid: f943d209-dfeb-43e5-b572-c9a06217936e
ms.openlocfilehash: d644c25ec2dee06eea4a5fb66c30792bb650f252
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/23/2019
ms.locfileid: "61945970"
---
# <a name="57398---maxinstancesexceeded"></a>57398 - MaxInstancesExceeded
## <a name="properties"></a>Özellikler  
  
|||  
|-|-|  
|Kimlik|57398|  
|anahtar sözcükler|WFServices|  
|Düzey|Uyarı|  
|Kanal|Microsoft Windows uygulama sunucusu-uygulamalar/analitik|  
  
## <a name="description"></a>Açıklama  
 Sistem sınırını 'MaxConcurrentInstances' kısıtlama için isabet gösterir.  
  
## <a name="message"></a>İleti  
 Sistem sınırını 'MaxConcurrentInstances' kısıtlama için basın. Bu kısıtlama için sınır %1'e ayarlanmıştır. Kısıtlama değeri öznitelik 'maxConcurrentInstances' serviceThrottle öğesinde değiştirerek veya davranışını denetlemek ServiceThrottlingBehavior 'MaxConcurrentInstances' özelliğini değiştirerek değiştirilebilir.  
  
## <a name="details"></a>Ayrıntılar  
  
|Veri öğesi adı|Veri öğesi türü|Açıklama|  
|--------------------|--------------------|-----------------|  
|Ad|xs:string|Öğe adı.|  
|AppDomain|xs:string|AppDomain.CurrentDomain.FriendlyName tarafından döndürülen dize.|
