---
title: 57398 - MaxInstancesExceeded
ms.date: 03/30/2017
ms.assetid: f943d209-dfeb-43e5-b572-c9a06217936e
ms.openlocfilehash: bd490aad24fba4550bc778799cd6f836dcfd466c
ms.sourcegitcommit: bc293b14af795e0e999e3304dd40c0222cf2ffe4
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/26/2020
ms.locfileid: "96289184"
---
# <a name="57398---maxinstancesexceeded"></a>57398 - MaxInstancesExceeded

## <a name="properties"></a>Özellikler  
  
|||  
|-|-|  
|ID|57398|  
|Anahtar sözcükler|WFServices|  
|Düzey|Uyarı|  
|Kanal|Microsoft-Windows-uygulama sunucusu-uygulamalar/analitik|  
  
## <a name="description"></a>Açıklama  

 Sistem kısıtlama ' MaxConcurrentInstances ' için ayarlanan sınıra ulaştı.  
  
## <a name="message"></a>İleti  

 Sistem kısıtlama ' MaxConcurrentInstances ' için belirlenen sınıra ulaştı. Bu kısıtlama için sınır %1 olarak ayarlandı. ' MaxConcurrentInstances ' özniteliği Servicekısıtlaması öğesinde değiştirilerek veya Behavior Servicekısıtlar Lingbehavior üzerinde ' MaxConcurrentInstances ' özelliği değiştirilerek kısıtlama değeri değiştirilebilir.  
  
## <a name="details"></a>Ayrıntılar  
  
|Veri öğesi adı|Veri öğesi türü|Açıklama|  
|--------------------|--------------------|-----------------|  
|Ad|xs: String|Öğenin adı.|  
|AppDomain|xs: String|AppDomain. CurrentDomain. FriendlyName tarafından döndürülen dize.|
