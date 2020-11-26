---
title: 1003 - WorkflowInstanceCanceled
ms.date: 03/30/2017
ms.assetid: 64754dc2-c160-4bf3-869a-13d56694e2dc
ms.openlocfilehash: bd8abf173ab6588d4a35ba59c6cd14fb53445e9f
ms.sourcegitcommit: bc293b14af795e0e999e3304dd40c0222cf2ffe4
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/26/2020
ms.locfileid: "96239906"
---
# <a name="1003---workflowinstancecanceled"></a>1003 - WorkflowInstanceCanceled

## <a name="properties"></a>Özellikler  
  
|||  
|-|-|  
|ID|1003|  
|Anahtar sözcükler|WFRuntime|  
|Düzey|Bilgi|  
|Kanal|Microsoft-Windows-Application Server-uygulamalar/hata ayıkla|  
  
## <a name="description"></a>Açıklama  

 Iptal edilen durumda bir iş akışı örneğinin tamamlandığını gösterir.  
  
## <a name="message"></a>İleti  

 WorkflowInstance kimliği: ' %1 ' Iptal edildi durumunda tamamlandı.  
  
## <a name="details"></a>Ayrıntılar  
  
|Veri öğesi adı|Veri öğesi türü|Açıklama|  
|--------------------|--------------------|-----------------|  
|WorkflowInstanceId|`xs:string`|İş akışının örnek kimliği|  
|AppDomain|`xs:string`|AppDomain. CurrentDomain. FriendlyName tarafından döndürülen dize.|
