---
title: 1001 - WorkflowApplicationCompleted
ms.date: 03/30/2017
ms.assetid: 7a2ab59a-cf66-437a-b01e-f8f7268a3f7a
ms.openlocfilehash: be97991be9b61908a23486da0ef255ebfbdc5485
ms.sourcegitcommit: bc293b14af795e0e999e3304dd40c0222cf2ffe4
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/26/2020
ms.locfileid: "96239958"
---
# <a name="1001---workflowapplicationcompleted"></a>1001 - WorkflowApplicationCompleted

## <a name="properties"></a>Özellikler  
  
|||  
|-|-|  
|ID|1001|  
|Anahtar sözcükler|WFRuntime|  
|Düzey|Bilgi|  
|Kanal|Microsoft-Windows-Application Server-uygulamalar/hata ayıkla|  
  
## <a name="description"></a>Açıklama  

 Bir iş akışı uygulamasının kapalı durumda tamamlandığını gösterir.  
  
## <a name="message"></a>İleti  

 WorkflowInstance kimliği: ' %1 ' kapalı durumda tamamlandı.  
  
## <a name="details"></a>Ayrıntılar  
  
|Veri öğesi adı|Veri öğesi türü|Açıklama|  
|--------------------|--------------------|-----------------|  
|WorkflowInstanceId|`xs:string`|İş akışının örnek kimliği|  
|AppDomain|`xs:string`|AppDomain. CurrentDomain. FriendlyName tarafından döndürülen dize.|
