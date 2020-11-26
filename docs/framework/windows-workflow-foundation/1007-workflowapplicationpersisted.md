---
title: 1007 - WorkflowApplicationPersisted
ms.date: 03/30/2017
ms.assetid: f4ea4452-28e3-4e66-93c6-eb12ee29bcb1
ms.openlocfilehash: aa4c7b2c98924eb43f78ab23a145b93906e302fc
ms.sourcegitcommit: bc293b14af795e0e999e3304dd40c0222cf2ffe4
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/26/2020
ms.locfileid: "96239829"
---
# <a name="1007---workflowapplicationpersisted"></a>1007 - WorkflowApplicationPersisted

## <a name="properties"></a>Özellikler  
  
|||  
|-|-|  
|ID|1007|  
|Anahtar sözcükler|WFRuntime|  
|Düzey|Bilgi|  
|Kanal|Microsoft-Windows-Application Server-uygulamalar/hata ayıkla|  
  
## <a name="description"></a>Açıklama  

 Bir iş akışı uygulamasının kalıcı olduğunu gösterir.  
  
## <a name="message"></a>İleti  

 WorkflowApplication kimliği: ' %1 ' kalıcı oldu.  
  
## <a name="details"></a>Ayrıntılar  
  
|Veri öğesi adı|Veri öğesi türü|Açıklama|  
|--------------------|--------------------|-----------------|  
|Workflowapplicationıd|`xs:string`|İş akışı uygulama kimliği|  
|AppDomain|`xs:string`|AppDomain. CurrentDomain. FriendlyName tarafından döndürülen dize.|
