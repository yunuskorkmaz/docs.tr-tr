---
description: 'Hakkında daha fazla bilgi edinin: 1008-Workflowapplicationyüklenmeyen'
title: 1008 - WorkflowApplicationUnloaded
ms.date: 03/30/2017
ms.assetid: a605b780-4a7e-43ab-92e7-0a3b01d053b0
ms.openlocfilehash: 5e906c0daae525accc3b8b13c907479d18f2fc8c
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99755570"
---
# <a name="1008---workflowapplicationunloaded"></a>1008 - WorkflowApplicationUnloaded

## <a name="properties"></a>Özellikler  
  
|||  
|-|-|  
|ID|1008|  
|Anahtar sözcükler|WFRuntime|  
|Level|Bilgi|  
|Kanal|Microsoft-Windows-Application Server-uygulamalar/hata ayıkla|  
  
## <a name="description"></a>Description  

 Bir iş akışı uygulamasının bellekten kaldırılmadığını belirtir.  
  
## <a name="message"></a>İleti  

 WorkflowInstance kimliği: ' %1 ' kaldırıldı.  
  
## <a name="details"></a>Ayrıntılar  
  
|Veri öğesi adı|Veri öğesi türü|Description|  
|--------------------|--------------------|-----------------|  
|WorkflowInstanceId|`xs:string`|İş akışının örnek kimliği|  
|AppDomain|`xs:string`|AppDomain. CurrentDomain. FriendlyName tarafından döndürülen dize.|
