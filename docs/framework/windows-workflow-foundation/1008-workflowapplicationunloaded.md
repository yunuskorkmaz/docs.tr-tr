---
title: 1008 - WorkflowApplicationUnloaded
ms.date: 03/30/2017
ms.assetid: a605b780-4a7e-43ab-92e7-0a3b01d053b0
ms.openlocfilehash: 6ea121e7901d877d4f0d8f9f5bfd259c2f93696d
ms.sourcegitcommit: bc293b14af795e0e999e3304dd40c0222cf2ffe4
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/26/2020
ms.locfileid: "96239837"
---
# <a name="1008---workflowapplicationunloaded"></a>1008 - WorkflowApplicationUnloaded

## <a name="properties"></a>Özellikler  
  
|||  
|-|-|  
|ID|1008|  
|Anahtar sözcükler|WFRuntime|  
|Düzey|Bilgi|  
|Kanal|Microsoft-Windows-Application Server-uygulamalar/hata ayıkla|  
  
## <a name="description"></a>Açıklama  

 Bir iş akışı uygulamasının bellekten kaldırılmadığını belirtir.  
  
## <a name="message"></a>İleti  

 WorkflowInstance kimliği: ' %1 ' kaldırıldı.  
  
## <a name="details"></a>Ayrıntılar  
  
|Veri öğesi adı|Veri öğesi türü|Açıklama|  
|--------------------|--------------------|-----------------|  
|WorkflowInstanceId|`xs:string`|İş akışının örnek kimliği|  
|AppDomain|`xs:string`|AppDomain. CurrentDomain. FriendlyName tarafından döndürülen dize.|
