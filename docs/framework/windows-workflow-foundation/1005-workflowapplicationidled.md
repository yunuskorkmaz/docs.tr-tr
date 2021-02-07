---
description: 'Hakkında daha fazla bilgi edinin: 1005-Workflowapplicationıdled'
title: 1005 - WorkflowApplicationIdled
ms.date: 03/30/2017
ms.assetid: 74d77dfa-f20d-4fe9-a6ae-e6d1b5fe4182
ms.openlocfilehash: ee8d0b7ff2155333213a718a04c3966024fda89d
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99755609"
---
# <a name="1005---workflowapplicationidled"></a>1005 - WorkflowApplicationIdled

## <a name="properties"></a>Özellikler  
  
|||  
|-|-|  
|ID|1005|  
|Anahtar sözcükler|WFRuntime|  
|Level|Bilgi|  
|Kanal|Microsoft-Windows-Application Server-uygulamalar/hata ayıkla|  
  
## <a name="description"></a>Description  

 Bir iş akışı uygulamasının ıdlenmiş olduğunu gösterir.  
  
## <a name="message"></a>İleti  

 WorkflowApplication kimliği: ' %1 ' boşta oldu.  
  
## <a name="details"></a>Ayrıntılar  
  
|Veri öğesi adı|Veri öğesi türü|Description|  
|--------------------|--------------------|-----------------|  
|WorkflowInstanceId|`xs:string`|İş akışı uygulama kimliği|  
|AppDomain|`xs:string`|AppDomain. CurrentDomain. FriendlyName tarafından döndürülen dize.|
