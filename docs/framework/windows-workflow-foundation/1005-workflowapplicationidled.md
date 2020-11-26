---
title: 1005 - WorkflowApplicationIdled
ms.date: 03/30/2017
ms.assetid: 74d77dfa-f20d-4fe9-a6ae-e6d1b5fe4182
ms.openlocfilehash: 3b7210246b7fb754145c8aa6128da3183cea9f91
ms.sourcegitcommit: bc293b14af795e0e999e3304dd40c0222cf2ffe4
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/26/2020
ms.locfileid: "96239867"
---
# <a name="1005---workflowapplicationidled"></a>1005 - WorkflowApplicationIdled

## <a name="properties"></a>Özellikler  
  
|||  
|-|-|  
|ID|1005|  
|Anahtar sözcükler|WFRuntime|  
|Düzey|Bilgi|  
|Kanal|Microsoft-Windows-Application Server-uygulamalar/hata ayıkla|  
  
## <a name="description"></a>Açıklama  

 Bir iş akışı uygulamasının ıdlenmiş olduğunu gösterir.  
  
## <a name="message"></a>İleti  

 WorkflowApplication kimliği: ' %1 ' boşta oldu.  
  
## <a name="details"></a>Ayrıntılar  
  
|Veri öğesi adı|Veri öğesi türü|Açıklama|  
|--------------------|--------------------|-----------------|  
|WorkflowInstanceId|`xs:string`|İş akışı uygulama kimliği|  
|AppDomain|`xs:string`|AppDomain. CurrentDomain. FriendlyName tarafından döndürülen dize.|
